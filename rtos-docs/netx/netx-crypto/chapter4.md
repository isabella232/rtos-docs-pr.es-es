---
title: 'Capítulo 4: Descripción de NetX Crypto API de Azure RTOS'
description: Descripción de NetX Crypto API de Azure RTOS
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815261"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="00f8f-103">Capítulo 4: Descripción de NetX Crypto API de Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="00f8f-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="00f8f-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="00f8f-104">nx_crypto_initialize</span></span>

<span data-ttu-id="00f8f-105">Inicializa la biblioteca de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="00f8f-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-106">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="00f8f-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-107">Description</span></span>

<span data-ttu-id="00f8f-108">Esta función inicializa el módulo de la biblioteca de NetX Crypto de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="00f8f-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="00f8f-109">Antes de utilizar cualquiera de las otras funciones criptográficas, la aplicación debe llamar a esta función para realizar la inicialización y validar la integridad de la biblioteca.</span><span class="sxs-lookup"><span data-stu-id="00f8f-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="00f8f-110">Si no se llama a esta función antes de usar otros servicios de NetX Crypto, se devolverán errores.</span><span class="sxs-lookup"><span data-stu-id="00f8f-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-111">Parameters</span></span>

- <span data-ttu-id="00f8f-112">**None**</span><span class="sxs-lookup"><span data-stu-id="00f8f-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-113">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-113">Return Values</span></span>

- <span data-ttu-id="00f8f-114">**NX_CRYPTO_SUCCESS** (0x00) Se inicializó correctamente la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="00f8f-115">Las funciones de la biblioteca están ahora listas y se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="00f8f-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) No se puede inicializar la biblioteca de criptografía o se produce un error en la comprobación de integridad.</span><span class="sxs-lookup"><span data-stu-id="00f8f-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="00f8f-117">La aplicación no puede usar esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="00f8f-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="00f8f-118">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="00f8f-118">Example</span></span>

<span data-ttu-id="00f8f-119">TODO</span><span class="sxs-lookup"><span data-stu-id="00f8f-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="00f8f-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="00f8f-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="00f8f-121">Recupera el estado actual del módulo habilitado para FIPS.</span><span class="sxs-lookup"><span data-stu-id="00f8f-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-122">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="00f8f-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-123">Description</span></span>

<span data-ttu-id="00f8f-124">Este servicio solo está disponible en la biblioteca de compilación de FIPS.</span><span class="sxs-lookup"><span data-stu-id="00f8f-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="00f8f-125">Devuelve el estado actual de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-126">Parameters</span></span>

- <span data-ttu-id="00f8f-127">**None**</span><span class="sxs-lookup"><span data-stu-id="00f8f-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-128">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-128">Return Values</span></span>

- <span data-ttu-id="00f8f-129">**Marca de estado:**</span><span class="sxs-lookup"><span data-stu-id="00f8f-129">**Status Flag:**</span></span>
  - <span data-ttu-id="00f8f-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="00f8f-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="00f8f-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="00f8f-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="00f8f-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="00f8f-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="00f8f-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="00f8f-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="00f8f-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="00f8f-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="00f8f-135">**Los demás valores no son válidos.**</span><span class="sxs-lookup"><span data-stu-id="00f8f-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="00f8f-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="00f8f-136">Example</span></span>

<span data-ttu-id="00f8f-137">TODO</span><span class="sxs-lookup"><span data-stu-id="00f8f-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="00f8f-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="00f8f-139">Inicializa el bloque de control de criptografía AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-141">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-141">Description</span></span>

<span data-ttu-id="00f8f-142">Esta función inicializa el bloque de control AES con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="00f8f-143">Una vez inicializado el bloque de control AES, la operación AES posterior usará la misma clave y tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="00f8f-144">La aplicación puede crear varios bloques de control AES, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-145">Una clave se asigna a un bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-145">A key is assigned to a control block.</span></span> <span data-ttu-id="00f8f-146">La operación de cifrado o descifrado posterior puede hacer referencia al mismo bloque de control AES sin necesidad de volver a inicializar el bloque de control AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="00f8f-147">Si se cambia la clave de la sesión, la aplicación debe volver a inicializar el bloque de control AES con la clave actualizada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="00f8f-148">Al llamar a *nx_crypto_method_aes_init()* , se actualiza automáticamente una clave y un tamaño de clave configurados previamente a la nueva clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-149">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-149">Parameters</span></span>

- <span data-ttu-id="00f8f-150">**method** Puntero a un bloque de control de método criptográfico AES válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="00f8f-151">Están disponibles los siguientes métodos criptográficos AES predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="00f8f-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="00f8f-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="00f8f-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="00f8f-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="00f8f-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="00f8f-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="00f8f-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="00f8f-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="00f8f-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="00f8f-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="00f8f-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="00f8f-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="00f8f-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="00f8f-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="00f8f-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="00f8f-160">**key** Apunta a un búfer que contiene la clave AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="00f8f-161">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="00f8f-162">Los valores válidos son:</span><span class="sxs-lookup"><span data-stu-id="00f8f-162">Valid values are:</span></span>
  - <span data-ttu-id="00f8f-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="00f8f-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="00f8f-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="00f8f-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="00f8f-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="00f8f-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="00f8f-166">**Los demás valores no son válidos.**</span><span class="sxs-lookup"><span data-stu-id="00f8f-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="00f8f-167">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-168">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-169">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-170">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="00f8f-171">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-172">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-173">Con AES, el tamaño de los metadatos debe ser *sizeof(NX_AES)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-174">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-174">Return Values</span></span>

- <span data-ttu-id="00f8f-175">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control AES con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-176">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-177">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) El tamaño de la clave no es válido para AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="00f8f-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="00f8f-180">Realice una operación AES (cifrado o descifrado).</span><span class="sxs-lookup"><span data-stu-id="00f8f-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-181">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-182">Description</span></span>

<span data-ttu-id="00f8f-183">Esta función realiza la operación de cifrado o descifrado AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="00f8f-184">El bloque de control AES debe haberse inicializado con *nx_crypto_method_aes_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="00f8f-185">El algoritmo AES que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-186">El tamaño del búfer de entrada debe ser un múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="00f8f-187">El tamaño de los datos descifrados es el mismo que el tamaño de los datos de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="00f8f-188">Si los datos cifrados se rellenaron para lograr un múltiplo par del tamaño de bloque AES, el relleno se incluirá en el búfer de salida y la aplicación debe controlarlo.</span><span class="sxs-lookup"><span data-stu-id="00f8f-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="00f8f-189">Esta operación no conserva la información de estado y no modifica el material de la clave en el bloque de control AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="00f8f-190">Cuando la operación es NX_CRYPTO_SET_ADDITIONAL_DATA y el algoritmo es AES-CCM8, la entrada apunta a datos adicionales e input_length_in_byte es la longitud de los datos adicionales.</span><span class="sxs-lookup"><span data-stu-id="00f8f-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-191">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-191">Parameters</span></span>

- <span data-ttu-id="00f8f-192">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-193">Las operaciones válidas son:</span><span class="sxs-lookup"><span data-stu-id="00f8f-193">Valid opertions are:</span></span>
  - <span data-ttu-id="00f8f-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="00f8f-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="00f8f-196">*NX_CRYPTO_AUTHENTICATE (solo AES-XCBC)*</span><span class="sxs-lookup"><span data-stu-id="00f8f-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="00f8f-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (solo AES-CCM8)*</span><span class="sxs-lookup"><span data-stu-id="00f8f-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="00f8f-198">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-199">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-200">**method** Puntero al método criptográfico AES válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="00f8f-201">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_aes_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="00f8f-202">**input_data** Apunta a un búfer que contiene datos de texto cifrado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="00f8f-203">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-204">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="00f8f-205">Debe ser un múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="00f8f-206">**iv_ptr** Puntero al vector inicial.</span><span class="sxs-lookup"><span data-stu-id="00f8f-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="00f8f-207">No existen restricciones en el búfer del vector inicial.</span><span class="sxs-lookup"><span data-stu-id="00f8f-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="00f8f-208">**iv_size** Tamaño del bloque de vector inicial, en bytes. Este campo debe tener un valor de 16.</span><span class="sxs-lookup"><span data-stu-id="00f8f-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="00f8f-209">**output_buffer** Puntero al área de memoria de AES para almacenar los datos de texto sin cifrar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="00f8f-210">La aplicación debe asignar espacio para el búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="00f8f-211">El búfer de salida se puede superponer al búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="00f8f-212">El búfer de salida se puede superponer al búfer de entrada si comparten la misma dirección de inicio.</span><span class="sxs-lookup"><span data-stu-id="00f8f-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="00f8f-213">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-214">El tamaño del búfer de salida debe ser al menos igual al tamaño del búfer de entrada y debe ser un múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="00f8f-215">**crypto_metadata** Puntero al bloque de control AES utilizado en *_nx_crypto_method_aes_init()\*.\**</span><span class="sxs-lookup"><span data-stu-id="00f8f-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="00f8f-216">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-217">Con AES, el tamaño de los metadatos debe ser *sizeof(NX_AES)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="00f8f-218">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-219">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-220">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-221">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-222">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-222">Return Values</span></span>

- <span data-ttu-id="00f8f-223">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="00f8f-224">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-225">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se ha especificado un algoritmo AES no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="00f8f-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="00f8f-228">Limpia el bloque de control AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-229">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-230">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-230">Description</span></span>

<span data-ttu-id="00f8f-231">La aplicación llama a esta función para limpiar el bloque de control AES después de determinar que esta sesión AES ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-232">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-232">Parameters</span></span>

- <span data-ttu-id="00f8f-233">**crypto_metadata** Puntero al bloque de control AES utilizado en *_nx_crypto_method_aes_init()\*.\**</span><span class="sxs-lookup"><span data-stu-id="00f8f-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-234">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-234">Return Values</span></span>

- <span data-ttu-id="00f8f-235">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión AES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="00f8f-236">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="00f8f-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="00f8f-238">Inicializa el bloque de control 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-239">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-240">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-240">Description</span></span>

<span data-ttu-id="00f8f-241">Esta función inicializa el bloque de control Triple DES (3DES) con las tres cadenas de clave especificadas.</span><span class="sxs-lookup"><span data-stu-id="00f8f-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="00f8f-242">Las cadenas de clave deben ser de 8 bytes cada una.</span><span class="sxs-lookup"><span data-stu-id="00f8f-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="00f8f-243">Las tres claves DES se deben concatenar en memoria contigua de un búfer de 24 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="00f8f-244">En el caso de la compilación compatible con FIPS, las tres claves deben ser diferentes entre sí o la función devolverá el error NX_CRYPTO_INVALID_KEY.</span><span class="sxs-lookup"><span data-stu-id="00f8f-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="00f8f-245">Una vez inicializado el bloque de control 3DES, las operaciones 3DES posteriores utilizarán las mismas claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="00f8f-246">Una aplicación puede crear varios bloques de control 3DES, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="00f8f-247">Una clave se asigna a un bloque de control y las sucesivas operaciones de cifrado o descifrado pueden hacer referencia al mismo bloque de control sin necesidad de volver a inicializarse.</span><span class="sxs-lookup"><span data-stu-id="00f8f-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="00f8f-248">Si se cambia la clave de una sesión, la aplicación tendrá que reinicializar el bloque de control con la clave actualizada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="00f8f-249">Al llamar a *nx_crypto_method_3des_init()* , se actualiza automáticamente una clave configurada previamente a las nuevas claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-250">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-250">Parameters</span></span>

- <span data-ttu-id="00f8f-251">**method** Puntero a un bloque de control de método criptográfico 3DES válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="00f8f-252">Está disponible el siguiente método de cifrado 3DES predefinido: ***crypto_method_3des***.</span><span class="sxs-lookup"><span data-stu-id="00f8f-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="00f8f-253">**key** Apunta a un búfer que contiene la clave Tres (3) DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="00f8f-254">**key_size_in_bits** Debe ser 192 (3 claves, cada 64 bits).</span><span class="sxs-lookup"><span data-stu-id="00f8f-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="00f8f-255">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-256">El identificador determina el bloque de control 3DES que se está inicializando.</span><span class="sxs-lookup"><span data-stu-id="00f8f-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="00f8f-257">Las operaciones 3DES posteriores (cifrado, descifrado y limpieza) utilizan este identificador para tener acceso al bloque de control 3DES</span><span class="sxs-lookup"><span data-stu-id="00f8f-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="00f8f-258">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="00f8f-259">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-260">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-261">En el caso de 3DES, el tamaño de los metadatos debe ser *sizeof(NX_3DES)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="00f8f-262">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="00f8f-262">Return Value</span></span>

- <span data-ttu-id="00f8f-263">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control 3DES con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-264">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-265">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) El tamaño de la clave no es válido para 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="00f8f-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="00f8f-268">Cifra o descifra con 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-269">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-269">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-270">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-270">Description</span></span>

<span data-ttu-id="00f8f-271">Esta función realiza la operación de cifrado o descifrado con 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="00f8f-272">El bloque de control 3DES se debe haber inicializado con *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="00f8f-273">El algoritmo 3DES que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-274">El tamaño del búfer de entrada debe ser un múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="00f8f-275">El tamaño de los datos descifrados es el mismo que el tamaño de los datos de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="00f8f-276">Si los datos cifrados se rellenaron para lograr un múltiplo par del tamaño de bloque 3DES, el relleno se incluirá en el búfer de salida y la aplicación debe controlarlo.</span><span class="sxs-lookup"><span data-stu-id="00f8f-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="00f8f-277">Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-278">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-278">Parameters</span></span>

- <span data-ttu-id="00f8f-279">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-280">Las operaciones válidas son:</span><span class="sxs-lookup"><span data-stu-id="00f8f-280">Valid operations are:</span></span>
  - <span data-ttu-id="00f8f-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="00f8f-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="00f8f-283">**handle** El identificador inicializado por *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="00f8f-284">**method** Puntero al método criptográfico 3DES válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="00f8f-285">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="00f8f-286">**input_data** Apunta a un búfer que contiene datos de texto cifrado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="00f8f-287">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-288">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="00f8f-289">Debe ser un múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="00f8f-290">**iv_ptr** Puntero al vector inicial.</span><span class="sxs-lookup"><span data-stu-id="00f8f-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="00f8f-291">No existen restricciones en el búfer del vector inicial.</span><span class="sxs-lookup"><span data-stu-id="00f8f-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="00f8f-292">**iv_size** Tamaño del bloque de vector inicial, en bytes. Este campo debe tener un valor de 8.</span><span class="sxs-lookup"><span data-stu-id="00f8f-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="00f8f-293">**output_buffer** Puntero al área de memoria de 3DES para almacenar los datos de texto sin cifrar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="00f8f-294">La aplicación debe asignar espacio para el búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="00f8f-295">El búfer de salida se puede superponer al búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="00f8f-296">El búfer de salida se puede superponer al búfer de entrada si comparten la misma dirección de inicio.</span><span class="sxs-lookup"><span data-stu-id="00f8f-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="00f8f-297">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-298">El tamaño del búfer de salida debe ser al menos igual al tamaño del búfer de entrada y debe ser un múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="00f8f-299">**crypto_metadata** Puntero al bloque de control 3DES utilizado en *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="00f8f-300">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-301">En el caso de 3DES, el tamaño de los metadatos debe ser *sizeof(NX_3DES)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="00f8f-302">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-303">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-304">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-305">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="00f8f-306">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-306">Description</span></span>

<span data-ttu-id="00f8f-307">Esta función realiza el cifrado 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="00f8f-308">El bloque de control 3DES se debe haber inicializado con *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="00f8f-309">Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="00f8f-310">Tenga en cuenta que esta función no agrega relleno, por lo que el autor de la llamada deberá controlar el relleno antes de invocar la operación de cifrado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-311">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-311">Return Values</span></span>

- <span data-ttu-id="00f8f-312">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control 3DES con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-313">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-314">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="00f8f-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="00f8f-316">Limpia el bloque de control 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-317">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-318">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-318">Description</span></span>

<span data-ttu-id="00f8f-319">La aplicación llama a esta función para limpiar el bloque de control 3DES después de determinar que esta sesión 3DES ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-320">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-320">Parameters</span></span>

- <span data-ttu-id="00f8f-321">**handle** El identificador inicializado por *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-322">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-322">Return Values</span></span>

- <span data-ttu-id="00f8f-323">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión 3DES.</span><span class="sxs-lookup"><span data-stu-id="00f8f-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="00f8f-324">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="00f8f-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="00f8f-326">Inicializa el bloque de control criptográfico DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-327">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-328">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-328">Description</span></span>

<span data-ttu-id="00f8f-329">Esta función inicializa el bloque de control DRBG con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="00f8f-330">Una vez que se inicializa el bloque de control DRBG, la siguiente operación DRBG usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-331">La aplicación puede crear varios bloques de control DRBG, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-332">Al inicializar el bloque de control DRBG, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-333">Al volver a inicializar el bloque de control DRBG, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-334">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-334">Parameters</span></span>

- <span data-ttu-id="00f8f-335">**method** Puntero a un bloque de control de método criptográfico DRBG válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="00f8f-336">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="00f8f-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="00f8f-338">**key** Este campo no se usa con DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="00f8f-339">**key_size_in_bits** Este campo no se usa con DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="00f8f-340">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-341">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-342">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-343">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="00f8f-344">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-345">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-346">Con DRBG, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_DRBG)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-347">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-347">Return Values</span></span>

- <span data-ttu-id="00f8f-348">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control DRBG con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-349">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-350">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="00f8f-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="00f8f-352">Realiza una operación DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-353">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-353">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-354">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-354">Description</span></span>

<span data-ttu-id="00f8f-355">Esta función realiza una operación DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-355">This function performs DRBG operation.</span></span> <span data-ttu-id="00f8f-356">El bloque de control DRBG se debe haber inicializado con *nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="00f8f-357">El algoritmo DRBG que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="00f8f-358">De forma predeterminada, se usa AES-128 con DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="00f8f-359">Cuando la operación es NX_CRYPTO_DRBG_OPTIONS_SET, la entrada apunta a la estructura NX_CRYPTO_DRBG_OPTIONS.</span><span class="sxs-lookup"><span data-stu-id="00f8f-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="00f8f-360">Cuando la operación es NX_CRYPTO_DRBG_INSTANTIATE, la clave apunta a nonce y la entrada apunta a la cadena de personalización.</span><span class="sxs-lookup"><span data-stu-id="00f8f-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="00f8f-361">Cuando la operación es NX_CRYPTO_DRBG_RESEED o NX_CRYPTO_DRBG_GENERATE, la entrada apunta a una entrada adicional.</span><span class="sxs-lookup"><span data-stu-id="00f8f-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-362">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-362">Parameters</span></span>

- <span data-ttu-id="00f8f-363">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-364">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-364">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="00f8f-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="00f8f-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="00f8f-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="00f8f-368">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-369">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-370">**method** Puntero al método criptográfico DRBG válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="00f8f-371">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_drbg_init_()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="00f8f-372">**key** Puntero a nonce para la operación de creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="00f8f-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="00f8f-373">Este campo no se utiliza con otras operaciones.</span><span class="sxs-lookup"><span data-stu-id="00f8f-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="00f8f-374">**key_size_in_bits** Tamaño de nonce, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="00f8f-375">Este campo no se utiliza con otras operaciones.</span><span class="sxs-lookup"><span data-stu-id="00f8f-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="00f8f-376">**input** Cuando la operación es NX_CRYPTO_DRBG_OPTIONS_SET, este campo apunta a opciones DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="00f8f-377">Cuando la operación es NX_CRYPTO_DRBG_INSTANTIATE, este campo apunta a una cadena de personalización.</span><span class="sxs-lookup"><span data-stu-id="00f8f-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="00f8f-378">Cuando la operación es NX_CRYPTO_DRBG_RESEED o NX_CRYPTO_DRBG_GENERATE, este campo apunta a datos de entrada adicionales.</span><span class="sxs-lookup"><span data-stu-id="00f8f-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="00f8f-379">**input_length_in_byte** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-380">**iv_ptr** Este campo no se usa con DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="00f8f-381">**output** Cuando la operación es NX_CRYPTO_DRBG_GENERATE, este campo apunta al área de memoria del DRBG generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="00f8f-382">De lo contrario, este campo no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="00f8f-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="00f8f-383">**output_length_in_byte** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-384">**crypto_metadata** Puntero al bloque de control DRBG usado en *_nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="00f8f-385">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-386">Con DRBG, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_DRBG)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="00f8f-387">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-388">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-389">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-390">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-391">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-391">Return Values</span></span>

- <span data-ttu-id="00f8f-392">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="00f8f-393">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-394">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo DRBG no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="00f8f-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="00f8f-398">Limpia el bloque de control DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-399">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-400">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-400">Description</span></span>

<span data-ttu-id="00f8f-401">La aplicación llama a esta función para limpiar el bloque de control DRBG después de determinar que esta sesión DRBG ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-402">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-402">Parameters</span></span>

- <span data-ttu-id="00f8f-403">**crypto_metadata** Puntero al bloque de control DRBG usado en *_nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-404">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-404">Return Values</span></span>

- <span data-ttu-id="00f8f-405">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión DRBG.</span><span class="sxs-lookup"><span data-stu-id="00f8f-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="00f8f-406">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="00f8f-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="00f8f-408">Inicializa el bloque de control criptográfico ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-409">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-410">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-410">Description</span></span>

<span data-ttu-id="00f8f-411">Esta función inicializa el bloque de control ECDH con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="00f8f-412">Una vez inicializado el bloque de control ECDH, la siguiente operación ECDH debe usar el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-413">La aplicación puede crear varios bloques de control ECDH, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-414">Al inicializar el bloque de control ECDH, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-415">Al volver a inicializar el bloque de control ECDH, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-416">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-416">Parameters</span></span>

- <span data-ttu-id="00f8f-417">**method** Puntero a un bloque de control de método criptográfico ECDH válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="00f8f-418">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="00f8f-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="00f8f-420">**key** Este campo no se usa con ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="00f8f-421">**key_size_in_bits** Este campo no se usa con ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="00f8f-422">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-423">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-424">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-425">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="00f8f-426">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-427">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-428">Con ECDH, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDH)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-429">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-429">Return Values</span></span>

- <span data-ttu-id="00f8f-430">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control ECDH con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-431">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-432">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="00f8f-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="00f8f-434">Realiza la operación ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-435">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-435">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-436">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-436">Description</span></span>

<span data-ttu-id="00f8f-437">Esta función realiza la operación ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-437">This function performs ECDH operation.</span></span> <span data-ttu-id="00f8f-438">El bloque de control ECDH debe haberse inicializado con *nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="00f8f-439">El algoritmo ECDH que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-440">Cuando la operación es NX_CRYPTO_EC_CURVE_SET, la entrada apunta al método criptográfico de la curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="00f8f-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="00f8f-441">Cuando la operación es NX_CRYPTO_EC_KEY_PAIR_GENERATE, la salida apunta a la estructura NX_CRYPTO_EXTENDED_OUTPUT y el par de claves se copia en nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="00f8f-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="00f8f-442">Cuando la operación es NX_CRYPTO_DH_SETUP, la clave pública se devuelve a nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="00f8f-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="00f8f-443">Cuando la operación es NX_CRYPTO_DH_KEY_PAIR_IMPORT, la entrada apunta a la clave pública y la clave apunta a la clave privada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="00f8f-444">Cuando la operación es NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, la clave privada se copia en nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="00f8f-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="00f8f-445">Cuando la operación es NX_CRYPTO_DH_CALCULATE, la entrada apunta a la clave pública remota y el secreto compartido se copia en nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="00f8f-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-446">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-446">Parameters</span></span>

- <span data-ttu-id="00f8f-447">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-448">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-448">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="00f8f-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="00f8f-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="00f8f-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="00f8f-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="00f8f-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="00f8f-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="00f8f-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="00f8f-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="00f8f-455">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-456">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-457">**method** Puntero al método criptográfico ECDH válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="00f8f-458">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_ecdh_init_()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="00f8f-459">**key** Cuando la operación es NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo apunta a la clave privada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="00f8f-460">De lo contrario, este campo no se utiliza con ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="00f8f-461">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-462">**input** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo apunta al método criptográfico de la curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="00f8f-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="00f8f-463">Cuando la operación es NX_CRYPTO_DH_SETUP, no se utiliza este campo.</span><span class="sxs-lookup"><span data-stu-id="00f8f-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="00f8f-464">Cuando la operación es NX_CRYPTO_DH_CALCULATE, este campo apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-465">Cuando la operación es NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo apunta a una clave pública.</span><span class="sxs-lookup"><span data-stu-id="00f8f-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="00f8f-466">**input_length_in_byte** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-467">**iv_ptr** Este campo no se utiliza con ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="00f8f-468">**output** Cuando la operación es NX_CRYPTO_EC_CURVE_SET o NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="00f8f-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="00f8f-469">Cuando la operación es NX_CRYPTO_DH_SETUP, este campo apunta al área de memoria de la clave pública ECDH generada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="00f8f-470">Cuando la operación es NX_CRYPTO_DH_CALCULATE, este campo apunta al área de memoria del secreto compartido ECDH generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="00f8f-471">**output_length_in_byte** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-472">**crypto_metadata** Puntero al bloque de control ECDH utilizado en *_nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="00f8f-473">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-474">Con ECDH, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDH)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="00f8f-475">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-476">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-477">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-478">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-479">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-479">Return Values</span></span>

- <span data-ttu-id="00f8f-480">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="00f8f-481">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-482">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo ECDH no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="00f8f-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="00f8f-486">Limpia el bloque de control ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-487">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-488">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-488">Description</span></span>

<span data-ttu-id="00f8f-489">La aplicación llama a esta función para limpiar el bloque de control ECDH después de determinar que esta sesión ECDH ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-490">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-490">Parameters</span></span>

- <span data-ttu-id="00f8f-491">**crypto_metadata** Puntero al bloque de control ECDH utilizado en *_nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-492">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-492">Return Values</span></span>

- <span data-ttu-id="00f8f-493">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión ECDH.</span><span class="sxs-lookup"><span data-stu-id="00f8f-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="00f8f-494">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="00f8f-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="00f8f-496">Inicializa el bloque de control criptográfico ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-497">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-498">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-498">Description</span></span>

<span data-ttu-id="00f8f-499">Esta función inicializa el bloque de control ECDSA con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="00f8f-500">Una vez inicializado el bloque de control ECDSA, la operación ECDSA posterior debe usar el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-501">La aplicación puede crear varios bloques de control ECDSA, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-502">Al inicializar el bloque de control ECDSA, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-503">Al volver a inicializar el bloque de control ECDSA, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-504">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-504">Parameters</span></span>

- <span data-ttu-id="00f8f-505">**method** Puntero a un bloque de control de método criptográfico ECDSA válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="00f8f-506">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="00f8f-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="00f8f-508">**key** Este campo no se usa con ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="00f8f-509">**key_size_in_bits** Este campo no se usa con ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="00f8f-510">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-511">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-512">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-513">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="00f8f-514">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-515">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-516">Con ECDSA, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDSA)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-517">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-517">Return Values</span></span>

- <span data-ttu-id="00f8f-518">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control ECDSA con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-519">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-520">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="00f8f-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="00f8f-522">Realiza una operación ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-523">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-523">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-524">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-524">Description</span></span>

<span data-ttu-id="00f8f-525">Esta función realiza una operación ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="00f8f-526">El bloque de control ECDSA debe haberse inicializado con *nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="00f8f-527">El algoritmo ECDSA que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-528">Cuando la operación es NX_CRYPTO_EC_CURVE_SET, la entrada apunta al método criptográfico de la curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="00f8f-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="00f8f-529">Cuando la operación es NX_CRYPTO_EC_KEY_PAIR_GENERATE, la salida apunta a la estructura NX_CRYPTO_EXTENDED_OUTPUT y el par de claves se copia en nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="00f8f-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-530">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-530">Parameters</span></span>

- <span data-ttu-id="00f8f-531">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-532">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-532">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="00f8f-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="00f8f-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="00f8f-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="00f8f-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="00f8f-536">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-537">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-538">**method** Puntero al método criptográfico ECDSA válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="00f8f-539">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_ecdsa_init_()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="00f8f-540">**key** Apunta a la clave cuando la operación es NX_CRYPTO_VERIFY.</span><span class="sxs-lookup"><span data-stu-id="00f8f-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="00f8f-541">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="00f8f-542">Este campo no se utiliza con otros valores de operación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="00f8f-543">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-544">**input** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo apunta al método criptográfico de la curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="00f8f-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="00f8f-545">De lo contrario, este campo apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="00f8f-546">**input_length_in_byte** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-547">**iv_ptr** Este campo no se utiliza con ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="00f8f-548">**output** Cuando la operación es NX_CRYPTO_EC_CURVE_SET, este campo no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="00f8f-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="00f8f-549">Cuando la operación es NX_CRYPTO_AUTHENTICATE, este campo apunta al área de memoria de la firma ECDSA generada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="00f8f-550">Cuando la operación es NX_CRYPTO_VERIFY, este campo apunta al área de memoria de la firma ECDSA comprobada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="00f8f-551">**output_length_in_byte** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-552">**crypto_metadata** Puntero al bloque de control ECDSA utilizado en *_nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="00f8f-553">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-554">Con ECDSA, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_ECDSA)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="00f8f-555">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-556">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-557">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-558">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-559">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-559">Return Values</span></span>

- <span data-ttu-id="00f8f-560">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="00f8f-561">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-562">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo ECDSA no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="00f8f-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="00f8f-566">Limpia el bloque de control ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-567">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-568">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-568">Description</span></span>

<span data-ttu-id="00f8f-569">La aplicación llama a esta función para limpiar el bloque de control ECDSA después de determinar que esta sesión ECDSA ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-570">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-570">Parameters</span></span>

- <span data-ttu-id="00f8f-571">**crypto_metadata** Puntero al bloque de control ECDSA utilizado en *_nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-572">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-572">Return Values</span></span>

- <span data-ttu-id="00f8f-573">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión ECDSA.</span><span class="sxs-lookup"><span data-stu-id="00f8f-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="00f8f-574">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="00f8f-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="00f8f-576">Inicializa el bloque de control criptográfico HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-577">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-578">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-578">Description</span></span>

<span data-ttu-id="00f8f-579">Esta función inicializa el bloque de control HMAC MD5 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="00f8f-580">Una vez inicializado el bloque de control de HMAC MD5, la operación HMAC MD5 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-581">La aplicación puede crear varios bloques de control HMAC MD5, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-582">Al inicializar el bloque de control HMAC MD5, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-583">Al volver a inicializar el bloque de control HMAC MD5, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-584">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-584">Parameters</span></span>

- <span data-ttu-id="00f8f-585">**method** Puntero a un bloque de control de método criptográfico HMAC MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="00f8f-586">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="00f8f-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="00f8f-588">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-588">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-589">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-590">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-591">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-592">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-593">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-594">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="00f8f-595">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-596">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-597">Con HMAC MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-598">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-598">Return Values</span></span>

- <span data-ttu-id="00f8f-599">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC MD5 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-600">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-601">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="00f8f-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="00f8f-603">Realiza una operación hash de HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-604">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-604">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-605">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-605">Description</span></span>

<span data-ttu-id="00f8f-606">Esta función realiza una operación hash de HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="00f8f-607">El bloque de control HMAC MD5 se debe haber inicializado con *nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="00f8f-608">El algoritmo HMAC MD5 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-609">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="00f8f-610">Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-611">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-611">Parameters</span></span>

- <span data-ttu-id="00f8f-612">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-613">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-613">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-617">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-618">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-619">**method** Puntero al método criptográfico HMAC MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="00f8f-620">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="00f8f-621">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-621">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-622">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-623">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-624">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-625">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-626">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-627">**iv_ptr** Este campo no se usa con HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="00f8f-628">**iv_size** Este campo no se usa con HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="00f8f-629">**output_buffer** Puntero al área de memoria para el hash de HMAC MD5 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="00f8f-630">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-631">**crypto_metadata** Puntero al bloque de control HMAC MD5 utilizado en *_nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="00f8f-632">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-633">Con HMAC MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="00f8f-634">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-635">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-636">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-637">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-638">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-638">Return Values</span></span>

- <span data-ttu-id="00f8f-639">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="00f8f-640">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-641">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC MD5 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="00f8f-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="00f8f-645">Inicializa el bloque de control criptográfico HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-646">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-647">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-647">Description</span></span>

<span data-ttu-id="00f8f-648">Esta función inicializa el bloque de control HMAC SHA1 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="00f8f-649">Una vez inicializado el bloque de control HMAC SHA1, la operación HMAC SHA1 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-650">La aplicación puede crear varios bloques de control HMAC SHA1, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-651">Al inicializar el bloque de control HMAC SHA1, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-652">Al volver a inicializar el bloque de control HMAC SHA1, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-653">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-653">Parameters</span></span>

- <span data-ttu-id="00f8f-654">**method** Puntero a un bloque de control de método criptográfico HMAC SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="00f8f-655">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="00f8f-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="00f8f-657">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-657">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-658">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-659">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-660">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-661">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-662">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-663">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="00f8f-664">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-665">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-666">Con HMAC SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-667">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-667">Return Values</span></span>

- <span data-ttu-id="00f8f-668">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA1 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-669">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-670">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="00f8f-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="00f8f-672">Realiza una operación hash de HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-673">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-673">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-674">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-674">Description</span></span>

<span data-ttu-id="00f8f-675">Esta función realiza una operación hash de HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="00f8f-676">El bloque de control HMAC SHA1 se debe haber inicializado con *nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="00f8f-677">El algoritmo HMAC SHA1 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-678">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-679">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-679">Parameters</span></span>

- <span data-ttu-id="00f8f-680">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-681">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-681">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-685">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-686">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-687">**method** Puntero al método criptográfico HMAC SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="00f8f-688">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="00f8f-689">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-689">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-690">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-691">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-692">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-693">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-694">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-695">**iv_ptr** Este campo no se usa con HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="00f8f-696">**iv_ptr** Este campo no se usa con HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="00f8f-697">**output_buffer** Puntero al área de memoria para el hash de HMAC SHA1 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="00f8f-698">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-699">**crypto_metadata** Puntero al bloque de control HMAC SHA1 utilizado en *_nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="00f8f-700">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-701">Con HMAC SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="00f8f-702">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-703">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-704">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-705">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-706">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-706">Return Values</span></span>

- <span data-ttu-id="00f8f-707">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="00f8f-708">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-709">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA1 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="00f8f-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="00f8f-713">Limpia el bloque de control HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-714">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-715">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-715">Description</span></span>

<span data-ttu-id="00f8f-716">La aplicación llama a esta función para limpiar el bloque de control HMAC SHA1 después de determinar que esta sesión HMAC SHA1 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-717">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-717">Parameters</span></span>

- <span data-ttu-id="00f8f-718">**crypto_metadata** Puntero al bloque de control HMAC SHA1 utilizado en *_nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-719">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-719">Return Values</span></span>

- <span data-ttu-id="00f8f-720">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="00f8f-721">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="00f8f-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="00f8f-723">Inicializa el bloque de control criptográfico HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-724">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-725">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-725">Description</span></span>

<span data-ttu-id="00f8f-726">Esta función inicializa el bloque de control HMAC SHA256 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="00f8f-727">Una vez inicializado el bloque de control HMAC SHA256, la operación HMAC SHA256 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-728">La aplicación puede crear varios bloques de control HMAC SHA256, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-729">Al inicializar el bloque de control HMAC SH256, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-730">Al volver a inicializar el bloque de control HMAC SHA256, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-731">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-731">Parameters</span></span>

- <span data-ttu-id="00f8f-732">**method** Puntero a un bloque de control de método criptográfico HMAC SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="00f8f-733">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="00f8f-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="00f8f-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="00f8f-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="00f8f-736">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-736">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-737">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-738">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-739">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-740">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-741">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-742">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="00f8f-743">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-744">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-745">Con HMAC SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="00f8f-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-746">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-746">Return Values</span></span>

- <span data-ttu-id="00f8f-747">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA256 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-748">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-749">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="00f8f-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="00f8f-751">Realiza una operación hash de HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-752">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-752">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-753">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-753">Description</span></span>

<span data-ttu-id="00f8f-754">Esta función realiza una operación hash de HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="00f8f-755">El bloque de control HMAC SHA256 se debe haber inicializado con *nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="00f8f-756">El algoritmo HMAC SHA256 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-757">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 32 bytes para SHA256 o de 28 bytes para SHA224.</span><span class="sxs-lookup"><span data-stu-id="00f8f-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-758">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-758">Parameters</span></span>

- <span data-ttu-id="00f8f-759">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-760">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-760">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-764">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-765">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-766">**method** Puntero al método criptográfico HMAC SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="00f8f-767">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="00f8f-768">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-768">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-769">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-770">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-771">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-772">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-773">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-774">**iv_ptr** Este campo no se usa con HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="00f8f-775">**iv_ptr** Este campo no se usa con HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="00f8f-776">**output_buffer** Puntero al área de memoria para el hash de HMAC SHA256 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="00f8f-777">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-778">**crypto_metadata** Puntero al bloque de control HMAC SHA256 utilizado en *_nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="00f8f-779">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-780">Con HMAC SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="00f8f-781">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-782">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-783">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-784">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-785">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-785">Return Values</span></span>

- <span data-ttu-id="00f8f-786">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="00f8f-787">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-788">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA256 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="00f8f-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="00f8f-792">Limpia el bloque de control HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-793">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-794">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-794">Description</span></span>

<span data-ttu-id="00f8f-795">La aplicación llama a esta función para limpiar el bloque de control HMAC SHA256 después de determinar que esta sesión HMAC SHA256 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-796">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-796">Parameters</span></span>

- <span data-ttu-id="00f8f-797">**crypto_metadata** Puntero al bloque de control HMAC SHA256 utilizado en *_nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-798">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-798">Return Values</span></span>

- <span data-ttu-id="00f8f-799">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="00f8f-800">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="00f8f-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="00f8f-802">Inicializa el bloque de control criptográfico HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-803">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-804">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-804">Description</span></span>

<span data-ttu-id="00f8f-805">Esta función inicializa el bloque de control HMAC SHA512 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="00f8f-806">Una vez inicializado el bloque de control HMAC SHA512, la operación HMAC SHA512 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-807">La aplicación puede crear varios bloques de control HMAC SHA512, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-808">Al inicializar el bloque de control HMAC SH512, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-809">Al volver a inicializar el bloque de control HMAC SHA512, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-810">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-810">Parameters</span></span>

- <span data-ttu-id="00f8f-811">**method** Puntero a un bloque de control de método criptográfico HMAC SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="00f8f-812">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="00f8f-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="00f8f-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="00f8f-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="00f8f-815">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-815">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-816">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-817">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-818">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-819">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-820">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-821">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="00f8f-822">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-823">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-824">Con HMAC SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-825">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-825">Return Values</span></span>

- <span data-ttu-id="00f8f-826">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control HMAC SHA512 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-827">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-828">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="00f8f-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="00f8f-830">Realiza una operación hash de HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-831">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-831">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-832">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-832">Description</span></span>

<span data-ttu-id="00f8f-833">Esta función realiza una operación hash de HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="00f8f-834">El bloque de control HMAC SHA512 se debe haber inicializado con *nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="00f8f-835">El algoritmo HMAC SHA512 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-836">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 64 bytes para SHA512 o de 48 bytes para SHA384.</span><span class="sxs-lookup"><span data-stu-id="00f8f-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-837">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-837">Parameters</span></span>

- <span data-ttu-id="00f8f-838">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-839">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-839">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-843">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-844">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-845">**method** Puntero al método criptográfico HMAC SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="00f8f-846">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="00f8f-847">**key** Apunta a la clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-847">**key** Points to the key.</span></span> <span data-ttu-id="00f8f-848">No hay restricciones en el búfer de claves.</span><span class="sxs-lookup"><span data-stu-id="00f8f-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="00f8f-849">**key_size_in_bits** Tamaño de la clave, en bits.</span><span class="sxs-lookup"><span data-stu-id="00f8f-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="00f8f-850">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-851">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-852">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-853">**iv_ptr** Este campo no se usa con HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="00f8f-854">**iv_ptr** Este campo no se usa con HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="00f8f-855">**output_buffer** Puntero al área de memoria para el hash de HMAC SHA512 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="00f8f-856">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="00f8f-857">**crypto_metadata** Puntero al bloque de control HMAC SHA512 utilizado en *_nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="00f8f-858">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-859">Con HMAC SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="00f8f-860">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-861">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-862">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-863">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-864">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-864">Return Values</span></span>

- <span data-ttu-id="00f8f-865">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="00f8f-866">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-867">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo HMAC SHA512 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="00f8f-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="00f8f-871">Limpia el bloque de control HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-872">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-873">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-873">Description</span></span>

<span data-ttu-id="00f8f-874">La aplicación llama a esta función para limpiar el bloque de control HMAC SHA512 después de determinar que esta sesión HMAC SHA512 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-875">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-875">Parameters</span></span>

- <span data-ttu-id="00f8f-876">**crypto_metadata** Puntero al bloque de control HMAC SHA512 utilizado en *_nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-877">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-877">Return Values</span></span>

- <span data-ttu-id="00f8f-878">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="00f8f-879">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="00f8f-880">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="00f8f-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="00f8f-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="00f8f-882">Inicializa el bloque de control criptográfico MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-883">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-884">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-884">Description</span></span>

<span data-ttu-id="00f8f-885">Esta función inicializa el bloque de control MD5 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="00f8f-886">Una vez inicializado el bloque de control MD5, la operación MD5 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-887">La aplicación puede crear varios bloques de control MD5; cada uno representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-888">Al inicializar el bloque de control MD5, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-889">Al volver a inicializar el bloque de control MD5, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-890">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-890">Parameters</span></span>

- <span data-ttu-id="00f8f-891">**method** Puntero a un bloque de control de método criptográfico MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="00f8f-892">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="00f8f-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="00f8f-894">**key** Este campo no se usa con MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="00f8f-895">**key_size_in_bits** Este campo no se usa con MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="00f8f-896">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-897">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-898">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-899">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="00f8f-900">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-901">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-902">Con MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-903">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-903">Return Values</span></span>

- <span data-ttu-id="00f8f-904">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control MD5 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-905">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-906">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="00f8f-907">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="00f8f-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="00f8f-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="00f8f-909">Realiza una operación hash de MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-910">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-910">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-911">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-911">Description</span></span>

<span data-ttu-id="00f8f-912">Esta función realiza una operación hash de MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="00f8f-913">El bloque de control MD5 debe haberse inicializado con *nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="00f8f-914">El algoritmo MD5 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-915">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="00f8f-916">Esta operación no conserva la información de estado y no modifica el material de clave en el bloque de control MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-917">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-917">Parameters</span></span>

- <span data-ttu-id="00f8f-918">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-919">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-919">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-923">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-924">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-925">**method** Puntero al método criptográfico MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="00f8f-926">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="00f8f-927">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-928">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-929">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-930">**iv_ptr** Este campo no se utiliza con MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="00f8f-931">**iv_ptr** Este campo no se utiliza con MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="00f8f-932">**output_buffer** Puntero al área de memoria para el hash de MD5 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="00f8f-933">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-934">Con MD5, el tamaño del búfer debe ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="00f8f-935">**crypto_metadata** Puntero al bloque de control MD5 utilizado en *_nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="00f8f-936">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-937">Con MD5, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_MD5)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="00f8f-938">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-939">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-940">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-941">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-942">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-942">Return Values</span></span>

- <span data-ttu-id="00f8f-943">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="00f8f-944">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-945">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se ha especificado un algoritmo MD5 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="00f8f-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="00f8f-949">Limpia el bloque de control MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-950">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-951">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-951">Description</span></span>

<span data-ttu-id="00f8f-952">La aplicación llama a esta función para limpiar el bloque de control MD5 después de determinar que esta sesión MD5 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-953">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-953">Parameters</span></span>

- <span data-ttu-id="00f8f-954">**crypto_metadata** Puntero al bloque de control MD5 utilizado en *_nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-955">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-955">Return Values</span></span>

- <span data-ttu-id="00f8f-956">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión MD5.</span><span class="sxs-lookup"><span data-stu-id="00f8f-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="00f8f-957">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="00f8f-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="00f8f-959">Inicializa el bloque de control criptográfico SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-960">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-961">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-961">Description</span></span>

<span data-ttu-id="00f8f-962">Esta función inicializa el bloque de control SHA1 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="00f8f-963">Una vez inicializado el bloque de control SHA1, la operación SHA1 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-964">La aplicación puede crear varios bloques de control SHA1, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-965">Al inicializar el bloque de control SHA1, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-966">Al volver a inicializar el bloque de control SHA1, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-967">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-967">Parameters</span></span>

- <span data-ttu-id="00f8f-968">**method** Puntero a un bloque de control de método criptográfico SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="00f8f-969">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="00f8f-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="00f8f-971">**key** Este campo no se usa con SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="00f8f-972">**key_size_in_bits** Este campo no se usa con SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="00f8f-973">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-974">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-975">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-976">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="00f8f-977">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-978">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-979">Con SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-980">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-980">Return Values</span></span>

- <span data-ttu-id="00f8f-981">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA1 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-982">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-983">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="00f8f-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="00f8f-985">Realiza una operación hash de SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-986">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-986">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-987">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-987">Description</span></span>

<span data-ttu-id="00f8f-988">Esta función realiza una operación hash de SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="00f8f-989">El bloque de control SHA1 se debe haber inicializado con *nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="00f8f-990">El algoritmo SHA1 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-991">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-992">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-992">Parameters</span></span>

- <span data-ttu-id="00f8f-993">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-994">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-994">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-998">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-999">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1000">**method** Puntero al método criptográfico SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="00f8f-1001">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="00f8f-1002">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-1003">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-1004">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-1005">**iv_ptr** Este campo no se utiliza con SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="00f8f-1006">**iv_ptr** Este campo no se utiliza con SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="00f8f-1007">**output_buffer** Puntero al área de memoria para el hash de SHA1 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="00f8f-1008">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-1009">Con SHA1, el tamaño del búfer debe ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="00f8f-1010">**crypto_metadata** Puntero al bloque de control SHA1 utilizado en *_nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="00f8f-1011">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-1012">Con SHA1, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA1)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="00f8f-1013">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1014">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1015">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1016">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1017">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1017">Return Values</span></span>

- <span data-ttu-id="00f8f-1018">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="00f8f-1019">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-1020">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA1 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="00f8f-1023">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="00f8f-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="00f8f-1025">Limpia el bloque de control SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1026">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-1027">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1027">Description</span></span>

<span data-ttu-id="00f8f-1028">La aplicación llama a esta función para limpiar el bloque de control SHA1 después de determinar que esta sesión SHA1 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1029">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1029">Parameters</span></span>

- <span data-ttu-id="00f8f-1030">**crypto_metadata** Puntero al bloque de control SHA1 utilizado en *_nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1031">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1031">Return Values</span></span>

- <span data-ttu-id="00f8f-1032">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA1.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="00f8f-1033">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="00f8f-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="00f8f-1035">Inicializa el bloque de control criptográfico SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1036">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="00f8f-1037">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1037">Description</span></span>

<span data-ttu-id="00f8f-1038">Esta función inicializa el bloque de control SHA256 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="00f8f-1039">Una vez inicializado el bloque de control SHA256, la operación SHA256 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-1040">La aplicación puede crear varios bloques de control SHA256, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-1041">Al inicializar el bloque de control SHA256, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-1042">Al volver a inicializar el bloque de control SHA256, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1043">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1043">Parameters</span></span>

- <span data-ttu-id="00f8f-1044">**method** Puntero a un bloque de control de método criptográfico SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="00f8f-1045">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="00f8f-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="00f8f-1048">**key** Este campo no se usa con SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="00f8f-1049">**key_size_in_bits** Este campo no se usa con SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="00f8f-1050">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-1051">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-1052">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-1053">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="00f8f-1054">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-1055">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-1056">Con SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1057">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1057">Return Values</span></span>

- <span data-ttu-id="00f8f-1058">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA256 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-1059">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-1060">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="00f8f-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="00f8f-1062">Realiza una operación hash de SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1063">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1063">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-1064">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1064">Description</span></span>

<span data-ttu-id="00f8f-1065">Esta función realiza una operación hash de SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="00f8f-1066">El bloque de control SHA256 se debe haber inicializado con ***nx_crypto_method_sha256_init()***.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="00f8f-1067">El algoritmo SHA256 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-1068">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 32 bytes para SHA256 o de 28 bytes para SHA224.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1069">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1069">Parameters</span></span>

- <span data-ttu-id="00f8f-1070">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-1071">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-1071">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-1075">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1076">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1077">**method** Puntero al método criptográfico SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="00f8f-1078">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="00f8f-1079">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-1080">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-1081">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-1082">**iv_ptr** Este campo no se utiliza con SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="00f8f-1083">**iv_ptr** Este campo no se utiliza con SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="00f8f-1084">**output_buffer** Puntero al área de memoria para el hash de SHA256 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="00f8f-1085">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-1086">Con SHA256, el tamaño del búfer debe ser de 32 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="00f8f-1087">Con SHA224, el tamaño del búfer debe ser de 28 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="00f8f-1088">**crypto_metadata** Puntero al bloque de control SHA2 utilizado en *_nx_crypto_method_sha2_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="00f8f-1089">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-1090">Con SHA256, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA256)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="00f8f-1091">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1092">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1093">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1094">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1095">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1095">Return Values</span></span>

- <span data-ttu-id="00f8f-1096">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="00f8f-1097">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-1098">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA256 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="00f8f-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="00f8f-1102">Limpia el bloque de control SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1103">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-1104">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1104">Description</span></span>

<span data-ttu-id="00f8f-1105">La aplicación llama a esta función para limpiar el bloque de control SHA256 después de determinar que esta sesión SHA256 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1106">Parameters</span></span>

- <span data-ttu-id="00f8f-1107">**crypto_metadata** Puntero al bloque de control SHA256 utilizado en *_nx_crypto_method_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1108">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1108">Return Values</span></span>

- <span data-ttu-id="00f8f-1109">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA256.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="00f8f-1110">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="00f8f-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="00f8f-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="00f8f-1112">Inicializa el bloque de control criptográfico SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1113">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="00f8f-1114">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1114">Description</span></span>

<span data-ttu-id="00f8f-1115">Esta función inicializa el bloque de control SHA512 con la cadena de clave especificada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="00f8f-1116">Una vez inicializado el bloque de control SHA512, la operación SHA512 posterior usará el mismo bloque de control.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="00f8f-1117">La aplicación puede crear varios bloques de control SHA512, cada uno de los cuales representa una sesión.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="00f8f-1118">Al inicializar el bloque de control SHA512, se inicia una nueva sesión de cálculo de hash.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="00f8f-1119">Al volver a inicializar el bloque de control SHA512, se abandona la sesión actual y se inicia una nueva.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1120">Parameters</span></span>

- <span data-ttu-id="00f8f-1121">**method** Puntero a un bloque de control de método criptográfico SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="00f8f-1122">Están disponibles los siguientes métodos criptográficos predefinidos:</span><span class="sxs-lookup"><span data-stu-id="00f8f-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="00f8f-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="00f8f-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="00f8f-1125">**key** Este campo no se usa con SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="00f8f-1126">**key_size_in_bits** Este campo no se usa con SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="00f8f-1127">**handle** Este servicio devuelve un identificador al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="00f8f-1128">El identificador depende de la implementación y no se utiliza en esta implementación.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="00f8f-1129">La aplicación pasará NULL como valor del identificador.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="00f8f-1130">**crypto_metadata** Puntero a un espacio de memoria válido para el bloque de control SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="00f8f-1131">La dirección inicial del espacio de memoria debe estar alineada en 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="00f8f-1132">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-1133">Con SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1134">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1134">Return Values</span></span>

- <span data-ttu-id="00f8f-1135">**NX_CRYPTO_SUCCESS** (0x00) Inicialización correcta del bloque de control SHA512 con la clave y el tamaño de clave.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="00f8f-1136">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-1137">**NX_PTR_ERROR (0x07)** Puntero no válido a la clave, o crypto_metadata o crypto_metadata_size no válidos, o crypto_metadata no tiene una alineación de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="00f8f-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="00f8f-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="00f8f-1139">Realiza una operación hash de SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1140">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="00f8f-1141">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1141">Description</span></span>

<span data-ttu-id="00f8f-1142">Esta función realiza una operación hash de SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="00f8f-1143">El bloque de control SHA512 se debe haber inicializado con *nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="00f8f-1144">El algoritmo SHA512 que se va a ejecutar se basa en el algoritmo especificado en el bloque de control *method*.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="00f8f-1145">Con la operación *NX_CRYPTO_HASH_CALCULATE* final, el tamaño del búfer de salida debe ser de 64 bytes para SHA512 o de 48 bytes para SHA384.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1146">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1146">Parameters</span></span>

- <span data-ttu-id="00f8f-1147">**op** Tipo de operación que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="00f8f-1148">La operación válida es:</span><span class="sxs-lookup"><span data-stu-id="00f8f-1148">Valid operation is:</span></span>
  - <span data-ttu-id="00f8f-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="00f8f-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="00f8f-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="00f8f-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="00f8f-1152">**handle** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1153">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1154">**method** Puntero al método criptográfico SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="00f8f-1155">El método criptográfico que se usa aquí debe ser el mismo que se usa en *nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="00f8f-1156">**input_data** Apunta a un búfer que contiene datos de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="00f8f-1157">No hay restricciones en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="00f8f-1158">**input_data_size** Tamaño de los datos de entrada, en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="00f8f-1159">**iv_ptr** Este campo no se utiliza con SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="00f8f-1160">**iv_ptr** Este campo no se utiliza con SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="00f8f-1161">**output_buffer** Puntero al área de memoria para el hash de SHA512 generado.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="00f8f-1162">**output_buffer_size** Tamaño del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="00f8f-1163">Con SHA512, el tamaño del búfer debe ser de 64 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="00f8f-1164">Con SHA384, el tamaño del búfer debe ser de 48 bytes.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="00f8f-1165">**crypto_metadata** Puntero al bloque de control SHA512 utilizado en *_nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="00f8f-1166">**crypto_metadata_size** Tamaño, en bytes, del área crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="00f8f-1167">Con SHA512, el tamaño de los metadatos debe ser *sizeof(NX_CRYPTO_SHA512_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="00f8f-1168">**packet_ptr** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1169">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="00f8f-1170">**nx_crypto_hw_process_callback** Este campo no se usa en la implementación de software de la biblioteca de NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="00f8f-1171">Los valores pasados se omiten de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1172">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1172">Return Values</span></span>

- <span data-ttu-id="00f8f-1173">**NX_CRYPTO_SUCCESS** (0x00) Se ha ejecutado correctamente la operación SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="00f8f-1174">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="00f8f-1175">**NX_PTR_ERROR** (0x07) Puntero de entrada o longitud no válidos.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="00f8f-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Se está especificando un algoritmo SHA512 no válido.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="00f8f-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamaño no válido del búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="00f8f-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="00f8f-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="00f8f-1179">Limpia el bloque de control SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="00f8f-1180">Prototipo</span><span class="sxs-lookup"><span data-stu-id="00f8f-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="00f8f-1181">Descripción</span><span class="sxs-lookup"><span data-stu-id="00f8f-1181">Description</span></span>

<span data-ttu-id="00f8f-1182">La aplicación llama a esta función para limpiar el bloque de control SHA512 después de determinar que esta sesión SHA512 ya no se necesita.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="00f8f-1183">Parámetros</span><span class="sxs-lookup"><span data-stu-id="00f8f-1183">Parameters</span></span>

- <span data-ttu-id="00f8f-1184">**crypto_metadata** Puntero al bloque de control SHA512 utilizado en *_nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="00f8f-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="00f8f-1185">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="00f8f-1185">Return Values</span></span>

- <span data-ttu-id="00f8f-1186">**NX_CRYPTO_SUCCESS** (0x00) Se ha limpiado correctamente la sesión SHA512.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="00f8f-1187">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) La biblioteca de criptografía se encuentra en un estado no válido y no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="00f8f-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>