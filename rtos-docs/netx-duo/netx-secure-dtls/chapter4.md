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
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="936d8-103">Capítulo 4: Descripción de los servicios Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="936d8-104">Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX Secure DTLS (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="936d8-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="936d8-105">En la sección "Valores devueltos" de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por el macro **NX_SECURE_DISABLE_ERROR_CHECKING** que se usan para deshabilitar la comprobación de errores de la API, mientras que los valores que no aparecen en negrita están totalmente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="936d8-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="936d8-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="936d8-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="936d8-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="936d8-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="936d8-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="936d8-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="936d8-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="936d8-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="936d8-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="936d8-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="936d8-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="936d8-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="936d8-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="936d8-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="936d8-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="936d8-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="936d8-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="936d8-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="936d8-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="936d8-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="936d8-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="936d8-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="936d8-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="936d8-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="936d8-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="936d8-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="936d8-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="936d8-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="936d8-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="936d8-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="936d8-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="936d8-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="936d8-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="936d8-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="936d8-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="936d8-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="936d8-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="936d8-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="936d8-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="936d8-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="936d8-131">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="936d8-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="936d8-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="936d8-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="936d8-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="936d8-135">Iniciar una sesión de cliente de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-136">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="936d8-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-137">Description</span></span>

<span data-ttu-id="936d8-138">Este servicio inicia una sesión de cliente DTLS, que se conecta al servidor en la dirección IP y el puerto UDP proporcionados mediante el socket UDP proporcionado para las comunicaciones de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="936d8-139">El bloque de control de sesión DTLS debe inicializarse antes de llamar a este servicio mediante nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="936d8-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="936d8-140">Además, el cliente DTLS necesita que se haya agregado al menos un certificado de entidad de certificación de confianza a la sesión mediante nx_secure_dtls_session_trusted_certificate_add o que las claves precompartidas estén habilitadas y configuradas.</span><span class="sxs-lookup"><span data-stu-id="936d8-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-141">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-141">Parameters</span></span>

- <span data-ttu-id="936d8-142">**dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="936d8-143">**udp_socket** Socket UDP inicializado que se usará para establecer comunicaciones de red con el servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="936d8-144">**ip_address** Puntero a la estructura de la dirección IP que contiene la dirección del servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="936d8-145">**port** Socket UDP inicializado que se usará para establecer comunicaciones de red con el servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="936d8-146">**wait_option** Opción de suspensión para el intento de conexión.</span><span class="sxs-lookup"><span data-stu-id="936d8-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-147">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-147">Return Values</span></span>

- <span data-ttu-id="936d8-148">**NX_SUCCESS** (0x00) Asignación correcta del certificado a la sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="936d8-149">**NX_NOT_CONNECTED** (0x38) No se puede tener acceso al servidor en la dirección y el puerto especificados.</span><span class="sxs-lookup"><span data-stu-id="936d8-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="936d8-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Un tipo de mensaje TLS/DTLS recibido es incorrecto.</span><span class="sxs-lookup"><span data-stu-id="936d8-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="936d8-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) No se admite el cifrado proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="936d8-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Procesamiento del mensaje durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="936d8-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un mensaje entrante no pudo realizar una comprobación de MAC hash.</span><span class="sxs-lookup"><span data-stu-id="936d8-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="936d8-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error al enviar un socket TCP subyacente.</span><span class="sxs-lookup"><span data-stu-id="936d8-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="936d8-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Un mensaje entrante tenía un campo de longitud no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="936d8-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) Un mensaje ChangeCipherSpec entrante era incorrecto.</span><span class="sxs-lookup"><span data-stu-id="936d8-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="936d8-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="936d8-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="936d8-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) El host remoto ha indicado que no hay conjuntos de aplicaciones de cifrado admitidos por la pila de NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="936d8-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) Un mensaje DTLS recibido tenía una versión DTLS desconocida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="936d8-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="936d8-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) Un mensaje DTLS recibido tenía una versión de DTLS conocida pero no admitida en su encabezado.</span><span class="sxs-lookup"><span data-stu-id="936d8-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="936d8-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Error en una asignación interna de paquetes TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="936d8-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) El host remoto proporcionó un certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="936d8-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="936d8-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Una entrada en la tabla de conjunto de aplicaciones de cifrado tenía un puntero de función NULL.</span><span class="sxs-lookup"><span data-stu-id="936d8-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="936d8-166">**NX_PTR_ERROR** (0x07): La sesión, el socket o el puntero de dirección no son válidos.</span><span class="sxs-lookup"><span data-stu-id="936d8-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-167">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-167">Allowed From</span></span>

<span data-ttu-id="936d8-168">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-169">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-170">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-170">See Also</span></span>

- <span data-ttu-id="936d8-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="936d8-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="936d8-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="936d8-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="936d8-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="936d8-174">Asignación de un paquete para una sesión de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-175">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="936d8-176">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-176">Description</span></span>

<span data-ttu-id="936d8-177">Este servicio asigna un NX_PACKET para la sesión DTLS activa especificada desde el NX_PACKET_POOL especificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="936d8-178">La aplicación debe llamar a este servicio para asignar paquetes de datos que se enviarán a través de una conexión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="936d8-179">La sesión DTLS debe inicializarse antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="936d8-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="936d8-180">El paquete asignado se ha inicializado correctamente para que se puedan agregar datos de encabezado y pie de página de DTLS una vez que se hayan rellenado los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="936d8-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="936d8-181">De lo contrario, el comportamiento es idéntico al de *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="936d8-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-182">Parameters</span></span>

- <span data-ttu-id="936d8-183">**session_ptr** Puntero a una instancia de sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-184">**pool_ptr** Puntero a un NX_PACKET_POOL desde el que se va a asignar el paquete.</span><span class="sxs-lookup"><span data-stu-id="936d8-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="936d8-185">**packet_ptr** Puntero de salida al paquete recién asignado.</span><span class="sxs-lookup"><span data-stu-id="936d8-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="936d8-186">**wait_option** Opción de suspensión para la asignación de paquetes.</span><span class="sxs-lookup"><span data-stu-id="936d8-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="936d8-187">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-187">Return Values</span></span>

- <span data-ttu-id="936d8-188">**NX_SUCCESS** (0x00) Asignación correcta de paquetes.</span><span class="sxs-lookup"><span data-stu-id="936d8-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="936d8-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Error al asignar el paquete subyacente.</span><span class="sxs-lookup"><span data-stu-id="936d8-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="936d8-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) No se inicializó la sesión DTLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="936d8-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-191">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-191">Allowed From</span></span>

<span data-ttu-id="936d8-192">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-193">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="936d8-194">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-194">See Also</span></span>

- <span data-ttu-id="936d8-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="936d8-196">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="936d8-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="936d8-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="936d8-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="936d8-200">Incorporación de una clave precompartida a una sesión de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-201">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="936d8-202">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-202">Description</span></span>

<span data-ttu-id="936d8-203">Este servicio agrega una clave precompartida (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="936d8-204">La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de aplicaciones de cifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-205">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-205">Parameters</span></span>

- <span data-ttu-id="936d8-206">**session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-207">**pre_shared_key** Valor de PSK real.</span><span class="sxs-lookup"><span data-stu-id="936d8-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="936d8-208">**psk_length** Longitud del valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="936d8-209">**psk_identity** Cadena que se usa para identificar este valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="936d8-210">**identity_length** La longitud de la identidad de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="936d8-211">**hint** Cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="936d8-212">**hint_length** Longitud de la cadena de sugerencia.</span><span class="sxs-lookup"><span data-stu-id="936d8-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-213">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-213">Return Values</span></span>

- <span data-ttu-id="936d8-214">**NX_SUCCESS** (0x00) PSK añadida correctamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="936d8-215">**NX_PTR_ERROR** (0x07) Puntero de sesión DTLS no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="936d8-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) No se puede agregar otra PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-217">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-217">Allowed From</span></span>

<span data-ttu-id="936d8-218">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-219">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="936d8-220">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-220">See Also</span></span>

- <span data-ttu-id="936d8-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="936d8-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="936d8-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="936d8-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="936d8-223">Creación de un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-224">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-224">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="936d8-225">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-225">Description</span></span>

<span data-ttu-id="936d8-226">Este servicio crea una instancia de un servidor DTLS para administrar las solicitudes DTLS entrantes en un puerto UDP determinado.</span><span class="sxs-lookup"><span data-stu-id="936d8-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="936d8-227">Debido al hecho de que UDP no tiene estado, las solicitudes de DTLS de varios clientes pueden entrar en un único puerto mientras que otras sesiones DTLS están activas.</span><span class="sxs-lookup"><span data-stu-id="936d8-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="936d8-228">Por lo tanto, se necesita el servidor para mantener las sesiones activas y enrutar correctamente los mensajes entrantes al controlador adecuado.</span><span class="sxs-lookup"><span data-stu-id="936d8-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="936d8-229">El parámetro ip_ptr apunta a una instancia NX_IP que se va a usar para el socket UDP interno asociado con el servidor DTLS (y se almacena en el bloque de control NX_SECURE_DTLS_SERVER).</span><span class="sxs-lookup"><span data-stu-id="936d8-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="936d8-230">La instancia de IP y el puerto se usan para definir la interfaz de UDP en la que se crea una instancia del servidor con el servicio de nx_secure_dtls_server_start.</span><span class="sxs-lookup"><span data-stu-id="936d8-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="936d8-231">El parámetro de búfer de la sesión se usa para mantener los bloques de control para todas las sesiones DTLS simultáneas posibles para el servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="936d8-232">Debe asignarse con un tamaño que sea un múltiplo par del tamaño de la estructura del bloque de control NX_SECURE_DTLS_SESSION.</span><span class="sxs-lookup"><span data-stu-id="936d8-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="936d8-233">Para calcular el tamaño de metadatos necesario, se puede usar la API nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="936d8-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="936d8-234">DTLS usa el parámetro packet_reassembly_buffer para volver a ensamblar los datagramas UDP en un registro DTLS completo con el fin de descifrar y debe ser lo suficientemente grande como para acomodar el mayor registro DTLS esperado (16 KB es el tamaño máximo de registro de DTLS, pero muchas aplicaciones no envían esa cantidad de datos en un único registro).</span><span class="sxs-lookup"><span data-stu-id="936d8-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="936d8-235">La rutina de devolución de llamada connect_notify se invoca siempre que un nuevo cliente DTLS se conecta al servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="936d8-236">Depende de la aplicación iniciar después la sesión DTLS mediante el servicio *nx_secure_dtls_server_session_start*.</span><span class="sxs-lookup"><span data-stu-id="936d8-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="936d8-237">Aunque la sesión puede iniciarse en la devolución de llamada, se recomienda usar la devolución de llamada para notificar al subproceso de la aplicación (o al subproceso DTLS dedicado creado por la aplicación) de la conexión, ya que el subproceso IP invoca la devolución de llamada, que se usa para procesar todo el procesamiento de red de nivel inferior (por ejemplo, UDP).</span><span class="sxs-lookup"><span data-stu-id="936d8-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="936d8-238">Esto puede ser tan sencillo como guardar el parámetro de sesión DTLS (proporcionado como parámetro para la devolución de llamada) e invocar nx_secure_dtls_server_session_start en el otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="936d8-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="936d8-239">Por lo general, la devolución de llamada de connect_notify debería devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="936d8-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="936d8-240">La rutina de devolución de llamada de receive_notify se invoca cada vez que se recibe un registro DTLS que coincide con una sesión DTLS establecida existente (el puerto y la dirección IP del host remoto se usan para identificar una sesión existente).</span><span class="sxs-lookup"><span data-stu-id="936d8-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="936d8-241">Representa los "datos de aplicación" que se cifran y se envían a través de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="936d8-242">La aplicación debe llamar al servicio *nx_secure_dtls_session_receive* en la sesión DTLS proporcionada para recuperar los datos recibidos.</span><span class="sxs-lookup"><span data-stu-id="936d8-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="936d8-243">Al igual que con la devolución de llamada de connect_receive, se recomienda pasar la sesión a otro subproceso para controlar el procesamiento de mensajes, ya que la devolución de llamada se invoca desde el subproceso IP.</span><span class="sxs-lookup"><span data-stu-id="936d8-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="936d8-244">Por lo general, la devolución de llamada de connect_notify debería devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="936d8-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-245">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-245">Parameters</span></span>

- <span data-ttu-id="936d8-246">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-247">**ip_ptr** Puntero a un bloque de control NX_IP inicializado para usarlo como interfaz de red para el servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="936d8-248">**port** Puerto UDP local al que está enlazado el socket UDP del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="936d8-249">**timeout** Valor de tiempo de espera que se va a usar para las operaciones de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="936d8-250">**session_buffer** Espacio en búfer para contener los bloques de control de todas las instancias de NX_SECURE_DTLS_SESSION asignadas a esta instancia del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-251">**session_buffer_size** Tamaño del búfer de la sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="936d8-252">Esto determina el número de sesiones DTLS asignadas al servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="936d8-253">**crypto_table** Puntero a una estructura de tabla de cifrado TLS/DTLS usada para todas las operaciones criptográficas.</span><span class="sxs-lookup"><span data-stu-id="936d8-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="936d8-254">**crypto_metadata_buffer** Espacio en búfer para cálculos de operaciones criptográficas e información de estado.</span><span class="sxs-lookup"><span data-stu-id="936d8-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="936d8-255">**crypto_metadata_size** Tamaño del búfer de metadatos.</span><span class="sxs-lookup"><span data-stu-id="936d8-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="936d8-256">**packet_reassembly_buffer** Búfer usado por DTLS para volver a ensamblar los datos de UDP en los registros de DTLS para el descifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="936d8-257">**packet_reassembly_buffer_size** Tamaño del búfer de reensamblado.</span><span class="sxs-lookup"><span data-stu-id="936d8-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="936d8-258">Por lo general, debe ser mayor que 16 KB, pero puede ser menor en función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="936d8-259">**connect_notify** Rutina de devolución de llamada que se invoca cada vez que un cliente DTLS remoto trata de conectarse a este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="936d8-260">**receive_notify** Devolución de llamada invocada cuando se reciben datos de la aplicación a través de una sesión DTLS existente.</span><span class="sxs-lookup"><span data-stu-id="936d8-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-261">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-261">Return Values</span></span>

- <span data-ttu-id="936d8-262">**NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="936d8-263">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-264">**NX_INVALID_PARAMETERS** (0X4D) No hay suficiente espacio de búfer para las sesiones, el reensamblado de paquetes o la criptografía.</span><span class="sxs-lookup"><span data-stu-id="936d8-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-265">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-265">Allowed From</span></span>

<span data-ttu-id="936d8-266">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-267">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-267">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-268">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-268">See Also</span></span>

- <span data-ttu-id="936d8-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="936d8-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="936d8-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-271">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-272">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="936d8-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="936d8-275">Liberación de recursos usados por un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-276">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="936d8-277">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-277">Description</span></span>

<span data-ttu-id="936d8-278">Este servicio libera los recursos asignados a una instancia del servidor DTLS, incluido el socket UDP interno usado por el servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-279">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-279">Parameters</span></span>

- <span data-ttu-id="936d8-280">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-281">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-281">Return Values</span></span>

- <span data-ttu-id="936d8-282">**NX_SUCCESS** (0x00) Eliminación correcta del servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="936d8-283">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-284">**NX_STILL_BOUND** (0x42) El socket UDP sigue estando enlazado.</span><span class="sxs-lookup"><span data-stu-id="936d8-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-285">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-285">Allowed From</span></span>

<span data-ttu-id="936d8-286">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-287">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-287">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-288">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-288">See Also</span></span>

- <span data-ttu-id="936d8-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="936d8-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="936d8-293">Adición de un certificado de identidad de servidor local a un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-294">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-295">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-295">Description</span></span>

<span data-ttu-id="936d8-296">Este servicio agrega un certificado de identidad de servidor local a una instancia del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="936d8-297">Se necesita al menos un certificado de identidad para que los clientes se conecten a un servidor DTLS a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas).</span><span class="sxs-lookup"><span data-stu-id="936d8-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="936d8-298">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-299">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presente en el almacén de servidores DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="936d8-300">Para obtener más información sobre los certificados de servidor X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-301">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-301">Parameters</span></span>

- <span data-ttu-id="936d8-302">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-303">**certificate** Puntero a una estructura de certificados X.509 inicializada previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="936d8-304">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-305">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-305">Return Values</span></span>

- <span data-ttu-id="936d8-306">**NX_SUCCESS** (0x00) Adición correcta del certificado al servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="936d8-307">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-308">**NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-309">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-309">Allowed From</span></span>

<span data-ttu-id="936d8-310">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-311">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-311">Example</span></span>

<span data-ttu-id="936d8-312">\* Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-313">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-313">See Also</span></span>

- <span data-ttu-id="936d8-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-316">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-317">nx_secure_dtls_server_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="936d8-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="936d8-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="936d8-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="936d8-320">Eliminación de un certificado de identidad de servidor local de un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-321">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-322">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-322">Description</span></span>

<span data-ttu-id="936d8-323">Este servicio quita un certificado de identidad de servidor local de una instancia del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="936d8-324">Se necesita al menos un certificado de identidad para que los clientes se conecten a un servidor DTLS a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas).</span><span class="sxs-lookup"><span data-stu-id="936d8-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="936d8-325">El certificado que se va a quitar se puede identificar por su nombre común X.509 o por el cert_id numérico que se asignó en la llamada a *nx_secure_dtls_server_local_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="936d8-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="936d8-326">El cert_id solo se usa para identificar el certificado y lo mantiene la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="936d8-327">Si se usa el nombre común en lugar del identificador de certificado numérico, el parámetro cert_id debe establecerse en 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="936d8-328">Si se quita un certificado mientras se está procesando un protocolo de enlace DTLS, se producirá un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="936d8-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="936d8-329">Antes de quitar los certificados, se debe llamar al parámetro *nx_secure_dtls_server_stop* de servicio.</span><span class="sxs-lookup"><span data-stu-id="936d8-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-330">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-330">Parameters</span></span>

- <span data-ttu-id="936d8-331">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-332">**common_name** CommonName X.509 del certificado que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="936d8-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="936d8-333">Si se usa, envíe cert_id con valor cero.</span><span class="sxs-lookup"><span data-stu-id="936d8-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="936d8-334">**common_name_length** Longitud de la cadena common_name en bytes.</span><span class="sxs-lookup"><span data-stu-id="936d8-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="936d8-335">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="936d8-336">Si se usa, envíe NX_NULL para el parámetro common_name.</span><span class="sxs-lookup"><span data-stu-id="936d8-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-337">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-337">Return Values</span></span>

- <span data-ttu-id="936d8-338">**NX_SUCCESS** (0x00) Eliminación correcta del certificado del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="936d8-339">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en el servidor DTLS especificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-341">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-341">Allowed From</span></span>

<span data-ttu-id="936d8-342">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-343">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-343">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-344">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-344">See Also</span></span>

- <span data-ttu-id="936d8-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-346">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-347">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-348">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="936d8-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="936d8-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="936d8-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="936d8-351">Asignación de rutinas de devolución de llamada de notificación opcionales a un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-352">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="936d8-353">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-353">Description</span></span>

<span data-ttu-id="936d8-354">Este servicio se puede usar para agregar rutinas de devolución de llamada de notificación opcionales a un servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="936d8-355">Cualquier parámetro de devolución de llamada se puede enviar como NX_NULL si solo se quiere una devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="936d8-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="936d8-356">La devolución de llamada de disconnect_notify se invoca cuando un cliente remoto finaliza una sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="936d8-357">El parámetro dtls_session es la instancia de sesión que se cerró.</span><span class="sxs-lookup"><span data-stu-id="936d8-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="936d8-358">Por lo general, la devolución de llamada debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="936d8-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="936d8-359">La devolución de llamada de error_notify se invoca cada vez que se produce un error o un tiempo de espera de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="936d8-360">El parámetro dtls_session es la instancia de sesión para la que se produjo el error y error_code es el código de estado numérico para el error que provocó el problema (consulte el Apéndice A).</span><span class="sxs-lookup"><span data-stu-id="936d8-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="936d8-361">Códigos de retorno/error de Net Secure de la lista de códigos de error que se puede devolver.</span><span class="sxs-lookup"><span data-stu-id="936d8-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="936d8-362">Por lo general, la devolución de llamada debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="936d8-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-363">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-363">Parameters</span></span>

- <span data-ttu-id="936d8-364">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-365">**disconnect_notify** Rutina de devolución de llamada que se invoca siempre que un host de cliente remoto cierra una sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="936d8-366">**error_notify** Rutina de devolución de llamada que se invoca cuando DTLS encuentra un error o un tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="936d8-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-367">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-367">Return Values</span></span>

- <span data-ttu-id="936d8-368">**NX_SUCCESS** (0x00) Asignación correcta de rutinas de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="936d8-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="936d8-369">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-370">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-370">Allowed From</span></span>

<span data-ttu-id="936d8-371">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-372">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-372">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-373">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-373">See Also</span></span>

- <span data-ttu-id="936d8-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-375">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="936d8-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="936d8-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="936d8-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="936d8-378">Incorporación de una clave precompartida a un servidor de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-379">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="936d8-380">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-380">Description</span></span>

<span data-ttu-id="936d8-381">Este servicio agrega una clave precompartida (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="936d8-382">La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de aplicaciones de cifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="936d8-383">La PSK que se agrega se replica en todas las sesiones DTLS asignadas al servidor DTLS (a través del búfer de sesión proporcionado en la llamada a nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="936d8-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-384">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-384">Parameters</span></span>

- <span data-ttu-id="936d8-385">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-386">**pre_shared_key** Valor de PSK real.</span><span class="sxs-lookup"><span data-stu-id="936d8-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="936d8-387">**psk_length** Longitud del valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="936d8-388">**psk_identity** Cadena que se usa para identificar este valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="936d8-389">**identity_length** La longitud de la identidad de PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="936d8-390">**hint** Cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="936d8-391">**hint_length** Longitud de la cadena de sugerencia.</span><span class="sxs-lookup"><span data-stu-id="936d8-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-392">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-392">Return Values</span></span>

- <span data-ttu-id="936d8-393">**NX_SUCCESS** (0x00) PSK añadida correctamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="936d8-394">**NX_PTR_ERROR** (0x07) Puntero del servidor DTLS no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="936d8-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) No se puede agregar otra PSK.</span><span class="sxs-lookup"><span data-stu-id="936d8-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-396">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-396">Allowed From</span></span>

<span data-ttu-id="936d8-397">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-398">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="936d8-399">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-399">See Also</span></span>

- <span data-ttu-id="936d8-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="936d8-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="936d8-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="936d8-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="936d8-402">Envío de datos a través de una sesión DTLS establecida con un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-403">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="936d8-404">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-404">Description</span></span>

<span data-ttu-id="936d8-405">Este servicio envía un paquete de datos a través de una sesión de servidor DTLS establecida a un host del cliente DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="936d8-406">La sesión usada se obtiene en la rutina de devolución de llamada receive_notify proporcionada a nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="936d8-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="936d8-407">Los datos proporcionados en el paquete, que se deben asignar mediante *nx_secure_dtls_packet_allocate*, se cifran mediante los parámetros criptográficos y las rutinas de la sesión DTLS y, a continuación, se envían al host remoto a través del puerto UDP interno del servidor DTLS en la dirección IP y el puerto del cliente conectado (almacenados en la sesión DTLS).</span><span class="sxs-lookup"><span data-stu-id="936d8-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-408">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-408">Parameters</span></span>

- <span data-ttu-id="936d8-409">**session_ptr** Puntero a una instancia de sesión DTLS obtenida a partir de la rutina de devolución de llamada receive_notify proporcionada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="936d8-410">**packet_ptr** Puntero a una instancia NX_PACKET asignada previamente y rellenada con datos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-411">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-411">Return Values</span></span>

- <span data-ttu-id="936d8-412">**NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="936d8-413">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Se produjo un error en la operación de envío de UDP subyacente.</span><span class="sxs-lookup"><span data-stu-id="936d8-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-415">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-415">Allowed From</span></span>

<span data-ttu-id="936d8-416">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-417">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-417">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-418">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-418">See Also</span></span>

- <span data-ttu-id="936d8-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="936d8-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="936d8-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="936d8-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="936d8-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="936d8-424">Inicio de una sesión DTLS desde un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-425">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="936d8-426">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-426">Description</span></span>

<span data-ttu-id="936d8-427">Este servicio inicia una sesión del servidor DTLS mediante el protocolo de enlace DTLS del lado del servidor cuando un cliente DTLS remoto se ha conectado al servidor y ha pedido una conexión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="936d8-428">La sesión DTLS se obtiene en la rutina de devolución de llamada connect_notify proporcionada a nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="936d8-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-429">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-429">Parameters</span></span>

- <span data-ttu-id="936d8-430">**session_ptr** Puntero a una instancia de sesión DTLS obtenida de una devolución de llamada connect_notify del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="936d8-431">**wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-432">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-432">Return Values</span></span>

- <span data-ttu-id="936d8-433">**NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="936d8-434">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) No se pudo asignar un paquete de protocolo de enlace de DTLS (grupo de paquetes vacío).</span><span class="sxs-lookup"><span data-stu-id="936d8-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="936d8-436">**NX_SECURE_TLS_INVALID_PACKET** (0X104) Se han recibido datos que no eran un registro DTLS válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="936d8-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un registro DTLS no se pudo codificar correctamente (error de cifrado).</span><span class="sxs-lookup"><span data-stu-id="936d8-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="936d8-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Error al comprobar el relleno de cifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="936d8-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) Se ha recibido una alerta del host remoto durante el protocolo de enlace DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="936d8-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Se ha recibido un mensaje desconocido durante el protocolo de enlace DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="936d8-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) Se ha recibido un registro DTLS con una longitud no válida.</span><span class="sxs-lookup"><span data-stu-id="936d8-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="936d8-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) Se ha recibido un ClientHello sin conjuntos de aplicaciones de cifrado DTLS compatibles.</span><span class="sxs-lookup"><span data-stu-id="936d8-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="936d8-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) Se ha recibido un ClientHello con un método de compresión desconocido.</span><span class="sxs-lookup"><span data-stu-id="936d8-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="936d8-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Error genérico (no especificado) de protocolo de enlace, normalmente debido a problemas con el procesamiento de la extensión.</span><span class="sxs-lookup"><span data-stu-id="936d8-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="936d8-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0X130) Una función que todavía no se admite se invocó durante el protocolo de enlace DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="936d8-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Se ha encontrado un conjunto de aplicaciones de cifrado desconocido (error de criptografía interno indicado).</span><span class="sxs-lookup"><span data-stu-id="936d8-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="936d8-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) Se ha recibido un registro DTLS con una versión DTLS no coincidente.</span><span class="sxs-lookup"><span data-stu-id="936d8-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="936d8-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) No se pudo validar el hash de protocolo de enlace de DTLS, la sesión no es válida.</span><span class="sxs-lookup"><span data-stu-id="936d8-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="936d8-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error de envío UDP interno.</span><span class="sxs-lookup"><span data-stu-id="936d8-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-450">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-450">Allowed From</span></span>

<span data-ttu-id="936d8-451">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-452">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-452">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-453">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-453">See Also</span></span>

- <span data-ttu-id="936d8-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="936d8-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="936d8-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="936d8-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="936d8-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="936d8-459">Inicio de una instancia del servidor NetX Secure DTLS escuchando en el puerto UDP configurado</span><span class="sxs-lookup"><span data-stu-id="936d8-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-460">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="936d8-461">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-461">Description</span></span>

<span data-ttu-id="936d8-462">Este servicio inicia un servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="936d8-463">Una vez que se devuelve la llamada, el servidor está activo y comenzará el procesamiento de las solicitudes entrantes de los clientes de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="936d8-464">La instancia del servidor se debe haber configurado con el servicio *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="936d8-465">Este servicio enlaza el puerto UDP del servidor DTLS interno al puerto local configurado, por lo que la mayoría de los problemas encontrados tendrán que hacerse con las comunicaciones UDP y la configuración de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-466">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-466">Parameters</span></span>

- <span data-ttu-id="936d8-467">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-468">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-468">Return Values</span></span>

- <span data-ttu-id="936d8-469">**NX_SUCCESS** (0x00) Inicio correcto del servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="936d8-470">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-471">**NX_NOT_ENABLED** (0x14) UDP no habilitado.</span><span class="sxs-lookup"><span data-stu-id="936d8-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="936d8-472">**NX_NO_FREE_PORTS** (0X45) No hay puertos UDP disponibles.</span><span class="sxs-lookup"><span data-stu-id="936d8-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="936d8-473">**NX_INVALID_PORT** (0x46) Puerto UDP no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="936d8-474">**NX_ALREADY_BOUND** (0x22) El puerto UDP ya está enlazado.</span><span class="sxs-lookup"><span data-stu-id="936d8-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="936d8-475">**NX_PORT_UNAVAILABLE** (0x23) El puerto UDP no está disponible para su uso.</span><span class="sxs-lookup"><span data-stu-id="936d8-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-476">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-476">Allowed From</span></span>

<span data-ttu-id="936d8-477">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-478">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-478">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-479">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-479">See Also</span></span>

- <span data-ttu-id="936d8-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-482">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="936d8-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="936d8-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="936d8-485">Detención de una instancia activa del servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-486">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="936d8-487">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-487">Description</span></span>

<span data-ttu-id="936d8-488">Este servicio detiene la escucha de un servidor DTLS en el puerto UDP de configuración y restablece todas las sesiones DTLS asociadas, lo que detiene cualquier comunicación DTLS en curso.</span><span class="sxs-lookup"><span data-stu-id="936d8-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-489">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-489">Parameters</span></span>

- <span data-ttu-id="936d8-490">**server_ptr** Puntero a una instancia activa del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-491">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-491">Return Values</span></span>

- <span data-ttu-id="936d8-492">**NX_SUCCESS** (0x00) Detección correcta del servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="936d8-493">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-494">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-494">Allowed From</span></span>

<span data-ttu-id="936d8-495">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-496">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-496">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-497">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-497">See Also</span></span>

- <span data-ttu-id="936d8-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-500">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="936d8-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="936d8-503">Adición de un certificado de CA de confianza a un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-504">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-505">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-505">Description</span></span>

<span data-ttu-id="936d8-506">Este servicio agrega una CA de confianza o un certificado de CA intermedio a una instancia del servidor DTLS y se asigna a todas las sesiones internas del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="936d8-507">Esto solo es necesario si se habilita la autenticación de certificados X.509 de cliente mediante *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="936d8-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="936d8-508">El certificado agregado se usará para comprobar los certificados X.509 de cliente entrantes.</span><span class="sxs-lookup"><span data-stu-id="936d8-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="936d8-509">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-510">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presente en el almacén de servidores DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="936d8-511">Para obtener más información sobre los certificados de servidor X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-512">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-512">Parameters</span></span>

- <span data-ttu-id="936d8-513">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-514">**certificate** Puntero a una estructura de certificados X.509 inicializada previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="936d8-515">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-516">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-516">Return Values</span></span>

- <span data-ttu-id="936d8-517">**NX_SUCCESS** (0x00) Adición correcta del certificado al servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="936d8-518">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-519">**NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-520">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-520">Allowed From</span></span>

<span data-ttu-id="936d8-521">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-522">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-522">Example</span></span>

<span data-ttu-id="936d8-523">\* Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-524">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-524">See Also</span></span>

- <span data-ttu-id="936d8-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-527">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-528">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="936d8-529">nx_secure_dtls_server_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="936d8-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="936d8-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="936d8-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="936d8-532">Eliminación de un certificado de CA de confianza de un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-533">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-534">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-534">Description</span></span>

<span data-ttu-id="936d8-535">Este servicio quita un certificado de CA de confianza de una instancia del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="936d8-536">Los certificados de CA de confianza solo son necesarios para un servidor DTLS para el que se haya habilitado la comprobación de certificados X.509 de cliente mediante una llamada a *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="936d8-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="936d8-537">El certificado que se va a quitar se puede identificar por su nombre común X.509 o por el cert_id numérico que se asignó en la llamada a *nx_secure_dtls_server_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="936d8-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="936d8-538">El cert_id solo se usa para identificar el certificado y lo mantiene la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="936d8-539">Si se usa el nombre común en lugar del identificador de certificado numérico, el parámetro cert_id debe establecerse en 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="936d8-540">Si se quita un certificado mientras se está procesando un protocolo de enlace DTLS, se puede producir un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="936d8-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="936d8-541">Antes de quitar los certificados, se debe llamar al parámetro *nx_secure_dtls_server_stop* de servicio.</span><span class="sxs-lookup"><span data-stu-id="936d8-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-542">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-542">Parameters</span></span>

- <span data-ttu-id="936d8-543">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-544">**common_name** CommonName X.509 del certificado que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="936d8-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="936d8-545">Si se usa, envíe cert_id con valor cero.</span><span class="sxs-lookup"><span data-stu-id="936d8-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="936d8-546">**common_name_length** Longitud de la cadena common_name en bytes.</span><span class="sxs-lookup"><span data-stu-id="936d8-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="936d8-547">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="936d8-548">Si se usa, envíe NX_NULL para el parámetro common_name.</span><span class="sxs-lookup"><span data-stu-id="936d8-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="936d8-549">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-549">Return Values</span></span>

- <span data-ttu-id="936d8-550">**NX_SUCCESS** (0x00) Eliminación correcta del certificado del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="936d8-551">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en el servidor DTLS especificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-553">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-553">Allowed From</span></span>

<span data-ttu-id="936d8-554">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-555">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-555">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-556">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-556">See Also</span></span>

- <span data-ttu-id="936d8-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-558">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-559">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-560">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="936d8-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="936d8-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="936d8-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="936d8-563">Configuración de un servidor NetX Secure DTLS para pedir y comprobar los certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="936d8-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-564">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="936d8-565">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-565">Description</span></span>

<span data-ttu-id="936d8-566">Este servicio configura un servidor DTLS para pedir y comprobar los certificados de cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="936d8-567">Esta función opcional se usa cuando se quiere usar certificados X.509 para la autenticación de clientes en lugar de otros mecanismos (por ejemplo, una clave precompartida).</span><span class="sxs-lookup"><span data-stu-id="936d8-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="936d8-568">*Cuando se configura un servidor DTLS para comprobar los certificados de cliente que usan este servicio, debe agregarse al menos un certificado de CA de confianza al servidor mediante nx_secure_dtls_server_trusted_certificate_add o el servidor rechazará todas las conexiones de cliente entrantes porque no podrá comprobar los certificados de cliente en el almacén de confianza.*</span><span class="sxs-lookup"><span data-stu-id="936d8-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="936d8-569">Tras llamar a este servicio, la instancia del servidor DTLS pide (una vez iniciado) certificados de cliente como parte del protocolo de enlace DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="936d8-570">Suponiendo que el cliente está correctamente configurado con un certificado de identidad (y la cadena de certificados asociada cuando corresponda), el servidor DTLS necesita que se asigne memoria para procesar los datos del certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="936d8-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="936d8-571">Esta memoria se envía como el parámetro *certs_buffer*.</span><span class="sxs-lookup"><span data-stu-id="936d8-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="936d8-572">Se debe ajustar el tamaño de certs_buffer para dar cabida a la cadena de certificados más grande esperada de un cliente DTLS, multiplicada por el *número de sesiones del servidor DTLS*</span><span class="sxs-lookup"><span data-stu-id="936d8-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="936d8-573">El búfer se divide entre las sesiones disponibles mediante el parámetro *certs_per_session* que representa el número máximo esperado de certificados en una cadena de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="936d8-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="936d8-574">El búfer también debe proporcionar espacio para la estructura de datos NX_SECURE_X509_CERT que se usa para analizar los datos del certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="936d8-575">El cálculo del tamaño de búfer adecuado se puede realizar con la fórmula siguiente:</span><span class="sxs-lookup"><span data-stu-id="936d8-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="936d8-576">El número de sesiones DTLS viene determinado por el tamaño del búfer de sesión enviado en nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="936d8-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="936d8-577">certs_per_session debe establecerse en el número máximo esperado de certificados en cualquier cadena de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="936d8-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="936d8-578">El tamaño máximo esperado del certificado depende de la aplicación, los tamaños de clave y otros factores, pero normalmente 2 KB es suficiente.</span><span class="sxs-lookup"><span data-stu-id="936d8-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-579">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-579">Parameters</span></span>

- <span data-ttu-id="936d8-580">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="936d8-581">**certs_per_session** Número de certificados que se van a asignar a cada sesión del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="936d8-582">**certs_buffer** Espacio en búfer para los datos de los certificados entrantes.</span><span class="sxs-lookup"><span data-stu-id="936d8-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="936d8-583">**buffer_size** Tamaño del búfer de certificados.</span><span class="sxs-lookup"><span data-stu-id="936d8-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-584">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-584">Return Values</span></span>

- <span data-ttu-id="936d8-585">**NX_SUCCESS** (0x00) Configuración correcta de la comprobación del cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="936d8-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="936d8-586">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-587">**NX_INVALID_PARAMETERS** (0x4D) Almacén de certificados no válido (¿instancia de DTLSserver no inicializada?).</span><span class="sxs-lookup"><span data-stu-id="936d8-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-588">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-588">Allowed From</span></span>

<span data-ttu-id="936d8-589">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-590">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-590">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-591">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-591">See Also</span></span>

- <span data-ttu-id="936d8-592">nx_secure_dtls_server_x509_client_verify_disable,</span><span class="sxs-lookup"><span data-stu-id="936d8-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="936d8-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-594">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-595">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-596">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="936d8-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="936d8-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="936d8-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="936d8-599">Deshabilita la comprobación de certificados X.509 del cliente para un servidor NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-600">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="936d8-601">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-601">Description</span></span>

<span data-ttu-id="936d8-602">Este servicio deshabilita la comprobación de certificados X.509 de cliente en un servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="936d8-603">El servicio no tiene ningún efecto si la comprobación de certificados de cliente X.509 no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="936d8-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="936d8-604">Deshabilitar la autenticación de cliente en una instancia del servidor DTLS activa puede producir un comportamiento impredecible.</span><span class="sxs-lookup"><span data-stu-id="936d8-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="936d8-605">Se debe llamar al servicio nx_secure_dtls_server_stop antes de cambiar el estado del servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-606">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-606">Parameters</span></span>

- <span data-ttu-id="936d8-607">**server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-608">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-608">Return Values</span></span>

- <span data-ttu-id="936d8-609">**NX_SUCCESS** (0x00) Deshabilitación correcta de la autenticación del cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="936d8-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="936d8-610">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-611">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-611">Allowed From</span></span>

<span data-ttu-id="936d8-612">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-613">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-613">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-614">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-614">See Also</span></span>

- <span data-ttu-id="936d8-615">nx_secure_dtls_server_x509_client_verify_configure,</span><span class="sxs-lookup"><span data-stu-id="936d8-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="936d8-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="936d8-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="936d8-617">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="936d8-618">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="936d8-619">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="936d8-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="936d8-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="936d8-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="936d8-622">Obtención de información del cliente remoto desde una sesión del servidor DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-623">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="936d8-624">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-624">Description</span></span>

<span data-ttu-id="936d8-625">Este servicio devuelve la información de red sobre un cliente DTLS que está conectado a una sesión determinada del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="936d8-626">La información devuelta consta de la dirección IP y el puerto UDP del cliente remoto, así como del puerto del servidor local al que está conectado el cliente.</span><span class="sxs-lookup"><span data-stu-id="936d8-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="936d8-627">En general, la instancia de sesión DTLS será la obtenida en la invocación de una de las rutinas de devolución de llamada de notificación DTLS (por ejemplo, las devoluciones de llamada connect_notify o receive_notify enviadas en nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="936d8-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-628">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-628">Parameters</span></span>

- <span data-ttu-id="936d8-629">**session_ptr** Puntero a una instancia activa de sesión del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-630">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-630">Return Values</span></span>

- <span data-ttu-id="936d8-631">**NX_SUCCESS** (0x00) Eliminación correcta del servidor.</span><span class="sxs-lookup"><span data-stu-id="936d8-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="936d8-632">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-633">**NX_INVALID_SOCKET** (0X13) El socket UDP asociado no es válido (¿sesión no inicializada?).</span><span class="sxs-lookup"><span data-stu-id="936d8-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="936d8-634">**NX_NOT_CONNECTED** (0x38) El socket UDP no está conectado: la conexión de cliente ha caído o no se ha establecido todavía.</span><span class="sxs-lookup"><span data-stu-id="936d8-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-635">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-635">Allowed From</span></span>

<span data-ttu-id="936d8-636">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-637">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-637">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-638">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-638">See Also</span></span>

- <span data-ttu-id="936d8-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span><span class="sxs-lookup"><span data-stu-id="936d8-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="936d8-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="936d8-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="936d8-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="936d8-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="936d8-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="936d8-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="936d8-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="936d8-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="936d8-644">Creación y configuración de una sesión de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-645">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-645">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="936d8-646">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-646">Description</span></span>

<span data-ttu-id="936d8-647">Este servicio crea y configura una sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="936d8-648">Por lo general, esto se usará para crear sesiones de cliente DTLS, ya que las sesiones del servidor DTLS se administran con el mecanismo de servidor DTLS (consulte *nx_secure_dtls_server_create*), pero puede haber instancias en las que una aplicación necesita crear una única instancia de sesión de servidor DTLS independiente, en cuyo caso se puede usar este servicio<sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="936d8-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="936d8-649">Los parámetros configuran la información y la asignación de memoria necesaria para crear una instancia de una sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="936d8-650">El parámetro crypto_table es una tabla de TLS que contiene todas las rutinas criptográficas necesarias para el cifrado y la autenticación de TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="936d8-651">El parámetro metadata_buffer se usa para cálculos de cifrado (consulte nx_secure_tls_metadata_size_calculate en la guía de usuario de NetX Secure TLS) y el parámetro packet_reassembly_buffer se usa para volver a ensamblar los datagramas UDP en un registro DTLS completo para el descifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="936d8-652">Los parámetros certs_number y remote_certificate_buffer son necesarios para los clientes DTLS que necesitan espacio para almacenar y procesar la cadena de certificados entrante del servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="936d8-653">El búfer debe ser capaz de dar cabida al tamaño máximo previsto de la cadena de certificados para cualquier servidor al que se conectará.</span><span class="sxs-lookup"><span data-stu-id="936d8-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="936d8-654">El búfer se divide por el número de certificados esperados (parámetro certs_number) y también debe ser lo suficientemente grande como para contener una estructura NX_SECURE_X509_CERT por certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="936d8-655">El tamaño del búfer se puede determinar mediante la siguiente fórmula:</span><span class="sxs-lookup"><span data-stu-id="936d8-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="936d8-656">certs_number es el número máximo esperado de certificados en la cadena de certificados del servidor</span><span class="sxs-lookup"><span data-stu-id="936d8-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="936d8-657">El tamaño máximo de los certificados depende del tamaño de las claves que se usan y de la información del certificado, pero 2 KB suele ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="936d8-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="936d8-658">**7** La creación de sesiones del servidor DTLS con esta rutina no se recomienda y tiene algunas limitaciones.</span><span class="sxs-lookup"><span data-stu-id="936d8-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="936d8-659">El principal problema es que la sesión no controlará conexiones de cliente adicionales correctamente; como el UDP no tiene conexión, un segundo cliente puede enviar datos legalmente al puerto UDP del servidor cuando una sesión DTLS anterior todavía está activa, lo que haría que la sesión del servidor finalizara con un error.</span><span class="sxs-lookup"><span data-stu-id="936d8-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-660">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-660">Parameters</span></span>

- <span data-ttu-id="936d8-661">**dtls_session** Puntero a una estructura de sesión DTLS sin inicializar.</span><span class="sxs-lookup"><span data-stu-id="936d8-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="936d8-662">**crypto_table** Puntero a una estructura de tabla de cifrado TLS/DTLS usada para todas las operaciones criptográficas.</span><span class="sxs-lookup"><span data-stu-id="936d8-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="936d8-663">**crypto_metadata_buffer** Espacio en búfer para cálculos de operaciones criptográficas e información de estado.</span><span class="sxs-lookup"><span data-stu-id="936d8-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="936d8-664">**crypto_metadata_size** Tamaño del búfer de metadatos.</span><span class="sxs-lookup"><span data-stu-id="936d8-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="936d8-665">**packet_reassembly_buffer** Búfer usado por DTLS para volver a ensamblar los datos de UDP en los registros de DTLS para el descifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="936d8-666">**packet_reassembly_buffer_size** Tamaño del búfer de reensamblado.</span><span class="sxs-lookup"><span data-stu-id="936d8-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="936d8-667">Por lo general, debe ser mayor que 16 KB, pero puede ser menor en función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="936d8-668">**certs_number** Número máximo esperado de certificados en la cadena de certificados del servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="936d8-669">**remote_certificate_buffer** Espacio en búfer para los datos de los certificados entrantes.</span><span class="sxs-lookup"><span data-stu-id="936d8-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="936d8-670">**remote_certificate_buffer_size** Tamaño del búfer de certificados.</span><span class="sxs-lookup"><span data-stu-id="936d8-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="936d8-671">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-671">Return Values</span></span>

- <span data-ttu-id="936d8-672">**NX_SUCCESS** (0x00) Creación correcta de la sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="936d8-673">**NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="936d8-674">**NX_INVALID_PARAMETERS** (0X4D) No hay suficiente espacio de búfer para el reensamblado de paquetes, los certificados o la criptografía.</span><span class="sxs-lookup"><span data-stu-id="936d8-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-675">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-675">Allowed From</span></span>

<span data-ttu-id="936d8-676">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-677">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-677">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-678">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-678">See Also</span></span>

- <span data-ttu-id="936d8-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="936d8-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="936d8-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="936d8-682">Liberación de recursos usados por una sesión NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-683">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="936d8-684">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-684">Description</span></span>

<span data-ttu-id="936d8-685">Este servicio elimina una sesión DTLS, lo que libera todos los recursos que se asignaron cuando se creó.</span><span class="sxs-lookup"><span data-stu-id="936d8-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-686">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-686">Parameters</span></span>

- <span data-ttu-id="936d8-687">**dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-688">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-688">Return Values</span></span>

- <span data-ttu-id="936d8-689">**NX_SUCCESS** (0x00) Eliminación correcta de la sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="936d8-690">**NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-691">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-691">Allowed From</span></span>

<span data-ttu-id="936d8-692">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-693">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-693">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-694">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-694">See Also</span></span>

- <span data-ttu-id="936d8-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="936d8-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="936d8-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="936d8-698">Apagado de una sesión NetX Secure DTLS activa</span><span class="sxs-lookup"><span data-stu-id="936d8-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-699">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="936d8-700">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-700">Description</span></span>

<span data-ttu-id="936d8-701">Este servicio finaliza una sesión DTLS activa mediante el envío de una alerta CloseNotify de TLS/DTLS al host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="936d8-702">La dirección IP y el puerto usados son los que se usan en la llamada anterior a nx_secure_dtls_session_send.</span><span class="sxs-lookup"><span data-stu-id="936d8-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-703">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-703">Parameters</span></span>

- <span data-ttu-id="936d8-704">**dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="936d8-705">**wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-706">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-706">Return Values</span></span>

- <span data-ttu-id="936d8-707">**NX_SUCCESS** (0x00) Eliminación correcta de la sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="936d8-708">**NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="936d8-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) No se pudo asignar paquetes para la alerta CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="936d8-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="936d8-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Probable error interno: no se reconoce la rutina criptográfica.</span><span class="sxs-lookup"><span data-stu-id="936d8-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="936d8-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error de envío UDP subyacente.</span><span class="sxs-lookup"><span data-stu-id="936d8-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="936d8-712">**NX_IP_ADDRESS_ERROR** (0x21) Error con la dirección IP del host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="936d8-713">**NX_NOT_BOUND** (0x24) Socket UDP subyacente no enlazado al puerto.</span><span class="sxs-lookup"><span data-stu-id="936d8-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="936d8-714">**NX_INVALID_PORT** (0x46) Puerto UDP no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="936d8-715">**NX_PORT_UNAVAILABLE** (0x23) El puerto UDP no está disponible para su uso.</span><span class="sxs-lookup"><span data-stu-id="936d8-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-716">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-716">Allowed From</span></span>

<span data-ttu-id="936d8-717">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-718">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-718">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-719">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-719">See Also</span></span>

- <span data-ttu-id="936d8-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="936d8-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="936d8-723">Adición de un certificado de identidad local a una sesión de NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-724">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-725">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-725">Description</span></span>

<span data-ttu-id="936d8-726">Este servicio agrega un certificado de identidad local a una instancia de sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="936d8-727">En general, este servicio se usará cuando una sesión de cliente DTLS necesite proporcionar un certificado de identidad a un host de servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="936d8-728">Se trata de una configuración opcional para DTLS, por lo que no suele ser necesario un certificado para los clientes de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="936d8-729">Un certificado de identidad necesita una clave privada asociada.</span><span class="sxs-lookup"><span data-stu-id="936d8-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="936d8-730">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-731">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="936d8-732">Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-733">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-733">Parameters</span></span>

- <span data-ttu-id="936d8-734">**session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-735">**certificate** Puntero a una estructura de certificados X.509 inicializada previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="936d8-736">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-737">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-737">Return Values</span></span>

- <span data-ttu-id="936d8-738">**NX_SUCCESS** (0x00) Adición correcta del certificado a la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="936d8-739">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-740">**NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-741">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-741">Allowed From</span></span>

<span data-ttu-id="936d8-742">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-743">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-743">Example</span></span>

<span data-ttu-id="936d8-744">\*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-745">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-745">See Also</span></span>

- <span data-ttu-id="936d8-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="936d8-748">nx_secure_dtls_session_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="936d8-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="936d8-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="936d8-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="936d8-751">Eliminación de un certificado de identidad local de una sesión NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-752">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-753">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-753">Description</span></span>

<span data-ttu-id="936d8-754">Este servicio quita un certificado de identidad local de una instancia de sesión DTLS con un número de identificación de certificado (asignado cuando el certificado se agregó con nx_secure_dtls_session_local_certificate_add) o el campo CommonName X.509.</span><span class="sxs-lookup"><span data-stu-id="936d8-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="936d8-755">Si el parámetro common_name se usa para coincidir con el certificado, el parámetro cert_id debe establecerse en 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="936d8-756">Si se usa cert_id, common_name debe enviarse un valor NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="936d8-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="936d8-757">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-758">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="936d8-759">Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-760">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-760">Parameters</span></span>

- <span data-ttu-id="936d8-761">**session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-762">**common_name** Puntero a la cadena CommonName que debe coincidir.</span><span class="sxs-lookup"><span data-stu-id="936d8-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="936d8-763">**common_name_length** Longitud de la cadena common_name.</span><span class="sxs-lookup"><span data-stu-id="936d8-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="936d8-764">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-765">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-765">Return Values</span></span>

- <span data-ttu-id="936d8-766">**NX_SUCCESS** (0x00) Eliminación correcta del certificado de la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="936d8-767">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en la sesión DTLS especificada.</span><span class="sxs-lookup"><span data-stu-id="936d8-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-769">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-769">Allowed From</span></span>

<span data-ttu-id="936d8-770">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-771">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-771">Example</span></span>

<span data-ttu-id="936d8-772">\*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-773">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-773">See Also</span></span>

- <span data-ttu-id="936d8-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="936d8-776">nx_secure_dtls_session_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="936d8-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="936d8-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="936d8-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="936d8-779">Recepción de datos de la aplicación a través de una sesión NetX Secure DTLS establecida</span><span class="sxs-lookup"><span data-stu-id="936d8-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-780">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="936d8-781">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-781">Description</span></span>

<span data-ttu-id="936d8-782">Este servicio devuelve datos de aplicación recibidos por una sesión DTLS activa.</span><span class="sxs-lookup"><span data-stu-id="936d8-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="936d8-783">La sesión DTLS puede ser una sesión de servidor DTLS (administrada por una instancia del servidor DTLS) o una sesión de cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="936d8-784">El paquete devuelto se puede procesar con cualquiera de los servicios de NX_PACKET API (consulte la documentación de NetX para obtener más información).</span><span class="sxs-lookup"><span data-stu-id="936d8-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-785">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-785">Parameters</span></span>

- <span data-ttu-id="936d8-786">**dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="936d8-787">**packet_ptr_ptr** Puntero a un puntero NX_PACKET para el paquete devuelto.</span><span class="sxs-lookup"><span data-stu-id="936d8-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="936d8-788">**wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.</span><span class="sxs-lookup"><span data-stu-id="936d8-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-789">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-789">Return Values</span></span>

- <span data-ttu-id="936d8-790">**NX_SUCCESS** (0x00) Recepción correcta del paquete de datos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="936d8-791">**NX_PTR_ERROR** (0x07) Puntero no válido de paquete o sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="936d8-792">**NX_NOT_ENABLED** (0x14) El UDP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="936d8-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="936d8-793">**NX_NOT_BOUND** (0x24) Socket UDP no enlazado al puerto.</span><span class="sxs-lookup"><span data-stu-id="936d8-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="936d8-794">**NX_SECURE_TLS_INVALID_PACKET** (0X104) Se han recibido datos que no eran un registro DTLS válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="936d8-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un registro DTLS no se pudo codificar correctamente (error de cifrado).</span><span class="sxs-lookup"><span data-stu-id="936d8-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="936d8-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Error al comprobar el relleno de cifrado.</span><span class="sxs-lookup"><span data-stu-id="936d8-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="936d8-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) Se ha recibido una alerta del host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="936d8-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Se ha recibido un mensaje desconocido.</span><span class="sxs-lookup"><span data-stu-id="936d8-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="936d8-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) Se ha recibido un registro DTLS con una longitud no válida.</span><span class="sxs-lookup"><span data-stu-id="936d8-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="936d8-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Se ha encontrado un conjunto de aplicaciones de cifrado desconocido (indica un error interno de criptografía).</span><span class="sxs-lookup"><span data-stu-id="936d8-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="936d8-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) Se ha recibido un registro DTLS con una versión DTLS no coincidente.</span><span class="sxs-lookup"><span data-stu-id="936d8-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-802">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-802">Allowed From</span></span>

<span data-ttu-id="936d8-803">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-804">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-804">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-805">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-805">See Also</span></span>

- <span data-ttu-id="936d8-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span><span class="sxs-lookup"><span data-stu-id="936d8-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="936d8-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="936d8-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="936d8-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="936d8-809">Eliminación de datos en una instancia de sesión NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-810">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="936d8-811">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-811">Description</span></span>

<span data-ttu-id="936d8-812">Este servicio restablece una sesión DTLS y borra todos los datos criptográficos efímeros, lo que permite que la estructura se vuelva a usar para una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="936d8-813">Los datos persistentes (por ejemplo, los almacenes de certificados) se mantienen para que no sea necesario llamar a nx_secure_dtls_session_create de forma repetida.</span><span class="sxs-lookup"><span data-stu-id="936d8-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-814">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-814">Parameters</span></span>

- <span data-ttu-id="936d8-815">**dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-816">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-816">Return Values</span></span>

- <span data-ttu-id="936d8-817">**NX_SUCCESS** (0x00) Sesión restablecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="936d8-818">**NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.</span><span class="sxs-lookup"><span data-stu-id="936d8-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-819">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-819">Allowed From</span></span>

<span data-ttu-id="936d8-820">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-821">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-821">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-822">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-822">See Also</span></span>

- <span data-ttu-id="936d8-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="936d8-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="936d8-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="936d8-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="936d8-826">Envío de datos a través de una sesión DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-827">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="936d8-828">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-828">Description</span></span>

<span data-ttu-id="936d8-829">Este servicio envía un paquete de datos a través de una sesión DTLS establecida a un host de DTLS remoto en la dirección IP y el puerto especificados.</span><span class="sxs-lookup"><span data-stu-id="936d8-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="936d8-830">La sesión usada es una sesión de cliente DTLS activa.</span><span class="sxs-lookup"><span data-stu-id="936d8-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="936d8-831">Tenga en cuenta que la dirección IP y el puerto se proporcionan debido a la naturaleza sin estado del UDP, pero por lo general deben coincidir con la dirección y el puerto usados para iniciar la sesión en nx_secure_dtls_session_start.</span><span class="sxs-lookup"><span data-stu-id="936d8-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="936d8-832">Los datos proporcionados en el paquete, que se deben asignar mediante *nx_secure_dtls_packet_allocate*, se cifran mediante los parámetros criptográficos y las rutinas de la sesión DTLS y, a continuación, se envían al host remoto a través del socket UDP de la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-833">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-833">Parameters</span></span>

- <span data-ttu-id="936d8-834">**session_ptr** Puntero a una instancia de sesión de cliente DTLS activa.</span><span class="sxs-lookup"><span data-stu-id="936d8-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="936d8-835">**packet_ptr** Puntero a una instancia NX_PACKET asignada previamente y rellenada con datos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="936d8-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="936d8-836">**ip_address** Puntero a una estructura NXD_ADDRESS que contiene la dirección IP del host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="936d8-837">**port** Puerto UDP en el host remoto.</span><span class="sxs-lookup"><span data-stu-id="936d8-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-838">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-838">Return Values</span></span>

- <span data-ttu-id="936d8-839">**NX_SUCCESS** (0x00) Envío correcto del paquete.</span><span class="sxs-lookup"><span data-stu-id="936d8-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="936d8-840">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Se produjo un error en la operación de envío de UDP subyacente.</span><span class="sxs-lookup"><span data-stu-id="936d8-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-842">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-842">Allowed From</span></span>

<span data-ttu-id="936d8-843">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-844">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-844">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-845">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-845">See Also</span></span>

- <span data-ttu-id="936d8-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="936d8-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="936d8-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="936d8-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="936d8-849">Adición de un certificado de CA de confianza a una sesión NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-850">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-851">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-851">Description</span></span>

<span data-ttu-id="936d8-852">Este servicio agrega una CA de confianza o un certificado X.509 de CA intermedio a una instancia de sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="936d8-853">Un cliente DTLS necesita al menos un certificado de confianza para validar los certificados de servidor remoto, a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas).</span><span class="sxs-lookup"><span data-stu-id="936d8-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="936d8-854">Un certificado de confianza no suele tener una clave privada.</span><span class="sxs-lookup"><span data-stu-id="936d8-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="936d8-855">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-856">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="936d8-857">Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-858">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-858">Parameters</span></span>

- <span data-ttu-id="936d8-859">**session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-860">**certificate** Puntero a una estructura de certificados X.509 inicializada previamente.</span><span class="sxs-lookup"><span data-stu-id="936d8-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="936d8-861">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="936d8-862">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-862">Return Values</span></span>

- <span data-ttu-id="936d8-863">**NX_SUCCESS** (0x00) Adición correcta del certificado a la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="936d8-864">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-865">**NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-866">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-866">Allowed From</span></span>

<span data-ttu-id="936d8-867">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-868">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-868">Example</span></span>

<span data-ttu-id="936d8-869">\*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-870">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-870">See Also</span></span>

- <span data-ttu-id="936d8-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="936d8-873">nx_secure_dtls_session_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="936d8-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="936d8-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="936d8-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="936d8-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="936d8-876">Eliminación de un certificado de CA de confianza de una sesión NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="936d8-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="936d8-877">Prototipo</span><span class="sxs-lookup"><span data-stu-id="936d8-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="936d8-878">Descripción</span><span class="sxs-lookup"><span data-stu-id="936d8-878">Description</span></span>

<span data-ttu-id="936d8-879">Este servicio quita un certificado de CA de confianza de una instancia de sesión DTLS con un número de id. de certificado (asignado cuando el certificado se agregó con nx_secure_dtls_session_trusted_certificate_add) o el campo CommonName X.509.</span><span class="sxs-lookup"><span data-stu-id="936d8-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="936d8-880">Si el parámetro common_name se usa para coincidir con el certificado, el parámetro cert_id debe establecerse en 0.</span><span class="sxs-lookup"><span data-stu-id="936d8-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="936d8-881">Si se usa cert_id, common_name debe enviarse un valor NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="936d8-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="936d8-882">El parámetro cert_id es un identificador numérico distinto de cero para el certificado.</span><span class="sxs-lookup"><span data-stu-id="936d8-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="936d8-883">Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="936d8-884">Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="936d8-885">Parámetros</span><span class="sxs-lookup"><span data-stu-id="936d8-885">Parameters</span></span>

- <span data-ttu-id="936d8-886">**session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="936d8-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="936d8-887">**common_name** Puntero a la cadena CommonName que debe coincidir.</span><span class="sxs-lookup"><span data-stu-id="936d8-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="936d8-888">**common_name_length** Longitud de la cadena common_name.</span><span class="sxs-lookup"><span data-stu-id="936d8-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="936d8-889">**cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="936d8-890">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="936d8-890">Return Values</span></span>

- <span data-ttu-id="936d8-891">**NX_SUCCESS** (0x00) Eliminación correcta del certificado de la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="936d8-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="936d8-892">**NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="936d8-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="936d8-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en la sesión DTLS especificada.</span><span class="sxs-lookup"><span data-stu-id="936d8-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="936d8-894">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="936d8-894">Allowed From</span></span>

<span data-ttu-id="936d8-895">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="936d8-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="936d8-896">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="936d8-896">Example</span></span>

<span data-ttu-id="936d8-897">\*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="936d8-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="936d8-898">Consulte también</span><span class="sxs-lookup"><span data-stu-id="936d8-898">See Also</span></span>

- <span data-ttu-id="936d8-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="936d8-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="936d8-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="936d8-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="936d8-901">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="936d8-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="936d8-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="936d8-902">nx_secure_x509_certificate_initialize</span></span>
