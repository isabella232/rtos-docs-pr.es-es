---
title: 'Capítulo 4: Descripción de NetX Crypto API de Azure RTOS'
description: Descripción de NetX Crypto API de Azure RTOS
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5bd4cdae28a293ec9ef259bbd29fdb8f8d6dc43f964cbc184290b82ee8f590a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788813"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Capítulo 4: Descripción de NetX Crypto API de Azure RTOS

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Inicializa la biblioteca de NetX Secure.

### <a name="prototype"></a>Prototipo

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Descripción

Esta función inicializa el módulo de la biblioteca de NetX Crypto de Azure RTOS. Antes de utilizar cualquiera de las otras funciones criptográficas, la aplicación debe llamar a esta función para realizar la inicialización y validar la integridad de la biblioteca. Si no se llama a esta función antes de usar otros servicios de NetX Crypto, se devolverán errores.

### <a name="parameters"></a>Parámetros

- **None**

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se inicializó correctamente la biblioteca de NetX Crypto. Las funciones de la biblioteca están ahora listas y se pueden usar.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) No se puede inicializar la biblioteca de criptografía o se produce un error en la comprobación de integridad. La aplicación no puede usar esta biblioteca.

### <a name="example"></a>Ejemplo

TODO

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Recupera el estado actual del módulo habilitado para FIPS.

### <a name="prototype"></a>Prototipo

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Descripción

Este servicio solo está disponible en la biblioteca de compilación de FIPS. Devuelve el estado actual de la biblioteca de NetX Crypto.

### <a name="parameters"></a>Parámetros

- **None**

### <a name="return-values"></a>Valores devueltos

- **Marca de estado:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Los demás valores no son válidos.**

### <a name="example"></a>Ejemplo

TODO

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Inicializa el bloque de control de criptografía AES.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control AES con la cadena de clave especificada. Una vez inicializado el bloque de control AES, la operación AES posterior usará la misma clave y tamaño de clave.

La aplicación puede crear varios bloques de control AES, cada uno de los cuales representa una sesión. Una clave se asigna a un bloque de control. La operación de cifrado o descifrado posterior puede hacer referencia al mismo bloque de control AES sin necesidad de volver a inicializar el bloque de control AES. Si se cambia la clave de la sesión, la aplicación debe volver a inicializar el bloque de control AES con la clave actualizada.

Al llamar a *nx_crypto_method_aes_init()* , se actualiza automáticamente una clave y un tamaño de clave configurados previamente a la nueva clave.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico AES válido. Están disponibles los siguientes métodos criptográficos AES predefinidos:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **key** Apunta a un búfer que contiene la clave AES.
- **key_size_in_bits** Tamaño de la clave, en bits. Los valores válidos son:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Los demás valores no son válidos.**
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control AES. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con AES, el tamaño de los metadatos debe ser *sizeof(NX_AES)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control AES con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) El tamaño de la clave no es válido para AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Realice una operación AES (cifrado o descifrado).

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Descripción

Esta función realiza la operación de cifrado o descifrado AES. El bloque de control AES debe haberse inicializado con *nx_crypto_method_aes_init()* . El algoritmo AES que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

El tamaño del búfer de entrada debe ser un múltiplo de 16 bytes. El tamaño de los datos descifrados es el mismo que el tamaño de los datos de entrada. Si los datos cifrados se rellenaron para lograr un múltiplo par del tamaño de bloque AES, el relleno se incluirá en el búfer de salida y la aplicación debe controlarlo.

Esta operación no conserva la información de estado y no modifica el material de la clave en el bloque de control AES.

Cuando la operación es NX_CRYPTO_SET_ADDITIONAL_DATA y el algoritmo es AES-CCM8, la entrada apunta a datos adicionales e input_length_in_byte es la longitud de los datos adicionales.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. Las operaciones válidas son:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (solo AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (solo AES-CCM8)*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico AES válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_aes_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto cifrado. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes. Debe ser un múltiplo de 16 bytes.
- **iv_ptr** Puntero al vector inicial. No existen restricciones en el búfer del vector inicial.
- **iv_size** Tamaño del bloque de vector inicial, en bytes. Este campo debe tener un valor de 16.
- **output_buffer** Puntero al área de memoria de AES para almacenar los datos de texto sin cifrar. La aplicación debe asignar espacio para el búfer de salida. El búfer de salida se puede superponer al búfer de entrada. El búfer de salida se puede superponer al búfer de entrada si comparten la misma dirección de inicio.
- **output_buffer_size** Tamaño del búfer de salida en bytes. El tamaño del búfer de salida debe ser al menos igual al tamaño del búfer de entrada y debe ser un múltiplo de 16 bytes.
- **crypto_metadata** Puntero al bloque de control AES utilizado en *_nx_crypto_method_aes_init()\*.\**
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con AES, el tamaño de los metadatos debe ser *sizeof(NX_AES)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se ha especificado un algoritmo AES no válido.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Limpia el bloque de control AES.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control AES después de determinar que esta sesión AES ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control AES utilizado en *_nx_crypto_method_aes_init()\*.\**

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Inicializa el bloque de control 3DES.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control Triple DES (3DES) con las tres cadenas de clave especificadas. Las cadenas de clave deben ser de 8 bytes cada una. Las tres claves DES se deben concatenar en memoria contigua de un búfer de 24 bytes. En el caso de la compilación compatible con FIPS, las tres claves deben ser diferentes entre sí o la función devolverá el error NX_CRYPTO_INVALID_KEY. Una vez inicializado el bloque de control 3DES, las operaciones 3DES posteriores utilizarán las mismas claves.

Una aplicación puede crear varios bloques de control 3DES, cada uno de los cuales representa una sesión. Una clave se asigna a un bloque de control y las sucesivas operaciones de cifrado o descifrado pueden hacer referencia al mismo bloque de control sin necesidad de volver a inicializarse. Si se cambia la clave de una sesión, la aplicación tendrá que reinicializar el bloque de control con la clave actualizada.

Al llamar a *nx_crypto_method_3des_init()* , se actualiza automáticamente una clave configurada previamente a las nuevas claves.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico 3DES válido. Está disponible el siguiente método de cifrado 3DES predefinido: ***crypto_method_3des***.
- **key** Apunta a un búfer que contiene la clave Tres (3) DES.
- **key_size_in_bits** Debe ser 192 (3 claves, cada 64 bits).
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador determina el bloque de control 3DES que se está inicializando. Las operaciones 3DES posteriores (cifrado, descifrado y limpieza) utilizan este identificador para tener acceso al bloque de control 3DES
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control 3DES. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. En el caso de 3DES, el tamaño de los metadatos debe ser *sizeof(NX_3DES)* .

### <a name="return-value"></a>Valor devuelto

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control 3DES con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) El tamaño de la clave no es válido para 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Cifra o descifra con 3DES.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza la operación de cifrado o descifrado con 3DES. El bloque de control 3DES se debe haber inicializado con *nx_crypto_method_3des_init()* . El algoritmo 3DES que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

El tamaño del búfer de entrada debe ser un múltiplo de 8 bytes. El tamaño de los datos descifrados es el mismo que el tamaño de los datos de entrada. Si los datos cifrados se rellenaron para lograr un múltiplo par del tamaño de bloque 3DES, el relleno se incluirá en el búfer de salida y la aplicación debe controlarlo.

Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control 3DES.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. Las operaciones válidas son:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **handle** El identificador inicializado por *_nx_crypto_method_3des_init()* .
- **method** Puntero al método criptográfico 3DES válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_3des_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto cifrado.
No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes. Debe ser un múltiplo de 8 bytes.
- **iv_ptr** Puntero al vector inicial. No existen restricciones en el búfer del vector inicial.
- **iv_size** Tamaño del bloque de vector inicial, en bytes. Este campo debe tener un valor de 8.
- **output_buffer** Puntero al área de memoria de 3DES para almacenar los datos de texto sin cifrar. La aplicación debe asignar espacio para el búfer de salida. El búfer de salida se puede superponer al búfer de entrada. El búfer de salida se puede superponer al búfer de entrada si comparten la misma dirección de inicio.
- **output_buffer_size** Tamaño del búfer de salida en bytes. El tamaño del búfer de salida debe ser al menos igual al tamaño del búfer de entrada y debe ser un múltiplo de 8 bytes.
- **crypto_metadata** Puntero al bloque de control 3DES utilizado en *_nx_crypto_method_3des_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. En el caso de 3DES, el tamaño de los metadatos debe ser *sizeof(NX_3DES)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="description"></a>Descripción

Esta función realiza el cifrado 3DES. El bloque de control 3DES se debe haber inicializado con *nx_crypto_method_3des_init()* . Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control 3DES. Tenga en cuenta que esta función no agrega relleno, por lo que el autor de la llamada deberá controlar el relleno antes de invocar la operación de cifrado.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control 3DES con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Limpia el bloque de control 3DES.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control 3DES después de determinar que esta sesión 3DES ya no se necesita.

### <a name="parameters"></a>Parámetros

- **handle** El identificador inicializado por *_nx_crypto_method_3des_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión 3DES.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Inicializa el bloque de control criptográfico DRBG.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control DRBG con la cadena de clave especificada. Una vez que se inicializa el bloque de control DRBG, la siguiente operación DRBG usará el mismo bloque de control.

La aplicación puede crear varios bloques de control DRBG, cada uno de los cuales representa una sesión. Al inicializar el bloque de control DRBG, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control DRBG, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico DRBG válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_drbg*
- **key** Este campo no se usa con DRBG.
- **key_size_in_bits** Este campo no se usa con DRBG.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control DRBG. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con DRBG, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_DRBG)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control DRBG con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Realiza una operación DRBG.

### <a name="prototype"></a>Prototipo

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación DRBG. El bloque de control DRBG se debe haber inicializado con *nx_crypto_method_drbg_init()* . El algoritmo DRBG que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*. De forma predeterminada, se usa AES-128 con DRBG.

Cuando la operación es NX_CRYPTO_DRBG_OPTIONS_SET, la entrada apunta a la estructura NX_CRYPTO_DRBG_OPTIONS. Cuando la operación es NX_CRYPTO_DRBG_INSTANTIATE, la clave apunta a nonce y la entrada apunta a la cadena de personalización. Cuando la operación es NX_CRYPTO_DRBG_RESEED o NX_CRYPTO_DRBG_GENERATE, la entrada apunta a una entrada adicional.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico DRBG válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_drbg_init_()* .
- **key** Puntero a nonce para la operación de creación de instancias. Este campo no se utiliza con otras operaciones.
- **key_size_in_bits** Tamaño de nonce, en bits. Este campo no se utiliza con otras operaciones.
- **input** Cuando la operación es NX_CRYPTO_DRBG_OPTIONS_SET, este campo apunta a opciones DRBG. Cuando la operación es NX_CRYPTO_DRBG_INSTANTIATE, este campo apunta a una cadena de personalización. Cuando la operación es NX_CRYPTO_DRBG_RESEED o NX_CRYPTO_DRBG_GENERATE, este campo apunta a datos de entrada adicionales.
- **input_length_in_byte** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se usa con DRBG.
- **output** Cuando la operación es NX_CRYPTO_DRBG_GENERATE, este campo apunta al área de memoria del DRBG generado. De lo contrario, este campo no se utiliza.
- **output_length_in_byte** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control DRBG usado en *_nx_crypto_method_drbg_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con DRBG, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_DRBG)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo DRBG no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Limpia el bloque de control DRBG.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control DRBG después de determinar que esta sesión DRBG ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control DRBG usado en *_nx_crypto_method_drbg_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Inicializa el bloque de control criptográfico ECDH.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control ECDH con la cadena de clave especificada. Una vez inicializado el bloque de control ECDH, la siguiente operación ECDH debe usar el mismo bloque de control.

La aplicación puede crear varios bloques de control ECDH, cada uno de los cuales representa una sesión. Al inicializar el bloque de control ECDH, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control ECDH, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico ECDH válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_ecdh*
- **key** Este campo no se usa con ECDH.
- **key_size_in_bits** Este campo no se usa con ECDH.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control ECDH. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con ECDH, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDH)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control ECDH con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Realiza la operación ECDH.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza la operación ECDH. El bloque de control ECDH debe haberse inicializado con *nx_crypto_method_ecdh_init()* . El algoritmo ECDH que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Cuando la operación es NX_CRYPTO_EC_CURVE_SET, la entrada apunta al método criptográfico de la curva elíptica. Cuando la operación es NX_CRYPTO_EC_KEY_PAIR_GENERATE, la salida apunta a la estructura NX_CRYPTO_EXTENDED_OUTPUT y el par de claves se copia en nx_crypto_extended_output_data. Cuando la operación es NX_CRYPTO_DH_SETUP, la clave pública se devuelve a nx_crypto_extended_output_data. Cuando la operación es NX_CRYPTO_DH_KEY_PAIR_IMPORT, la entrada apunta a la clave pública y la clave apunta a la clave privada. Cuando la operación es NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, la clave privada se copia en nx_crypto_extended_output_data. Cuando la operación es NX_CRYPTO_DH_CALCULATE, la entrada apunta a la clave pública remota y el secreto compartido se copia en nx_crypto_extended_output_data.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico ECDH válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_ecdh_init_()* .
- **key** Cuando la operación es NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo apunta a la clave privada. De lo contrario, este campo no se utiliza con ECDH.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo apunta al método criptográfico de la curva elíptica. Cuando la operación es NX_CRYPTO_DH_SETUP, no se utiliza este campo. Cuando la operación es NX_CRYPTO_DH_CALCULATE, este campo apunta a un búfer que contiene datos de texto de entrada. Cuando la operación es NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo apunta a una clave pública.
- **input_length_in_byte** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con ECDH.
- **output** Cuando la operación es NX_CRYPTO_EC_CURVE_SET o NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo no se utiliza. Cuando la operación es NX_CRYPTO_DH_SETUP, este campo apunta al área de memoria de la clave pública ECDH generada. Cuando la operación es NX_CRYPTO_DH_CALCULATE, este campo apunta al área de memoria del secreto compartido ECDH generado.
- **output_length_in_byte** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control ECDH utilizado en *_nx_crypto_method_ecdh_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con ECDH, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDH)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo ECDH no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Limpia el bloque de control ECDH.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control ECDH después de determinar que esta sesión ECDH ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control ECDH utilizado en *_nx_crypto_method_ecdh_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Inicializa el bloque de control criptográfico ECDSA.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control ECDSA con la cadena de clave especificada. Una vez inicializado el bloque de control ECDSA, la operación ECDSA posterior debe usar el mismo bloque de control.

La aplicación puede crear varios bloques de control ECDSA, cada uno de los cuales representa una sesión. Al inicializar el bloque de control ECDSA, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control ECDSA, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico ECDSA válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_ecdsa*
- **key** Este campo no se usa con ECDSA.
- **key_size_in_bits** Este campo no se usa con ECDSA.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control ECDSA. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con ECDSA, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDSA)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control ECDSA con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Realiza una operación ECDSA.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación ECDSA. El bloque de control ECDSA debe haberse inicializado con *nx_crypto_method_ecdsa_init()* . El algoritmo ECDSA que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Cuando la operación es NX_CRYPTO_EC_CURVE_SET, la entrada apunta al método criptográfico de la curva elíptica. Cuando la operación es NX_CRYPTO_EC_KEY_PAIR_GENERATE, la salida apunta a la estructura NX_CRYPTO_EXTENDED_OUTPUT y el par de claves se copia en nx_crypto_extended_output_data.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico ECDSA válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_ecdsa_init_()* .
- **key** Apunta a la clave cuando la operación es NX_CRYPTO_VERIFY. No hay restricciones en el búfer de claves. Este campo no se utiliza con otros valores de operación.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo apunta al método criptográfico de la curva elíptica. De lo contrario, este campo apunta a un búfer que contiene datos de texto de entrada.
- **input_length_in_byte** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con ECDSA.
- **output** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo no se utiliza. Cuando la operación es NX_CRYPTO_AUTHENTICATE, este campo apunta al área de memoria de la firma ECDSA generada. Cuando la operación es NX_CRYPTO_VERIFY, este campo apunta al área de memoria de la firma ECDSA comprobada.
- **output_length_in_byte** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control ECDSA utilizado en *_nx_crypto_method_ecdsa_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con ECDSA, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDSA)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo ECDSA no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Limpia el bloque de control ECDSA.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control ECDSA después de determinar que esta sesión ECDSA ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control ECDSA utilizado en *_nx_crypto_method_ecdsa_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Inicializa el bloque de control criptográfico HMAC MD5.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control HMAC MD5 con la cadena de clave especificada. Una vez inicializado el bloque de control de HMAC MD5, la operación HMAC MD5 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control HMAC MD5, cada uno de los cuales representa una sesión. Al inicializar el bloque de control HMAC MD5, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control HMAC MD5, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico HMAC MD5 válido.
Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_hmac_md5*
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC MD5. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5_HMAC)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC MD5 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Realiza una operación hash de HMAC MD5.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de HMAC MD5. El bloque de control HMAC MD5 se debe haber inicializado con *nx_crypto_method_hmac_md5_init()* . El algoritmo HMAC MD5 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 16 bytes.

Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control HMAC MD5.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico HMAC MD5 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_md5_init()* .
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se usa con HMAC MD5.
- **iv_size** Este campo no se usa con HMAC MD5.
- **output_buffer** Puntero al área de memoria para el hash de HMAC MD5 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control HMAC MD5 utilizado en *_nx_crypto_method_hmac_md5_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5_HMAC)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC MD5 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Inicializa el bloque de control criptográfico HMAC SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control HMAC SHA1 con la cadena de clave especificada. Una vez inicializado el bloque de control HMAC SHA1, la operación HMAC SHA1 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control HMAC SHA1, cada uno de los cuales representa una sesión. Al inicializar el bloque de control HMAC SHA1, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control HMAC SHA1, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico HMAC SHA1 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_hmac_sha1*
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA1. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1_HMAC)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA1 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Realiza una operación hash de HMAC SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de HMAC SHA1. El bloque de control HMAC SHA1 se debe haber inicializado con *nx_crypto_method_hmac_sha1_init()* . El algoritmo HMAC SHA1 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 20 bytes.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico HMAC SHA1 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha1_init()* .
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se usa con HMAC SHA1.
- **iv_ptr** Este campo no se usa con HMAC SHA1.
- **output_buffer** Puntero al área de memoria para el hash de HMAC SHA1 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control HMAC SHA1 utilizado en *_nx_crypto_method_hmac_sha1_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1_HMAC)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA1 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Limpia el bloque de control HMAC SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control HMAC SHA1 después de determinar que esta sesión HMAC SHA1 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control HMAC SHA1 utilizado en *_nx_crypto_method_hmac_sha1_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Inicializa el bloque de control criptográfico HMAC SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control HMAC SHA256 con la cadena de clave especificada. Una vez inicializado el bloque de control HMAC SHA256, la operación HMAC SHA256 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control HMAC SHA256, cada uno de los cuales representa una sesión. Al inicializar el bloque de control HMAC SH256, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control HMAC SHA256, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico HMAC SHA256 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA256. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256_HMAC)*

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA256 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Realiza una operación hash de HMAC SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de HMAC SHA256. El bloque de control HMAC SHA256 se debe haber inicializado con *nx_crypto_method_hmac_sha256_init()* . El algoritmo HMAC SHA256 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 32 bytes para SHA256 o de 28 bytes para SHA224.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico HMAC SHA256 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha256_init()* .
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se usa con HMAC SHA256.
- **iv_ptr** Este campo no se usa con HMAC SHA256.
- **output_buffer** Puntero al área de memoria para el hash de HMAC SHA256 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control HMAC SHA256 utilizado en *_nx_crypto_method_hmac_sha256_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256_HMAC)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA256 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Limpia el bloque de control HMAC SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control HMAC SHA256 después de determinar que esta sesión HMAC SHA256 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control HMAC SHA256 utilizado en *_nx_crypto_method_hmac_sha256_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Inicializa el bloque de control criptográfico HMAC SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control HMAC SHA512 con la cadena de clave especificada. Una vez inicializado el bloque de control HMAC SHA512, la operación HMAC SHA512 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control HMAC SHA512, cada uno de los cuales representa una sesión. Al inicializar el bloque de control HMAC SH512, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control HMAC SHA512, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico HMAC SHA512 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA512. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA512 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Realiza una operación hash de HMAC SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de HMAC SHA512. El bloque de control HMAC SHA512 se debe haber inicializado con *nx_crypto_method_hmac_sha512_init()* . El algoritmo HMAC SHA512 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 64 bytes para SHA512 o de 48 bytes para SHA384.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico HMAC SHA512 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha512_init()* .
- **key** Apunta a la clave. No hay restricciones en el búfer de claves.
- **key_size_in_bits** Tamaño de la clave, en bits.
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se usa con HMAC SHA512.
- **iv_ptr** Este campo no se usa con HMAC SHA512.
- **output_buffer** Puntero al área de memoria para el hash de HMAC SHA512 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes.
- **crypto_metadata** Puntero al bloque de control HMAC SHA512 utilizado en *_nx_crypto_method_hmac_sha512_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con HMAC SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA512 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Limpia el bloque de control HMAC SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control HMAC SHA512 después de determinar que esta sesión HMAC SHA512 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control HMAC SHA512 utilizado en *_nx_crypto_method_hmac_sha512_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

### <a name="example"></a>Ejemplo 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Inicializa el bloque de control criptográfico MD5.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control MD5 con la cadena de clave especificada. Una vez inicializado el bloque de control MD5, la operación MD5 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control MD5; cada uno representa una sesión. Al inicializar el bloque de control MD5, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control MD5, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico MD5 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_md5*
- **key** Este campo no se usa con MD5.
- **key_size_in_bits** Este campo no se usa con MD5.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control MD5. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control MD5 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

### <a name="example"></a>Ejemplo

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Realiza una operación hash de MD5.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de MD5. El bloque de control MD5 debe haberse inicializado con *nx_crypto_method_md5_init()* . El algoritmo MD5 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 16 bytes.

Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control MD5.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico MD5 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_md5_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con MD5.
- **iv_ptr** Este campo no se utiliza con MD5.
- **output_buffer** Puntero al área de memoria para el hash de MD5 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes. Con MD5, el tamaño del búfer debe ser de 16 bytes.
- **crypto_metadata** Puntero al bloque de control MD5 utilizado en *_nx_crypto_method_md5_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se ha especificado un algoritmo MD5 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Limpia el bloque de control MD5.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control MD5 después de determinar que esta sesión MD5 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control MD5 utilizado en *_nx_crypto_method_md5_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Inicializa el bloque de control criptográfico SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control SHA1 con la cadena de clave especificada. Una vez inicializado el bloque de control SHA1, la operación SHA1 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control SHA1, cada uno de los cuales representa una sesión. Al inicializar el bloque de control SHA1, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control SHA1, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico SHA1 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_sha1*
- **key** Este campo no se usa con SHA1.
- **key_size_in_bits** Este campo no se usa con SHA1.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA1. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA1 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Realiza una operación hash de SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de SHA1. El bloque de control SHA1 se debe haber inicializado con *nx_crypto_method_hmac_sha1_init()* . El algoritmo SHA1 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 20 bytes.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico SHA1 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha1_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con SHA1.
- **iv_ptr** Este campo no se utiliza con SHA1.
- **output_buffer** Puntero al área de memoria para el hash de SHA1 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes. Con SHA1, el tamaño del búfer debe ser de 20 bytes.
- **crypto_metadata** Puntero al bloque de control SHA1 utilizado en *_nx_crypto_method_sha1_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA1 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

### <a name="example"></a>Ejemplo

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Limpia el bloque de control SHA1.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control SHA1 después de determinar que esta sesión SHA1 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control SHA1 utilizado en *_nx_crypto_method_sha1_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Inicializa el bloque de control criptográfico SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control SHA256 con la cadena de clave especificada. Una vez inicializado el bloque de control SHA256, la operación SHA256 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control SHA256, cada uno de los cuales representa una sesión. Al inicializar el bloque de control SHA256, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control SHA256, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico SHA256 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **key** Este campo no se usa con SHA256.
- **key_size_in_bits** Este campo no se usa con SHA256.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA256. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA256 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Realiza una operación hash de SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de SHA256. El bloque de control SHA256 se debe haber inicializado con ***nx_crypto_method_sha256_init()***. El algoritmo SHA256 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 32 bytes para SHA256 o de 28 bytes para SHA224.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico SHA256 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha256_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con SHA256.
- **iv_ptr** Este campo no se utiliza con SHA256.
- **output_buffer** Puntero al área de memoria para el hash de SHA256 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes. Con SHA256, el tamaño del búfer debe ser de 32 bytes. Con SHA224, el tamaño del búfer debe ser de 28 bytes.
- **crypto_metadata** Puntero al bloque de control SHA2 utilizado en *_nx_crypto_method_sha2_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA256 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Limpia el bloque de control SHA256.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control SHA256 después de determinar que esta sesión SHA256 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control SHA256 utilizado en *_nx_crypto_method_sha256_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Inicializa el bloque de control criptográfico SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Descripción

Esta función inicializa el bloque de control SHA512 con la cadena de clave especificada. Una vez inicializado el bloque de control SHA512, la operación SHA512 posterior usará el mismo bloque de control.

La aplicación puede crear varios bloques de control SHA512, cada uno de los cuales representa una sesión. Al inicializar el bloque de control SHA512, se inicia una nueva sesión de cálculo de hash. Al volver a inicializar el bloque de control SHA512, se abandona la sesión actual y se inicia una nueva.

### <a name="parameters"></a>Parámetros

- **method** Puntero a un bloque de control de método criptográfico SHA512 válido. Están disponibles los siguientes métodos criptográficos predefinidos:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **key** Este campo no se usa con SHA512.
- **key_size_in_bits** Este campo no se usa con SHA512.
- **handle** Este servicio devuelve un identificador al autor de la llamada. El identificador depende de la implementación y no se utiliza en esta implementación. La aplicación pasará NULL como valor del identificador.
- **crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA512. La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512)* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA512 con la clave y el tamaño de clave.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Realiza una operación hash de SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Descripción

Esta función realiza una operación hash de SHA512. El bloque de control SHA512 se debe haber inicializado con *nx_crypto_method_hmac_sha512_init()* . El algoritmo SHA512 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.

Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 64 bytes para SHA512 o de 48 bytes para SHA384.

### <a name="parameters"></a>Parámetros

- **op** Tipo de operación que se va a ejecutar. La operación válida es:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **method** Puntero al método criptográfico SHA512 válido. El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha512_init()* .
- **input_data** Apunta a un búfer que contiene datos de texto de entrada. No hay restricciones en el búfer de entrada.
- **input_data_size** Tamaño de los datos de entrada, en bytes.
- **iv_ptr** Este campo no se utiliza con SHA512.
- **iv_ptr** Este campo no se utiliza con SHA512.
- **output_buffer** Puntero al área de memoria para el hash de SHA512 generado.
- **output_buffer_size** Tamaño del búfer de salida en bytes. Con SHA512, el tamaño del búfer debe ser de 64 bytes. Con SHA384, el tamaño del búfer debe ser de 48 bytes.
- **crypto_metadata** Puntero al bloque de control SHA512 utilizado en *_nx_crypto_method_sha512_init()* .
- **crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata. Con SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .
- **packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.
- **nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto. Los valores pasados se omiten de forma silenciosa.

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.
- **NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA512 no válido.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Limpia el bloque de control SHA512.

### <a name="prototype"></a>Prototipo

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para limpiar el bloque de control SHA512 después de determinar que esta sesión SHA512 ya no se necesita.

### <a name="parameters"></a>Parámetros

- **crypto_metadata** Puntero al bloque de control SHA512 utilizado en *_nx_crypto_method_sha512_init()* .

### <a name="return-values"></a>Valores devueltos

- **NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.