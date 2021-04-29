---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción de todos los servicios de NetX Secure (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815353"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS NetX Secure

Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX Secure (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la macro **NX_SECURE_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no aparecen en negrita están totalmente deshabilitados.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Realizar pruebas automáticas en los métodos criptográficos
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Calcular el valor del código hash mediante una función hash proporcionada por el usuario
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Establecer el certificado de identidad activo para una sesión de TLS de NetX Secure
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Establecer una clave compartida previamente para una sesión de cliente TLS de NetX Secure
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Inicializar el módulo de TLS de NetX Secure
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Agregar un certificado local a una sesión de TLS de NetX Secure
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Buscar un certificado local en una sesión de TLS de NetX Secure por nombre común
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Quitar certificado local de una sesión de TLS de NetX Secure
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Calcular el tamaño de los metadatos criptográficos para una sesión de TLS de NetX Secure
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Asignar un paquete para una sesión de TLS de NetX Secure
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Agregar una clave compartida previamente a una sesión de TLS de NetX Secure
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Asignar espacio para el certificado proporcionado por un host de TLS remoto
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Asignar espacio para todos los certificados proporcionados por un host de TLS remoto
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Liberar el espacio asignado para los certificados entrantes
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Agregar un certificado específicamente para servidores TLS mediante un identificador numérico
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Buscar un certificado mediante un identificador numérico
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Quitar un certificado de servidor local mediante un identificador numérico
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Configurar una devolución de llamada para que TLS la use para la validación de certificados adicional
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Configurar una devolución de llamada para que TLS la invoque al principio de un protocolo de enlace de cliente TLS
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Habilitar la comprobación X.509 de cliente y asignar espacio para los certificados de cliente
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Deshabilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Habilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Crear una sesión de TLS de NetX Secure para comunicaciones seguras
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Eliminar una sesión de TLS de NetX Secure
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Finalizar una sesión activa de TLS de NetX Secure
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Establecer el búfer de reensamblado de paquetes para una sesión de TLS de NetX Secure
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Invalidar la versión predeterminada del protocolo TLS para una sesión de TLS de NetX Secure
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Recibir datos de una sesión de TLS de NetX Secure
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Asignar una devolución de llamada que se invocará al comienzo de una renegociación de sesión
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Iniciar un protocolo de enlace de renegociación de sesión con el host remoto
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Borrar y restablecer una sesión de TLS de NetX Secure
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Enviar datos mediante una sesión de TLS de NetX Secure
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Configurar una devolución de llamada para que TLS la invoque al comienzo de un protocolo de enlace del servidor TLS
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Analizar una extensión de Indicación de nombre de servidor (SNI) recibida desde un cliente TLS
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Establecer un nombre DNS de extensión de Indicación de nombre de servidor (SNI) para enviar a un servidor remoto
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Iniciar una sesión de TLS de NetX Secure
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Asignar una función de marca de tiempo a una sesión de TLS de NetX Secure
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Agregar un certificado de confianza a la sesión de TLS de NetX Secure
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Quitar un certificado de confianza de la sesión de TLS de NetX Secure
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Inicializar un certificado X.509 para TLS de NetX Secure
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Comprobar el nombre DNS con el certificado X.509
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Comprobar el certificado X.509 en una lista de revocación de certificados (CRL) proporcionada
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Inicializar una estructura de nombre DNS de X.509
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Buscar y analizar una extensión de uso extendido de clave X.509 en un certificado X.509
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Buscar y devolver una extensión X.509 en un certificado X.509
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Buscar y analizar una extensión de uso de clave X.509 en un certificado X.509

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Realizar pruebas automáticas en los métodos criptográficos

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Descripción

Este servicio ejecuta las pruebas automáticas de los métodos criptográficos para realizar la validación. La prueba automática solo está disponible si se ha compilado la biblioteca de NetX Secure con el símbolo NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definido.

Para cada método criptográfico admitido, la prueba automática proporciona datos de entrada predefinidos y comprueba que la salida coincide con el valor esperado predefinido.

La prueba automática de criptografía de NetX Secure admite los siguientes algoritmos y tamaños de clave:

- DES: cifrado y descifrado
- Triple DES (3DES): cifrado y descifrado
- AES: tamaño de clave de 128, 192 y 256 bits, cifrado y descifrado, en modo CBC y en modo de contador.
- HMAC-MD5: autenticación y cálculo de hash
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autenticación y cálculo de hash
- MD5: autenticación
- Función pseudoaleatoria (PRF): PRF_HMAC_SHA1 y PRF_HMAC_SHA2-256
- RSA: operación de potencia-módulo de RSA de 1024, 2048 y 4096 bits
- SHA: autenticación SHA1 (96 y 160 bits) y SHA2 (256 bits, 384 bits, 512 bits)

Esta función tiene los vectores integrados para los algoritmos criptográficos enumerados anteriormente. Sin embargo, solo comprueba los que aparecen en el elemento *cipher_table* pasado a esta función. Por ejemplo, para una sesión de TLS que solo usa el conjunto de cifrado TLS_RSA_WITH_AES_128_CBC_SHA, esta función realizará una prueba automática en RSA (1024, 2048 y 4096 bits), AES-CBC (128 bits) y SHA1.

### <a name="parameters"></a>Parámetros

- **crypto_table**: puntero a la tabla de cifrado que utiliza la sesión de TLS. Es el mismo elemento crypto_table que se pasa a la llamada **_nx_secure_tls_session_create()_**.
- **metadata**: puntero al espacio para el área de metadatos de criptografía. .
- **metadata_size**: tamaño del búfer de metadatos.

### <a name="return-values"></a>Valores devueltos

- **NX_SECURE_TLS_SUCCESS**: (0x00) Se han probado correctamente los métodos criptográficos proporcionados.
- **NX_PTR_ERROR**: (0x07) Estructura de método criptográfico no válida.
- **NX_NOT_SUCCESSFUL**: (0x43) Se ha producido un error en la prueba automática de criptografía.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Calcular el valor del código hash mediante una función hash proporcionada por el usuario

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Descripción

Esta función calcula el valor del código hash del flujo de datos del área de memoria especificada, utilizando el método criptográfico HMAC y la cadena de clave proporcionados. La función de cálculo del código hash del módulo solo está disponible si se ha compilado la biblioteca de NetX Secure con el siguiente símbolo definido: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parámetros

- **hmac_ptr**: puntero al método criptográfico HMAC que se utiliza para calcular el valor del código hash.
- **start_address**: dirección inicial del búfer de datos.
- **end_address**: dirección final del búfer de datos. Tenga en cuenta que el cálculo del código hash no incluye los datos de esta dirección final.
- **key**: cadena de clave que se usa en el cálculo de HMAC.
- **key_length**: tamaño de la cadena de clave en bytes.
- **metadata**: puntero al espacio usado por el algoritmo HMAC.
- **metadata_size**: tamaño del búfer de metadatos.
- **output_buffer**: ubicación de memoria donde se va a almacenar la salida del código hash.
- **output_buffer_size**: espacio disponible del búfer de salida en bytes.
- **actual_size**: lo devuelve la función e indica el número real de bytes que se escriben en el búfer de salida.

### <a name="return-values"></a>Valores devueltos

- **0**: se ha calculado correctamente el valor del código hash.
- **1**: error en el cálculo del código hash.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a>Consulte también

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

Establecer el certificado de identidad activo para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Descripción

Este servicio está diseñado para ser llamado desde una devolución de llamada de sesión (consulte nx_secure_tls_session_client_callback_set y nx_secure_tls_session_server_callback_set). Cuando se le llama con una estructura NX_SECURE_X509_CERT inicializada previamente, se usará ese certificado en lugar del certificado de identidad predeterminado. En la mayoría de los casos, el certificado se debe haber agregado al almacén local (consulte nx_secure_tls_local_certificate_add) o el protocolo de enlace de TLS puede producir un error.

Este servicio está diseñado para permitir que TLS admita varios certificados de identidad. Esto resulta útil para un servidor de TLS que proporciona servicio a varias direcciones de red para que el servidor pueda elegir un certificado adecuado para proporcionar al cliente remoto en función del punto de entrada del cliente. Para un cliente TLS, esta rutina se puede usar para cambiar el certificado que se envía a un servidor remoto en tiempo de ejecución después de que el servidor se haya identificado en el protocolo de enlace de TLS (esto es menos frecuente que el caso de uso de servidor TLS).

En el caso de que varios certificados puedan compartir el mismo nombre distintivo X.509, los certificados deberán agregarse mediante nx_secure_tls_server_certificate_add, que introduce un identificador numérico independiente del certificado.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS que se pasa a la devolución de llamada de sesión.
- **certificate**: puntero a un certificado X.509 inicializado que se va a utilizar para la sesión actual.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta del certificado a la sesión.
- **NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

Establecer una clave compartida previamente para una sesión de cliente TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Descripción

Este servicio agrega una clave compartida previamente (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión de TLS, y establece esa PSK para que se use en las conexiones de cliente TLS subsiguientes. La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de cifrado de PSK.

En este caso, la PSK está asociada a un servidor TLS remoto específico con el que el cliente TLS desea comunicarse. La PSK establecida mediante esta API se proporcionará al host del servidor TLS remoto durante el siguiente protocolo de enlace de TLS.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **pre_shared_key**: valor real de la PSK.
- **psk_length**: longitud del valor de la PSK.
- **psk_identity**: cadena que se usa para identificar este valor de PSK.
- **identity_length**: longitud de la identidad de la PSK.
- **hint**: cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.
- **hint_length**: longitud de la cadena de sugerencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) PSK agregada correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE**: (0x125) No se puede agregar otra PSK.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

Inicializar el módulo de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Descripción

Este servicio inicializa el módulo de TLS de NetX Secure. Se le debe llamar antes de que se pueda acceder a otros servicios de NetX Secure.

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Agregar un certificado local a una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT inicializada al almacén local de una sesión de TLS. Este certificado puede ser utilizado por la pila de TLS para identificar el dispositivo durante el protocolo de enlace de TLS (si se marcó como certificado de identidad durante la inicialización de la estructura del certificado mediante nx_secure_x509_certificate_initialize) o como un emisor como parte de una cadena de certificados proporcionada al host remoto durante el protocolo de enlace de TLS.

Si se necesitan varios certificados locales con el mismo nombre común, se pueden agregar certificados mediante el servicio *nx_secure_tls_server_certificate_add* (consulte la advertencia siguiente).

Se **requiere** un certificado para el modo de servidor TLS.

El certificado es *opcional* para el modo de cliente TLS.

> [!IMPORTANT]
> *Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate_ptr**: puntero a una instancia de certificado TLS inicializada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado agregado correctamente.
- **NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido o duplicado.
- **NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

Buscar un certificado local en una sesión de TLS de NetX Secure por nombre común

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Descripción

Este servicio encuentra un certificado en el almacén de certificados del dispositivo local de una sesión de TLS y devuelve un puntero a la estructura NX_SECURE_X509_CERT del almacén. El parámetro common_name y su longitud (name_length) se usan para identificar el certificado en el almacén mediante la coincidencia del campo de nombre común del firmante X.509 del certificado.

Si hay más de un certificado con el mismo nombre común, solo se devolverá el primero: use *nx_secure_tls_server_certificate_find* en su lugar.

> [!IMPORTANT]
> *Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate**: puntero devuelto al certificado coincidente.
- **common_name**: cadena de nombre común que debe coincidir (nombre DNS).
- **name_length**: longitud de los datos de cadena common_name.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró el certificado y se devolvió el puntero en el parámetro "certificate".
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró ningún certificado con el nombre común proporcionado.
- **NX_PTR_ERROR**: (0x07) Sesión de TLS, puntero de certificado o cadena de nombre común no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

Quitar certificado local de una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Descripción

Este servicio quita una instancia de certificado local de una sesión de TLS, con la clave en el campo de nombre común del certificado.

> [!IMPORTANT]
> *Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **common_name**: valor del nombre común del certificado que se va a quitar.
- **common_name_length**: longitud de la cadena del nombre común.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado agregado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

Calcular el tamaño de los metadatos criptográficos para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Descripción

Este servicio calcula y devuelve el tamaño de los metadatos criptográficos necesarios para una sesión de TLS determinada y la tabla de criptografía TLS (consulte la sección "Inicialización de TLS con métodos criptográficos" para más información sobre la tabla de cifrado criptográfico).

Se debe llamar a este servicio con la tabla criptográfica deseada para calcular el tamaño del búfer de metadatos que se pasa en nx_secure_tls_session_create.

### <a name="parameters"></a>Parámetros

- **crypto_table**: puntero a una tabla de criptografía completa de TLS de NetX Secure.
- **metadata_size**: salida del cálculo de tamaño en bytes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cálculo correcto del tamaño de los metadatos.
- **NX_PTR_ERROR**: (0x07) Tabla de cifrado o puntero al tamaño devuelto no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Calcular el valor del código hash de las rutinas de la biblioteca de NetX Secure

### <a name="prototype"></a>Prototipo

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>Descripción

Este servicio inicializa el módulo de TLS de NetX Secure. Se le debe llamar antes de que se pueda acceder a otros servicios de NetX Secure.

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Asignar un paquete para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio asigna un elemento NX_PACKET para la sesión de TLS activa especificada desde el elemento NX_PACKET_POOL especificado. La aplicación debe llamar a este servicio para asignar los paquetes de datos que se enviarán mediante una conexión TLS. Se debe inicializar la sesión de TLS antes de llamar a este servicio.

El paquete asignado se ha inicializado correctamente para que se puedan agregar los datos de encabezado y pie de página de TLS una vez que se hayan rellenado los datos del paquete. De lo contrario, el comportamiento es idéntico al de *nx_packet_allocate*.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **pool_ptr**: puntero a un elemento NX_PACKET_POOL desde el que se va a asignar el paquete.
- **packet_ptr**: puntero de salida al paquete recién asignado.
- **wait_option**: opción de suspensión para la asignación de paquetes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta del paquete.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error al asignar el paquete subyacente.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

Agregar una clave compartida previamente a una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Descripción

Este servicio agrega una clave compartida previamente (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión de TLS. La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de cifrado de PSK.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **pre_shared_key**: valor real de la PSK.
- **psk_length**: longitud del valor de la PSK.
- **psk_identity**: cadena que se usa para identificar este valor de PSK.
- **identity_length**: longitud de la identidad de la PSK.
- **hint**: cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.
- **hint_length**: longitud de la cadena de sugerencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) PSK agregada correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE**: (0x125) No se puede agregar otra PSK.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

Asignar espacio para el certificado proporcionado por un host de TLS remoto

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Descripción

Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT sin inicializar a una sesión de TLS con el fin de asignar espacio para los certificados proporcionados por un host remoto durante una sesión de TLS. Los datos del certificado remoto se analizan mediante el uso de TLS de NetX Secure y esa información se usa para rellenar la instancia de la estructura de certificado proporcionada a esta función. Los certificados agregados de esta manera se colocan en una lista vinculada.

Si se espera que el host remoto proporcione varios certificados, se debe llamar a esta función de forma repetida para asignar espacio para todos los certificados. Los certificados adicionales se agregan al final de la lista de certificados vinculados.

Si no se asigna un certificado remoto, se producirá un error en el modo de cliente TLS durante el protocolo de enlace de TLS, a menos que se utilice el conjunto de cifrado de una clave compartida previamente (PSK).

El parámetro *raw_certificate_buffer* apunta al espacio asignado para almacenar el certificado remoto entrante. Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes. El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor. Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.

En el modo de servidor TLS, solo se necesita la asignación de certificados remotos si está habilitada la autenticación de certificados de cliente.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate_ptr**: puntero a una instancia de certificado X.509 no inicializada.
- **raw_certificate_buffer**: puntero a un búfer para almacenar el certificado no analizado recibido del host remoto.
- **raw_buffer_size**: tamaño del búfer de certificados sin procesar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado asignado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.
- **NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

Asignar espacio para todos los certificados proporcionados por un host de TLS remoto

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Descripción

Este servicio asigna espacio para procesar cadenas de certificados entrantes de los hosts de servidor remotos con el fin de realizar la autenticación X.509 y la comprobación en una instancia de cliente TLS. En el modo de servidor TLS, la asignación de certificados remotos solo es necesaria si está habilitada la autenticación de certificados X.509 de cliente: en el caso de las instancias de servidor TLS, se debe usar en su lugar el servicio *nx_secure_tls_session_x509_client_verify_configure*.

Si no se asignan certificados remotos, se producirá un error en el modo de cliente TLS durante el protocolo de enlace de TLS, a menos que se utilice el conjunto de cifrado de una clave compartida previamente (PSK).

El parámetro *certificate_buffer* apunta al espacio asignado para almacenar los certificados remotos entrantes y los bloques de control necesarios para dichos certificados. El búfer se dividirá por el número de certificados (*certs_number*) con una parte igual para cada certificado. El parámetro *buffer_size* indica el tamaño del búfer. Se puede determinar el espacio necesario con la siguiente fórmula:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes. El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño para cada certificado, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor. Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certs_number**: número de certificados que se van a asignar desde el búfer proporcionado.
- **certificate_buffer**: puntero a un búfer para contener los certificados recibidos de un host remoto.
- **buffer_size**: tamaño del búfer de certificados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado asignado correctamente.
- **NX_PTR_ERROR**: (0x07) Sesión de TLS o puntero de búfer no válidos.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.
- **NX_INVALID_PARAMETERS**: (0x4D) El búfer era demasiado pequeño para contener el número deseado de certificados.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

Liberar el espacio asignado para los certificados entrantes

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio se usa para liberar todos los búferes de certificado asignados a una sesión de TLS determinada con nx_secure_tls_remote_certificate_allocated mediante su devolución al espacio de certificados libre de esa sesión. Esto puede ser necesario si una aplicación reutiliza un objeto de sesión de TLS sin eliminarlo y volver a crearlo con nx_secure_tls_session_delete y nx_secure_tls_session_create.

Tenga en cuenta que el espacio de certificados remotos se recupera automáticamente cuando se restablece la sesión de TLS, como sucede en nx_secure_tls_session_end, por lo que la mayoría de las aplicaciones no tendrán que llamar a este servicio.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Operación correcta.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_INVALID_PARAMETERS**: (0x4D) Error interno; el almacén de certificados probablemente esté dañado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

Agregar un certificado específicamente para servidores TLS mediante un identificador numérico

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Descripción

Este servicio se usa para agregar un certificado al almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado. El identificador numérico es independiente del certificado y permite agregar varios certificados como certificados de identidad a un servidor TLS, además de permitir que se agreguen varios certificados con el mismo nombre común al mismo almacén local de la sesión de TLS. Este mismo servicio se puede usar para los certificados de cliente, pero es raro que un cliente TLS tenga varios certificados de identidad.

El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación. El valor real no importa (siempre que sea distinto de cero), pero debe ser único en el almacén de la sesión de TLS proporcionada. El valor de cert_id se puede usar para buscar y quitar certificados del almacén local mediante nx_secure_tls_server_certificate_find y nx_secure_tls_server_certificate_remove, respectivamente.

> [!IMPORTANT]
> *Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_local_certificate_add. La API nx_secure_tls_server_certificate_add usa un identificador numérico único para cada certificado y el índice de los servicios de certificados locales basado en el nombre común de X.509. Los servicios de certificados de servidor permiten que existan varios certificados con datos compartidos (especialmente el nombre común) en el mismo almacén local, lo que resulta útil para un servidor con varias identidades.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate**: puntero a una instancia de certificado X.509 inicializada previamente.
- **cert_id**: número identificador del certificado (positivo, distinto de cero y relativamente único).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Operación correcta.
- **NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.
- **NX_SECURE_TLS_CERT_ID_INVALID**: (0x138) El identificador de certificado proporcionado tenía un valor no válido (probablemente 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE**: (0x139) El identificador de certificado proporcionado ya está presente en el almacén local.
- **NX_INVALID_PARAMETERS**: (0x4D) Error interno; el almacén de certificados probablemente esté dañado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

Buscar un certificado mediante un identificador numérico

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Descripción

Este servicio se usa para buscar un certificado en el almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado.

El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación cuando el certificado se agrega al almacén local de la sesión de TLS mediante nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_local_certificate_add. La API nx_secure_tls_server_certificate_add usa un identificador numérico único para cada certificado y el índice de los servicios de certificados locales basado en el nombre común de X.509. Los servicios de certificados de servidor permiten que existan varios certificados con datos compartidos (especialmente el nombre común) en el mismo almacén local, lo que resulta útil para un servidor con varias identidades.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate**: puntero a un puntero de certificado X.509 para devolver una referencia al certificado encontrado.
- **cert_id**: valor del identificador de certificado (positivo y distinto de cero).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Operación correcta.
- **NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) El identificador de certificado proporcionado no coincidía con ninguno del almacén local de la sesión de TLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

Quitar un certificado de servidor local mediante un identificador numérico

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Descripción

Este servicio se usa para quitar un certificado del almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado.

El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación cuando el certificado se agrega al almacén local de la sesión de TLS mediante nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **cert_id**: valor del identificador de certificado (positivo y distinto de cero).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Operación correcta.
- **NX_PTR_ERROR**: (0x07) Sesión de TLS no válida.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) El identificador de certificado proporcionado no coincidía con ninguno del almacén local de la sesión de TLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

Obtener el valor y el nivel de la alerta de TLS enviados por el host remoto

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Descripción

Este servicio se usa para recuperar el valor y el nivel de la alerta de TLS cuando el host remoto envía una alerta en respuesta a algún problema o error.

Los valores de los parámetros alert_level y alert_value solo son válidos si se llama a esta función inmediatamente después de una llamada a la API de TLS que haya devuelto el estado NX_SECURE_TLS_ALERT_RECEIVED (0x114), que indica que se ha recibido una alerta del host remoto.

Tenga en cuenta que si el host local de TLS envía una alerta, los códigos de error devueltos son mucho más descriptivos del error real que la propia alerta de TLS, ya que los valores de la alerta de TLS se dejan ambiguos intencionadamente para evitar determinados tipos de ataque (por ejemplo, un ataque de tipo "padding oracle" o similar).

El nivel de alerta solo toma uno de estos dos valores: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) o NX_SECURE_TLS_ALERT_LEVEL_FATAL (0X2). En general, solo se le asignará un nivel de "advertencia" a la alerta CloseNotify (que se usa para indicar una finalización correcta de una sesión de TLS), aunque algunas situaciones de configuración de extensiones también se pueden considerar advertencias. La gran mayoría de las alertas serán "graves", lo que indica un posible error de seguridad y provocarán un cierre inmediato de la conexión TLS (protocolo de enlace o sesión).

Los valores de las alertas de TLS se definen en los documentos RFC de TLS; esta es la lista del documento RFC 5246 (TLS v1.2) como referencia:

| Nombre de la alerta                     | Value | Descripción                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Sin errores, indica que la finalización de la sesión se ha completado correctamente.                                                                                                                   |
| unexpected_message            | 10    | TLS ha recibido un mensaje inesperado o desordenado.                                                                                                           |
| bad_record_mac               | 20    | Error en el descifrado o la comprobación de MAC.                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **EN DESUSO**: error de descifrado (en desuso debido a los ataques de tipo "padding oracle").                                                                                      |
| record_overflow               | 22    | Se ha recibido un registro que es mayor que el tamaño máximo de registro de TLS.                                                                                        |
| decompression_failure         | 30    | Se encontró un problema en la compresión y descompresión de un registro de TLS.                                                                                       |
| handshake_failure             | 40    | Se produjo un error de protocolo de enlace no especificado que no está incluido en otras alertas.                                                                            |
| no_certificate_RESERVED      | 41    | **EN DESUSO** en TLS (solo SSL).                                                                                                                                 |
| bad_certificate               | 42    | Un certificado recibido contenía un formato o firmas no válidos.                                                                                   |
| unsupported_certificate       | 43    | Se ha recibido un certificado que era de un tipo no válido (por ejemplo, un certificado solo de firma utilizado para la autenticación del servidor TLS).                                    |
| certificate_revoked           | 44    | El estado del certificado (proporcionado por una CRL u OCSP) se indicó como "revocado".                                                                       |
| certificate_expired           | 45    | El certificado recibido estaba fuera de su intervalo de fechas válido (aún no es válido o ha expirado).                                                                 |
| certificate_unknown           | 46    | Se encontró algún problema de certificado desconocido que no estaba incluido en otras alertas.                                                                          |
| illegal_parameter             | 47    | Algunos valores de configuración o negociados en el protocolo de enlace de TLS no eran válidos o están fuera del intervalo.                                                                      |
| unknown_ca                    | 48    | No se pudo realizar un seguimiento del certificado de identidad recibido mediante una cadena de certificados a un certificado de CA raíz de confianza.                                              |
| access_denied                 | 49    | Indica que se recibió un certificado válido, pero el control de acceso de la aplicación indicó que el certificado no era válido para los recursos solicitados.            |
| decode_error                  | 50    | Algunos campos o valores de un mensaje del protocolo de enlace o del encabezado TLS estaban fuera del intervalo o no eran válidos, lo que provoca un error en la descodificación de un registro de TLS.                      |
| decrypt_error                 | 51    | No se pudo comprobar la firma o el código hash del mensaje de finalización durante el protocolo de enlace de TLS.                                                                         |
| export_restriction_RESERVED  | 60    | EN DESUSO en TLS v1.2.                                                                                                                                        |
| protocol_version              | 70    | Se reconoce la versión del protocolo TLS negociada durante el protocolo de enlace pero no se admite (por ejemplo, se presentó TLS v1.0 pero no se habilitó).                       |
| insufficient_security         | 71    | Se envía cuando se produce un error en el protocolo de enlace debido a la falta de cifrados seguros (por ejemplo, el tamaño de la clave es demasiado pequeño para los requisitos de la aplicación).                                |
| internal_error                | 80    | Algunos errores que no son de TLS (por ejemplo, problemas de asignación de memoria o problemas de la aplicación) han interrumpido la sesión de TLS.                                         |
| user_canceled                 | 90    | Se devuelve si un usuario o una aplicación cancelan la sesión de TLS antes de que se complete el protocolo de enlace (similar a CloseNotify).                                 |
| no_renegotiation              | 100   | Indica que el host remoto no está dispuesto a realizar protocolos de enlace de renegociación de TLS en respuesta a una solicitud de renegociación.                                 |
| unsupported_extension         | 110   | Se envía si un cliente TLS recibe un mensaje ServerHello que contiene extensiones no solicitadas explícitamente en el mensaje ClientHello inicial (lo que indica que el servidor tiene un problema). |

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **alert_level**: devuelve el nivel de la alerta recibida (advertencia o grave).
- **alert_value**: devuelve el valor de la alerta recibida (consulte la tabla).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Operación correcta.
- **NX_PTR_ERROR**: (0x07) Sesión de TLS no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

Configurar una devolución de llamada para que TLS la use para la validación de certificados adicional

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Descripción

Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando se reciba un certificado desde un host remoto, lo que permite que la aplicación realice comprobaciones de validación, como la validación de DNS, la revocación de certificados y la aplicación de directivas de certificados.

TLS de NetX Secure realizará una validación básica de la ruta X.509 en el certificado antes de invocar a la devolución de llamada para garantizar que se pueda realizar un seguimiento del certificado en un certificado del almacén de certificados de confianza de TLS, pero el resto de la validación se controlará mediante esta devolución de llamada.

La devolución de llamada proporciona el puntero de la sesión de TLS y un puntero al certificado de identidad del host remoto (la hoja de la cadena de certificados). La devolución de llamada debe devolver NX_SUCCESS si toda la validación es correcta; en caso contrario, debe devolver un código de error que indique el error de validación. Cualquier valor distinto de NX_SUCCESS hará que el protocolo de enlace de TLS se anule inmediatamente.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **func_ptr**: puntero a la función de devolución de llamada de validación del certificado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

Configurar una devolución de llamada para que TLS la invoque al principio de un protocolo de enlace de cliente TLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Descripción

Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando un protocolo de enlace del cliente TLS haya recibido un mensaje ServerHelloDone. La función de devolución de llamada permite a una aplicación procesar las extensiones de TLS del mensaje ServerHello recibido que requieran la toma de decisiones o una entrada.

La devolución de llamada se ejecuta con el bloque de control de la sesión de TLS de invocación y una matriz de objetos NX_SECURE_TLS_HELLO_EXTENSION. La matriz de objetos de extensión está pensada para pasarse a una función auxiliar que buscará y analizará una extensión específica. Actualmente, no se admiten extensiones específicas en NetX Secure que requieran una entrada del cliente TLS, pero la devolución de llamada está disponible para que los diseñadores de aplicaciones puedan administrar extensiones personalizadas o nuevas que puedan estar disponibles. Para obtener una función auxiliar de ejemplo que analice las extensiones de TLS proporcionadas en los mensajes de saludo, consulte *nx_secure_tls_session_sni_extension_parse*.

La devolución de llamada del cliente también se puede usar para seleccionar el certificado de identidad activo mediante *nx_secure_tls_active_certificate_set* para el cliente TLS en caso de que el servidor remoto haya solicitado un certificado y proporcione información para permitir que el cliente TLS seleccione un certificado específico. Consulte la referencia de nx_secure_tls_active_certificate_set para más información.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **func_ptr**: puntero a la función de devolución de llamada del cliente TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

Habilitar la comprobación X.509 de cliente y asignar espacio para los certificados de cliente

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Descripción

Este servicio habilita la autenticación de cliente X.509 opcional para una instancia de servidor TLS. También asigna el espacio necesario para procesar las cadenas de certificados entrantes del host del cliente remoto. Los certificados proporcionados por el cliente remoto se comprobarán con los certificados de confianza de la instancia de servidor TLS asignados con el servicio *nx_secure_tls_trusted_certificate_add*.

En el modo de cliente TLS se requiere la asignación de certificados remotos y en su lugar se debe usar el servicio *nx_secure_tls_remote_certificate_buffer_allocate*. La habilitación de la autenticación de cliente X.509 en una instancia de cliente TLS no tendrá ningún efecto.

El parámetro *certificate_buffer* apunta al espacio asignado para almacenar los certificados remotos entrantes y los bloques de control necesarios para dichos certificados. El búfer se dividirá por el número de certificados (*certs_number*) con una parte igual para cada certificado. El parámetro *buffer_size* indica el tamaño del búfer. Se puede determinar el espacio necesario con la siguiente fórmula:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes. El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño para cada certificado, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor. Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certs_number**: número de certificados que se van a asignar desde el búfer proporcionado.
- **certificate_buffer**: puntero a un búfer para contener los certificados recibidos de un host remoto.
- **buffer_size**: tamaño del búfer de certificados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado asignado correctamente.
- **NX_PTR_ERROR**: (0x07) Sesión de TLS o puntero de búfer no válidos.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.
- **NX_INVALID_PARAMETERS**: (0x4D) El búfer era demasiado pequeño para contener el número deseado de certificados.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

Deshabilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la autenticación de certificados de cliente para una sesión de TLS específica. Consulte nx_secure_tls_session_client_verify_enable para más información.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cambio de estado correcto.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

Habilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita la autenticación de certificados de cliente para una sesión de TLS específica. La habilitación de la autenticación de certificados de cliente para una instancia de servidor TLS hará que el servidor TLS solicite un certificado desde cualquier cliente TLS remoto durante el protocolo de enlace de TLS inicial. El certificado recibido del cliente TLS remoto está acompañado de un mensaje CertificateVerify, que el servidor TLS utiliza para comprobar que el cliente es el propietario del certificado (tiene acceso a la clave privada asociada a ese certificado).

Si se puede comprobar el certificado proporcionado y realizar un seguimiento de él en un certificado del almacén de certificados de confianza del servidor TLS mediante una cadena de certificados X.509, el cliente TLS remoto se autentica y el protocolo de enlace continúa. En caso de que se produzcan errores al procesar el certificado o el mensaje CertificateVerify, el protocolo de enlace de TLS finalizará con un error.

> [!NOTE]
> *El servidor TLS debe tener al menos un certificado en su almacén de confianza agregado con nx_secure_tls_trusted_certificate_add o siempre se producirá un error de autenticación.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cambio de estado correcto.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

Crear una sesión de TLS de NetX Secure para comunicaciones seguras

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Descripción

Este servicio inicializa una instancia de la estructura NX_SECURE_TLS_SESSION para su uso en el establecimiento de comunicaciones TLS seguras mediante una conexión de red.

El método toma un objeto NX_SECURE_TLS_CRYPTO que se rellena con los métodos criptográficos disponibles que se van a usar para TLS. *encryption_metadata_area* apunta a un búfer asignado para su uso por TLS para los "metadatos" utilizados por los métodos criptográficos de la tabla NX_SECURE_TLS_CRYPTO para los cálculos. El tamaño de la tabla se puede determinar mediante el servicio nx_secure_tls_metadata_size_calculate. Consulte la sección "Criptografía en TLS de NetX Secure" en el Capítulo 3 para más detalles.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **cipher_table**: puntero a los métodos criptográficos de TLS.
- **encryption_metadata_area**: puntero al espacio para los metadatos de criptografía.
- **encryption_metadata_size**: tamaño del búfer de metadatos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.
- **NX_INVALID_PARAMETERS**: (0x4D) El búfer de metadatos era demasiado pequeño para los métodos especificados.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER**: (0x106) No se proporcionó en la tabla de cifrado un método de cifrado necesario para la versión habilitada de TLS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- Criptografía en TLS de NetX Secure en el Capítulo 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Eliminar una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una sesión de TLS representada por una instancia de la estructura NX_SECURE_TLS_SESSION y libera todos los recursos del sistema que pertenecen a esa instancia de sesión.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

Finalizar una sesión activa de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio finaliza una sesión de TLS representada por una instancia de la estructura NX_SECURE_TLS_SESSION mediante el envío de un mensaje CloseNotify de TLS al host remoto. Después, el servicio espera a que el host remoto responda con su propio mensaje CloseNotify.

Si el host remoto no envía un mensaje CloseNotify, TLS lo considera un error y una posible infracción de seguridad, por lo que es importante comprobar el valor devuelto para una conexión segura. El parámetro **wait_option** se puede utilizar para controlar cuánto tiempo debe esperar el servicio a la respuesta antes de devolver el control al subproceso que realiza la llamada.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **wait_option**: indica cuánto tiempo debe esperar el servicio la respuesta del host remoto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE**: (0x113) No se ha recibido una respuesta del host remoto antes de que se agotara el tiempo de espera.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) No se pudo asignar un paquete para enviar el mensaje CloseNotify.
- **NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) No se pudo enviar el mensaje CloseNotify mediante el socket TCP.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

Establecer el búfer de reensamblado de paquetes para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Descripción

Este servicio asocia un búfer de reensamblado de paquetes a una sesión de TLS. Para descifrar y analizar los registros de TLS entrantes, los datos de cada registro se deben ensamblar desde los paquetes TCP subyacentes. Los registros de TLS pueden tener un tamaño máximo de 16 KB (aunque normalmente son mucho más pequeños), por lo que puede que no quepan en un único paquete TCP.

Si sabe que el tamaño del mensaje entrante será menor que el límite del registro de TLS de 16 KB, el tamaño del búfer puede ser menor, pero para controlar datos entrantes desconocidos, el búfer debe ser lo más grande posible. Si un registro entrante es mayor que el búfer proporcionado, la sesión de TLS finalizará con un error.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **buffer_ptr**: puntero al búfer que TLS utilizará para el reensamblado de paquetes.
- **buffer_size**: tamaño del búfer proporcionado en bytes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_INVALID_PARAMETERS**: (0x4D) Búfer o puntero de sesión de TLS no válidos.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

Invalidar la versión predeterminada del protocolo TLS para una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Descripción

Este servicio invalida la versión predeterminada (más reciente) del protocolo TLS usada por una sesión determinada. Esto permite a TLS de NetX Secure usar una versión anterior de TLS para una sesión de TLS específica sin deshabilitar las versiones más recientes de TLS en tiempo de compilación. Esto puede resultar útil en las aplicaciones que pueden necesitar comunicarse con un host más antiguo que no admita la versión más reciente de TLS.

> [!IMPORTANT]
> *A partir de la versión 5.11 SP3, TLS de NetX Secure es compatible con RFC 7507 (consulte la nota siguiente) y cualquier invalidación de una versión anterior con esta API producirá el envío de un SCSV de reserva en el mensaje ClientHello. Si el servidor admite una versión más reciente de TLS y el SCSV de reserva está incluido en el mensaje ClientHello, ese servidor anulará el protocolo de enlace de TLS con una alerta de "reserva inapropiada". El SCSV solo se envía cuando la invalidación de versión es una versión anterior de TLS que está habilitada (por ejemplo, si invalida la versión a TLS 1.2, no se enviará un SCSV).*

Los valores válidos para el parámetro protocol_version son las siguientes macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 y NX_SECURE_TLS_VERSION_TLS_1_2.

Las macros NX_SECURE_TLS_DISABLE_TLS_1_1 y NX_SECURE_TLS_ENABLE_TLS_1_0 se pueden usar para controlar las versiones de TLS que se han compilado en la aplicación. La versión 1.2 de TLS está siempre habilitada.

Tenga en cuenta que si el host remoto no admite la versión suministrada, se producirá un error en la conexión; TLS de NetX Secure solo negociará la versión de invalidación proporcionada.

> [!IMPORTANT]
> RFC 7507: SCSV de reserva de TLS. Este documento RFC se introdujo para mitigar un problema de seguridad causado originalmente por servidores que no administraban correctamente la negociación de cambio a una versión anterior del protocolo y que, en su lugar, rechazaron mensajes ClientHello válidos. En un intento de seguir siendo compatible con estos servidores antiguos, algunas aplicaciones cliente de TLS empezaron a reintentar los protocolos de enlace con errores con una versión de TLS anterior (por ejemplo, TLS 1.2 produce un error y se intenta con TLS 1.1). Sin embargo, esta solución ha creado un nuevo problema: un atacante podría forzar a un cliente a cambiar a una versión anterior mediante la introducción artificial de un error de red o de paquete que provoque un error en la conexión con el servidor, incluso cuando el servidor admita la versión más reciente de TLS. Al cambiar a una versión anterior, el atacante podría aprovechar las vulnerabilidades de seguridad de esa versión (en especial, SSL v3<sup>21</sup> es vulnerable al ataque POODLE). Para evitar esta situación, RFC 7507 introduce el "SCSV de reserva", un pseudo conjunto de cifrado<sup>22</sup> enviado en el mensaje ClientHello y que notifica a un servidor TLS cuando un cliente TLS usa una versión de TLS que no es la versión más reciente que admite. De este modo, un servidor que admita una versión más reciente puede rechazar un mensaje ClientHello que contenga el SCSV de reserva y evitar que el ataque de cambio a una versión anterior tenga éxito.

21. NetX Secure no implementa SSLv3 debido a la existencia de vulnerabilidades de seguridad graves conocidas, como POODLE.

22. Un pseudo conjunto de cifrado o SCSV (valor de conjunto de cifrado de señalización) es un número de conjunto de cifrado reservado que se usa para indicar las implementaciones de TLS habilitadas sobre características que no estaban disponibles en versiones anteriores de TLS. El SCSV de reserva y TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) son ejemplos.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **protocol_version**: macro de la versión de TLS de la versión específica de TLS que se va a usar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cambio de estado correcto.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**: (0x110) Versión de TLS conocida pero no admitida.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Versión de protocolo no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

Recibir datos de una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recibe datos de la sesión de TLS activa especificada, controlando el descifrado de los datos antes de proporcionárselos al autor de llamada en el parámetro NX_PACKET. Si no hay datos en cola en la sesión especificada, la llamada se suspende en función de la opción de espera proporcionada.

> [!IMPORTANT]
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **packet_ptr**: puntero a un puntero de paquete TLS asignado.
- **wait_option**: indica cuánto tiempo debe esperar el servicio a un paquete del host remoto antes de volver.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.
- **NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje recibido produjo un error en una comprobación del código hash de autenticación.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje recibido tenía una versión de protocolo desconocida en el encabezado.
- **NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) Se ha recibido una alerta del host remoto.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

Asignar una devolución de llamada que se invocará al comienzo de una renegociación de sesión

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Descripción

Este servicio asigna una devolución de llamada a una sesión de TLS a la que se invocará siempre que se reciba el primer mensaje de un protocolo de enlace de renegociación de sesión desde el host remoto.

La función de devolución de llamada está pensada como una notificación a la aplicación de que se está iniciando un protocolo de enlace de renegociación: la aplicación puede elegir finalizar la sesión de TLS devolviendo cualquier valor distinto de cero de la devolución de llamada, lo que hará que TLS finalice la sesión de TLS con un error. Si la aplicación desea continuar con la renegociación, la devolución de llamada debe devolver NX_SUCCESS.

> [!NOTE]
> *Debido a la semántica de la renegociación de TLS, se invocará a la devolución de llamada para los clientes TLS de NetX Secure siempre que se reciba un mensaje HelloRequest desde el servidor remoto, pero no cuando el cliente inicie la renegociación. En los servidores TLS de NetX Secure, la devolución de llamada se invocará siempre que se reciba un mensaje ClientHello de renegociación (cualquier mensaje ClientHello recibido en el contexto de una sesión de TLS activa). Esto significa que la devolución de llamada se invocará si el host remoto o la aplicación local han iniciado la renegociación, porque el servidor TLS enviará un mensaje HelloRequest al que responderá el cliente remoto.*

TLS de NetX Secure implementa la extensión de indicación de renegociación segura de RFC 5746 para asegurarse de que los protocolos de enlace de renegociación no estén sujetos a ataques de tipo "Man in the Middle".

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **func_ptr**: puntero a la función de devolución de llamada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta de la devolución de llamada.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido para la función de devolución de llamada o para la sesión de TLS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

Iniciar un protocolo de enlace de renegociación de sesión con el host remoto

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio inicia un protocolo de enlace de *renegociación* de sesión con un host TLS remoto conectado. Una renegociación consta de un segundo protocolo de enlace de TLS en el contexto de una sesión de TLS establecida previamente. Cada uno de los nuevos mensajes del protocolo de enlace se cifra con la sesión de TLS hasta que se generen nuevas claves de sesión y se intercambien los mensajes ChangeCipherSpec, momento en el que se usan las nuevas claves para cifrar todos los mensajes.

Se puede iniciar una renegociación en cualquier momento una vez establecida una sesión de TLS. Si se intenta una renegociación durante un protocolo de enlace de TLS o antes de que se establezca una sesión de TLS, no se realizará ninguna acción.

> [!NOTE]
> *Cuando se invoca este servicio, se realizará un protocolo de enlace de TLS completo, por lo que el tiempo de finalización y el estado devuelto variarán en función de los parámetros de sesión y la configuración de TLS actuales.*

TLS de NetX Secure implementa la extensión de indicación de renegociación segura de RFC 5746 para asegurarse de que los protocolos de enlace de renegociación no estén sujetos a ataques de tipo "Man in the Middle".

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **wait_option**: indica cuánto tiempo debe esperar el servicio a un paquete del host remoto antes de volver. Esto se pasa a todos los servicios de NetX dentro de TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Renegociación correcta.
- **NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.
- **NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje recibido produjo un error en una comprobación del código hash de autenticación.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje recibido tenía una versión de protocolo desconocida en el encabezado.
- **NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) Se ha recibido una alerta del host remoto.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE**: (0x134) La sesión de TLS local o remota está inactiva, lo que hace imposible la renegociación.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE**: (0x13A) El host remoto no proporcionó la extensión de renegociación segura o el SCSV, por lo que no se puede realizar la renegociación.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error al asignar el paquete subyacente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

Borrar y restablecer una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra una sesión de TLS y restablece el estado como si la sesión se hubiera creado ahora, por lo que se puede volver a usar un objeto de sesión de TLS existente para una nueva sesión.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_INVALID_PARAMETERS**: (0x4D) Puntero a la sesión de TLS no válido.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

Enviar datos mediante una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía datos en el elemento NX_PACKET proporcionado, utilizando la sesión de TLS activa especificada y controlando el cifrado de los datos antes de enviarlos al host remoto. Si el último tamaño de ventana anunciado del receptor es menor que esta solicitud, el servicio se suspende opcionalmente en función de las opciones de espera especificada.

> [!IMPORTANT]
> *A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red liberará el paquete después de la transmisión.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **packet_ptr**: puntero a un paquete TLS que contiene los datos que se van a enviar.
- **wait_option**: define cómo se comporta el servicio si la solicitud es mayor que el tamaño de la ventana del receptor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.
- **NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.
- **NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) Error al enviar mediante un socket TCP subyacente.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

Configurar una devolución de llamada para que TLS la invoque al comienzo de un protocolo de enlace del servidor TLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Descripción

Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando un protocolo de enlace del servidor TLS haya recibido un mensaje ClientHello. La función de devolución de llamada permite a una aplicación procesar las extensiones de TLS del mensaje ClientHello recibido que requieran la toma de decisiones o una entrada.

La devolución de llamada se ejecuta con el bloque de control de la sesión de TLS de invocación y una matriz de objetos NX_SECURE_TLS_HELLO_EXTENSION. La matriz de objetos de extensión está pensada para pasarse a una función auxiliar que buscará y analizará una extensión específica. Para obtener una función auxiliar de ejemplo que analice las extensiones de TLS proporcionadas en los mensajes de saludo, consulte *nx_secure_tls_session_sni_extension_parse*.

La devolución de llamada del servidor también se puede usar para seleccionar el certificado de identidad activo mediante *nx_secure_tls_active_certificate_set* para el servidor TLS. Esto se suele producir en respuesta a una extensión de Indicación de nombre de servidor (SNI), que permite a un cliente TLS indicar el servidor con el que intenta ponerse en contacto. Consulte las referencias de *nx_secure_tls_session_sni_extension_parse* y *nx_secure_tls_active_certificate_set* para más información.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **func_ptr**: puntero a la función de devolución de llamada del servidor TLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

Analizar una extensión de Indicación de nombre de servidor (SNI) recibida desde un cliente TLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Descripción

Este servicio está diseñado para que se le llame desde una devolución de llamada de la sesión del servidor TLS, que se agrega a una sesión de TLS mediante nx_secure_tls_session_server_callback_set. Se invoca a la devolución de llamada después de la recepción de un mensaje ClientHello desde un cliente TLS remoto y se proporciona una matriz de extensiones disponibles (y el número de extensiones de la matriz). Se pueden pasar esa matriz y su longitud directamente a esta rutina para determinar si hay una extensión SNI presente; si no la hay, se devuelve NX_SECURE_TLS_EXTENSION_NOT_FOUND, lo que indica simplemente que el cliente optó por no proporcionar la extensión SNI (esto no es un error).

Si se encuentra la extensión SNI, se devuelve el nombre DNS de X.509 proporcionado por el cliente TLS en la estructura dns_name. Actualmente, la extensión SNI solo proporciona una única entrada de nombre DNS, que puede ser utilizada por el servidor TLS para determinar el certificado de identidad que se va a enviar al cliente remoto.**

La estructura NX_SECURE_X509_DNS_NAME simplemente contiene el nombre DNS como una cadena UCHAR en el campo *nx_secure_x509_dns_name* y la longitud de la cadena de nombre en *nx_secure_x509_dns_name_length*. La macro NX_SECURE_X509_DNS_NAME_MAX controla el tamaño del búfer de nx_secure_x509_dns_name.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **extensions**: puntero a una matriz de extensiones de saludo de TLS (desde la devolución de llamada de la sesión).
- **num_extensions**: número de extensiones de la matriz (desde la devolución de llamada de la sesión).
- **dns_name**: devuelve el nombre DNS proporcionado en la extensión SNI.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Análisis correcto de la extensión.
- **NX_PTR_ERROR**: (0x07) Matriz de extensiones o puntero de sesión de TLS no válidos.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND**: (0x136) No se ha encontrado la extensión SNI.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID**: (0x137) El formato de la extensión SNI no era válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Establecer un nombre DNS de extensión de Indicación de nombre de servidor (SNI) para enviar a un servidor remoto

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Descripción

Este servicio permite que una aplicación de cliente TLS proporcione un nombre DNS de servidor preferido a un servidor TLS remoto mediante la extensión Indicación de nombre de servidor (SNI) de TLS. La extensión SNI permite al servidor seleccionar el certificado de identidad y los parámetros adecuados en función de la preferencia de servidor indicada por el cliente. La extensión SNI actualmente solo admite el envío de un único nombre DNS, de ahí el parámetro de nombre en singular. El parámetro dns_name se debe inicializar con *nx_secure_x509_dns_name_initialize* y contendrá el servidor preferido del cliente. Para anular el nombre de la extensión, basta con llamar a este servicio con un valor del parámetro "dns_name" establecido en NX_NULL.

La estructura NX_SECURE_X509_DNS_NAME simplemente contiene el nombre DNS como una cadena UCHAR en el campo *nx_secure_x509_dns_name* y la longitud de la cadena de nombre en *nx_secure_x509_dns_name_length*. La macro NX_SECURE_X509_DNS_NAME_MAX controla el tamaño del búfer de nx_secure_x509_dns_name.

> [!NOTE]
> *Se debe llamar a esta rutina antes de invocar a nx_secure_tls_session_start o el mensaje ClientHello no contendrá la extensión SNI.*

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **dns_name**: nombre DNS proporcionado por la aplicación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Nombre de servidor DNS agregado correctamente.
- **NX_PTR_ERROR**: (0x07) Nombre DNS o puntero de sesión de TLS no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

Iniciar una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio inicia una sesión de TLS con el bloque de control de la sesión de TLS proporcionado y un socket TCP conectado. La conexión TCP ya debe estar completa después de una llamada correcta a nx_tcp_client_socket_connect o nx_tcp_server_socket_accept.

Este servicio determinará el tipo de sesión de TLS (cliente o servidor) a partir del socket TCP.

La opción de espera define cómo se comporta el servicio mientras el protocolo de enlace de TLS está en curso.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **tcp_socket_ptr**: puntero a un socket TCP conectado.
- **wait_option**: define cómo se comporta el servicio mientras el protocolo de enlace de TLS está en curso.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**: (0x102) Un tipo de mensaje TLS recibido es incorrecto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER**: (0x106) No se admite el cifrado proporcionado por el host remoto.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE**: (0x107) Error al procesar el mensaje durante el protocolo de enlace de TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje entrante no pudo realizar una comprobación del hash de MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) Error al enviar mediante un socket TCP subyacente.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH**: (0x10A) Un mensaje entrante tenía un campo de longitud no válida.
- **NX_SECURE_TLS_BAD_CIPHERSPEC**: (0x10B) Un mensaje ChangeCipherSpec entrante era incorrecto.
- **NX_SECURE_TLS_INVALID_SERVER_CERT**: (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor TLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**: (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS**: (0x10E) El host remoto ha indicado que no hay conjuntos de cifrado admitidos por la pila de TLS de NetX Secure.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje TLS recibido tenía una versión de TLS desconocida en el encabezado.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**: (0x110) Un mensaje TLS recibido tenía una versión de TLS conocida pero no admitida en el encabezado.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error en la asignación interna del paquete TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE**: (0x112) El host remoto proporcionó un certificado no válido.
- **NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE**: (0x13B) Una entrada de la tabla del conjunto de cifrado tenía un puntero de función NULL.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK**: (0x146) Un mensaje ClientHello de TLS remoto incluía el SCSV de reserva y ha intentado un cambio a una versión de reserva.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a>Consulte también

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

Asignar una función de marca de tiempo a una sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Descripción

Esta función configura un puntero de función a la que TLS invocará cuando tenga que obtener la hora actual, que se usa en varios mensajes del protocolo de enlace de TLS y para la comprobación de certificados.

Se espera que la función devuelva el valor de la hora GMT actual en formato de 32 bits de UNIX (segundos desde la medianoche a partir del 1 de enero de 1970, UTC, pasando por alto los segundos bisiestos), según los requisitos para mensajes ClientHello de RFC 5246 de TLS.

Si no se asigna ninguna función de marca de tiempo, se usará un valor de 0 para la marca de tiempo en el protocolo de enlace de TLS y la comprobación de la expiración del certificado no funcionará.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS.
- **time_func_ptr**: puntero a una función que devuelve la hora actual (GMT) en formato de 32 bits de UNIX.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_INVALID_PARAMETERS**: (0x4D) Puntero a la sesión de TLS no válido.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

Agregar un certificado de confianza a la sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT inicializada a una sesión de TLS. La pila de TLS usa este certificado para comprobar los certificados proporcionados por el host remoto durante el protocolo de enlace de TLS.

Los certificados de confianza son necesarios para el modo de cliente TLS.

Los certificados de confianza solo son necesarios para el modo de servidor TLS si está habilitada la autenticación de certificados de cliente.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **certificate_ptr**: puntero a una instancia de certificado TLS inicializada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado agregado correctamente.
- **NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

Quitar un certificado de confianza de la sesión de TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Descripción

Este servicio quita un certificado de confianza de una sesión de TLS, con la clave en el campo de nombre común del certificado.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.
- **common_name**: valor del nombre común del certificado que se va a quitar.
- **common_name_length**: longitud de la cadena del nombre común.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado agregado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

Inicializar un certificado X.509 para TLS de NetX Secure

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a>Descripción

Este servicio inicializa una estructura NX_SECURE_X509_CERT a partir de un certificado digital X.509 codificado en binario para su uso en una sesión de TLS.

Los datos del certificado **deben** ser un certificado digital X.509 válido en formato binario con codificación DER. Los datos pueden proceder de cualquier origen (por ejemplo, el sistema de archivos, el búfer de constantes compilado, etc.), siempre que se proporcione un puntero UCHAR a los datos.

El parámetro *raw_data_buffer* y su tamaño son parámetros opcionales que especifican un búfer dedicado en el que se copian los datos del certificado antes del análisis. Si raw_data_buffer se pasa como NX_NULL, la estructura NX_SECURE_X509_CERT apuntará directamente a la matriz certificate_data (en este caso, se omitirá buffer_size). Si se pasa raw_data_buffer como NX_NULL, ***no*** modifique los datos a los que apunta el puntero certificate_data o se producirá un error en el procesamiento del certificado.

El parámetro de clave privada es para los certificados de identidad local: los servidores usan la clave privada para descifrar los datos de clave entrante de un cliente (cifrados con la clave pública del servidor) y los clientes para comprobar su identidad en un servidor cuando el servidor solicita un certificado de cliente. Al agregar una clave privada con esta API, se marcará automáticamente el certificado asociado como certificado de identidad para una aplicación TLS. Al inicializar los certificados para otros propósitos (por ejemplo, el almacén de confianza), el parámetro *private_key_data* se debe pasar como NULL, *private_key_data_length* como 0 y *private_key_type* se debe pasar como NX_SECURE_X509_KEY_TYPE_NONE.

El parámetro *private_key_type* indica el formato de la clave privada. Por ejemplo, si la clave privada es una clave privada RSA con formato PKCS#1 y codificación DER, el parámetro private_key_type se debe pasar como NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, un tipo conocido para NetX Secure que se analizará inmediatamente y se guardará para su uso posterior.

El parámetro private_key_type también admite tipos de clave definidos por el usuario<sup>23</sup> para plataformas y aplicaciones que tengan formatos de clave específicos u otras necesidades. Por ejemplo, un motor de cifrado basado en hardware puede usar un formato específico no reconocido por el software de NetX Secure, o se puede cifrar o representar una clave privada mediante un token criptográfico, como podría ser el caso de un Módulo de plataforma segura (TPM) o de hardware criptográfico PKCS#11. Cuando se usa un tipo de clave definido por el usuario, los datos de la clave se pasan literalmente a la rutina criptográfica adecuada; por ejemplo, se pasaría una clave privada RSA, sin análisis ni procesamiento, directamente a la rutina criptográfica de RSA proporcionada a TLS en la tabla de conjuntos de cifrado. El tipo de clave definido por el usuario también se pasa a la rutina criptográfica (en el caso de RSA, es el parámetro "op").

El intervalo de claves definidas por el usuario abarca la mitad superior de un número entero sin signo de 32 bits, de 0x0001 0000 a 0xFFFF FFFF. Los valores menores que 0x0001 0000 se reservan para el uso de NetX Secure.

Los tipos de clave definidos por el usuario son una característica avanzada que requiere rutinas criptográficas personalizadas para controlar los datos de clave privada sin procesar. Si necesita esta característica, póngase en contacto con su representante de Logic Express.

### <a name="parameters"></a>Parámetros

- **certificate_ptr**: puntero a una instancia de certificado X.509 no inicializada.
- **certificate_data**: puntero a los datos binarios X.509 con codificación DER.
- **raw_data_buffer**: puntero al búfer de datos de certificados dedicado opcional.
- **buffer_size**: tamaño del búfer de datos de certificados dedicado opcional.
- **certificate_data_length**: longitud de los datos binarios del certificado en bytes.
- **private_key_data**: puntero a los datos de la clave privada opcional.
- **private_key_data_length**: longitud de los datos de la clave privada.
- **private_key_type**: identificador del tipo de clave.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Certificado agregado correctamente.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.
- **NX_SECURE_TLS_INVALID_CERTIFICATE**: (0x112) Los datos del certificado no contenían un certificado X.509 con codificación DER.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**: (0x10D) El certificado no tenía un cifrado de clave pública admitido por NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE**: (0x186) La clave privada o el certificado no contenían una secuencia ASN.1 válida.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY**: (0x18A) La clave privada proporcionada no era una clave RSA PKCS#1 válida.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE**: (0x19D) El tipo de clave privada proporcionado no estaba definido por el usuario y no coincidía con ningún tipo conocido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>Consulte también

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- Importación de certificados X.509 en NetX Secure en el Capítulo 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Comprobar el nombre DNS con el certificado X.509

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Descripción

Este servicio comprueba el nombre común de un certificado con un nombre de dominio de nivel superior (TLD) proporcionado por el autor de llamada para la validación DNS de un host remoto. Esta función auxiliar está pensada para ser llamada desde una rutina de devolución de llamada de validación de certificados proporcionada por la aplicación. El nombre del TLD debe ser la parte superior de la dirección URL usada para acceder al host remoto (la cadena separada por "." antes de la primera barra diagonal). Si el nombre común contiene un carácter comodín (por ejemplo, *.example.com), el carácter comodín coincidirá con cualquiera que tenga el mismo sufijo. Tenga en cuenta que solo se tendrá en cuenta el primer carácter comodín ("* ") encontrado (lectura de derecha a izquierda) para la coincidencia de caracteres comodín: por ejemplo, abc.*. example. com coincidirá con *cualquier* nombre que termine en ".example.com".

Si el nombre común no coincide con la cadena proporcionada, se analiza la extensión "subjectAltName" (si existe en el certificado) y también se comparan las entradas de nombres DNS. Si ninguna de esas entradas coincide, se devuelve un error.

Es importante comprender el formato del nombre común (y las entradas subjectAltName) en los certificados esperados. Por ejemplo, algunos certificados pueden usar una dirección IP sin formato o un carácter comodín. Se debe dar formato a la cadena del TLD de DNS para que coincida con los valores esperados en los certificados recibidos.

### <a name="parameters"></a>Parámetros

- **certificate_ptr**: puntero a una instancia de certificado X.509.
- **dns_tld**: nombre del dominio de nivel superior con el que se va a comparar.
- **dns_tld_length**: longitud de la cadena del TLD.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Comparación correcta con el nombre común o con subjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH**: (0x195) No se encontró ningún nombre coincidente.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

Comprobar el certificado X.509 en una lista de revocación de certificados (CRL) proporcionada

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Descripción

Este servicio toma una lista de revocación de certificados con codificación DER y busca un certificado específico en esa lista. El emisor de la CRL se valida con un almacén de certificados proporcionado, el emisor de la CRL se valida para que sea el mismo que en el certificado que se está comprobando y el número de serie del certificado en cuestión se usa para buscar en la lista de certificados revocados. Si los emisores coinciden, se comprueba correctamente la firma y el certificado **no** está presente en la lista, la llamada se realiza correctamente. Todos los demás casos provocan que se devuelva un error.

### <a name="parameters"></a>Parámetros

- **crl_data**: puntero a una CRL con codificación DER.
- **crl_length**: longitud en bytes de los datos de la CRL.
- **store**: puntero a un almacén de certificados X.509.
- **certificate_ptr**: puntero a una instancia de certificado X.509.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Validación correcta de que no se ha revocado el certificado.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado del emisor de la CRL.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND**: (0x11B) No se encontró el certificado del emisor del certificado.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) El elemento ASN.1 de la CRL contenía un campo de longitud no válida.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG**: (0x189) La CRL contenía un elemento ASN.1 no válido.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE**: (0x18C) Error de comprobación de la cadena de certificados.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH**: (0x197) La CRL y los emisores del certificado no coincidían.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED**: (0x198) La firma de la CRL no era válida.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED**: (0x199) Se encontró el certificado que se está comprobando en la CRL y, por lo tanto, se ha revocado.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

Inicializar una estructura de nombre DNS de X.509

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Descripción

Este servicio inicializa un nombre DNS de X.509 para su uso con determinados servicios de API que requieren un formato de nombre específico. Por ejemplo, el servicio *nx_secure_tls_sni_extension_parse* espera un objeto NX_SECURE_X509_DNS_NAME para que coincida con el nombre proporcionado por un host remoto en la extensión de indicación de nombre de servidor durante el protocolo de enlace de TLS. Un nombre DNS es simplemente una cadena de caracteres con una longitud: la longitud máxima permitida de un nombre DNS (y el tamaño del búfer interno en NX_SECURE_X509_DNS_NAME) se controla mediante la macro NX_SECURE_X509_DNS_NAME_MAX (el valor predeterminado es de 100 bytes).

### <a name="parameters"></a>Parámetros

- **dns_name**: estructura de nombre DNS que se va a inicializar.
- **name_string**: datos de la cadena del nombre DNS.
- **length**: longitud de la cadena del nombre.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Inicialización correcta.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG**: (0x19E) La cadena de nombre especificada supera el valor de NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

Buscar y analizar una extensión de uso extendido de clave X.509 en un certificado X.509

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Descripción

Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*). Buscará un OID de uso extendido de clave específico dentro de un certificado X.509 y devolverá si el OID está presente. El parámetro key_usage es una asignación de números enteros de los OID que X.509 y TLS de NetX Secure usan internamente para evitar pasar las cadenas de OID de longitud variable como parámetros.

Los OID correspondientes a la extensión de uso extendido de clave se proporcionan en la tabla siguiente. Una implementación de cliente TLS típica que desee comprobar el uso extendido de clave en un certificado de servidor TLS recibido comprobará la existencia del OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH: si la extensión está presente pero ese OID no lo está, el certificado se considerará no válido para identificar el host como un servidor TLS y la devolución de llamada de comprobación del certificado debe devolver un error. Si falta la propia extensión, depende de la aplicación si desea continuar con el protocolo de enlace de TLS.

En la devolución de llamada de comprobación del certificado, el código de retorno de error NX_SECURE_X509_KEY_USAGE_ERROR está reservado para el uso de la aplicación. Si se produce un error al comprobar el uso de la clave, se puede devolver este valor desde la devolución de llamada para indicar el motivo del error.

| Identificador de NetX Secure                                | Valor de OID         | Descripción                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | El certificado se puede usar para identificar un servidor TLS. |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | El certificado se puede usar para identificar un cliente TLS. |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | El certificado se puede usar para firmar código.             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | El certificado se puede usar para firmar los mensajes de correo electrónico.           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | El certificado se puede usar para firmar las marcas de tiempo.       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | El certificado se puede usar para firmar las respuestas de OCSP.   |

OID y asignaciones para la extensión de uso extendido de clave X.509

### <a name="parameters"></a>Parámetros

- **certificate**: puntero al certificado que se está comprobando.
- **key_usage**: asignación de números enteros de OID de la tabla anterior.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró el OID de uso de clave especificado.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).
- **NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida (certificado no válido).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró la extensión de uso de clave extendida en el certificado proporcionado.
- **NX_PTR_ERROR**: (0x07) Puntero de certificado no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

Buscar y devolver una extensión X.509 en un certificado X.509

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Descripción

Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*) y es un servicio X.509 avanzado.

La función buscará una extensión específica dentro de un certificado X.509 en función de un OID y devolverá si el OID está presente, junto con una estructura que contiene referencias a los datos de la extensión sin procesar correspondientes. El parámetro extension_id es una asignación de números enteros de los OID que X.509 y TLS de NetX Secure usan internamente para evitar pasar las cadenas de OID de longitud variable como parámetros.

Las funciones auxiliares proporcionadas para extensiones específicas (como *nx_secure_x509_key_usage_extension_parse*) llaman a nx_secure_x509_extension_find internamente para obtener los datos de la extensión.

Los OID correspondientes a las extensiones X.509 conocidas se proporcionan en la tabla siguiente.

La estructura NX_SECURE_X509_EXTENSION contiene punteros al certificado X.509 que permiten que funciones auxiliares, como *nx_secure_x509_key_usage_extension_parse*, descodifiquen rápidamente los datos sin procesar ASN.1 con codificación DER de la extensión.

Para obtener información sobre extensiones específicas, consulte el documento RFC 5280 (especificación X.509) o la referencia de las funciones auxiliares adecuadas, si está disponible.

La versión actual de X.509 de NetX Secure tiene compatibilidad limitada con las extensiones X.509. En el futuro se agregarán más funciones auxiliares.

> [!IMPORTANT]
> *Este servicio es una característica avanzada para los usuarios familiarizados con las extensiones X.509 y ASN.1 con codificación DER. Se proporciona para permitir que los usuarios accedan a las extensiones para las que X.509 de NetX Secure no proporciona funciones auxiliares en la actualidad. En el caso de las extensiones sin funciones auxiliares, tendrá que analizar los elementos ASN.1 sin procesar con codificación DER.*

| Identificador de NetX Secure                              | Valor de OID | Descripción                                                                    | ¿Función auxiliar? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Atributos de directorio: atributos de información básica acerca del firmante del certificado.  | No               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Se usa para identificar una clave pública específica.                                         | No               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Proporciona información sobre los usos válidos de la clave pública del certificado.              | Sí              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Proporciona nombres DNS alternativos para identificar el certificado.                     | Sí<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Proporciona nombres DNS alternativos para identificar el emisor del certificado.            | No               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Proporciona información básica sobre las restricciones de uso del certificado.                        | No               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Se usa para restringir los nombres de certificado a dominios específicos.                        | No               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Proporciona los identificadores URI para la distribución de la CRL.                                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista de directivas de certificados para sistemas PKI de gran tamaño.                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista de directivas de certificados de la entidad de certificación                                                | No               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Se usa para identificar una clave pública específica asociada a una firma de certificado. | No               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Restricciones de directivas de la CA                                                          | No               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Información adicional sobre el uso de claves basado en OID.                                     | Sí              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Proporciona información para obtener listas de revocación de certificados incrementales.                                  | No               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Campo del certificado de la CA que indica que no se puede usar el elemento AnyPolicy.                  | No               |

OID y asignaciones de las extensiones X.509

24. La extensión SubjectAltName se analiza como parte de la comprobación del nombre DNS en el servicio nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parámetros

- **certificate**: puntero al certificado que se está comprobando.
- **extension**: estructura devuelta que contiene el puntero de datos de la extensión y la longitud.
- **extension_id**: asignación de números enteros de OID de la tabla anterior.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró el OID de extensión especificado y se devuelven los datos.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).
- **NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida.
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró el OID de extensión especificado en el certificado proporcionado.
- **NX_PTR_ERROR**: (0x07) Puntero de extensión o certificado no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

Buscar y analizar una extensión de uso de clave X.509 en un certificado X.509

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Descripción

Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*). Buscará la extensión de uso de clave y, si la encuentra, devolverá el campo de bits de uso de la clave en el parámetro "bitfield".

Los bits, tal y como se define en la especificación X.509 (RFC 5280), se indican en la tabla siguiente. Una operación AND bit a bit con la máscara de bits adecuada (y comprobando que sea distinto de cero) proporcionará el valor de cada bit.

Tenga en cuenta que la codificación DER del campo de bits elimina los ceros adicionales, por lo que la posición real de los bits en los datos del certificado sin procesar probablemente será diferente de sus posiciones en el campo de bits descodificado. Las máscaras de bits proporcionadas solo están pensadas para usarse en el campo de bits descodificado devuelto por *nx_secure_x509_key_usage_extension_parse* y no con los datos del certificado con codificación DER sin procesar.

En la devolución de llamada de comprobación del certificado, el código de retorno de error NX_SECURE_X509_KEY_USAGE_ERROR está reservado para el uso de la aplicación. Si se produce un error al comprobar el uso de la clave, se puede devolver este valor desde la devolución de llamada para indicar el motivo del error.

| Identificador de NetX Secure                            | Posición de bit | Descripción                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | El certificado se puede utilizar para firmas digitales.                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | El certificado se puede usar para comprobar firmas digitales distintas de las de certificados y CRL.                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | El certificado se puede usar para cifrar claves simétricas (transporte de claves).                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | El certificado se puede usar para cifrar directamente los datos de usuario sin procesar (poco frecuente).                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | El certificado se puede usar para el contrato de claves (como con Diffie-Hellman).                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | El certificado se puede usar para firmar y comprobar otros certificados (el certificado es un certificado CA o ICA).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | La clave pública del certificado se usa para comprobar las firmas en las CRL.                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Se utiliza con el bit de contrato de claves (bit 4): cuando se establece, la clave de certificado solo se puede usar para cifrar durante el acuerdo de claves. Indefinido si no se establece el bit de contrato de claves. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Se utiliza con el bit de contrato de claves (bit 4): cuando se establece, la clave de certificado solo se puede usar para descifrar durante el acuerdo de claves. Indefinido si no se establece el bit de contrato de claves. |

Máscaras de bits y valores de la extensión de uso de clave X.509

### <a name="parameters"></a>Parámetros

- **certificate**: puntero al certificado que se está comprobando.
- **bitfield**: devuelve el campo de bits completo de la extensión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró la extensión de uso de clave y se devuelve el campo de bits.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).
- **NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida (certificado no válido).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró la extensión de uso de clave en el certificado proporcionado.
- **NX_PTR_ERROR**: (0x07) Puntero de campo de bits o certificado no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Consulte también

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
