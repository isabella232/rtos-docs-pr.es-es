---
title: 'Capítulo 1: Introducción al cliente Azure RTOS NetX POP3'
description: La API de cliente POP3 de Azure RTOS NetX proporciona un sistema de transporte de correo que permite que las estaciones de trabajo pequeñas accedan a los maildrops de los clientes en los servidores POP3 para recuperar el correo de los clientes.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815166"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="f0ac2-103">Capítulo 1: Introducción al cliente Azure RTOS NetX POP3</span><span class="sxs-lookup"><span data-stu-id="f0ac2-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="f0ac2-104">El Protocolo de oficina de correo versión 3 (POP3) está diseñado para proporcionar un sistema de transporte de correo que permite que las estaciones de trabajo pequeñas accedan a los maildrops de los clientes en los servidores POP3 para recuperar el correo de los clientes.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="f0ac2-105">POP3 emplea servicios de protocolo de control de transmisión (TCP) para realizar la transferencia de archivos.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="f0ac2-106">Por este motivo, POP3 es un protocolo de transferencia de contenido de gran confiabilidad.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="f0ac2-107">Sin embargo, POP3 no proporciona operaciones extensas en el control de correo.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="f0ac2-108">Por lo general, el cliente descarga el correo y, a continuación, se elimina del maildrop del servidor.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="f0ac2-109">Requisitos del cliente POP3 de NetX</span><span class="sxs-lookup"><span data-stu-id="f0ac2-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="f0ac2-110">Requisitos de cliente</span><span class="sxs-lookup"><span data-stu-id="f0ac2-110">Client Requirements</span></span>

<span data-ttu-id="f0ac2-111">La API de cliente POP3 de Azure RTOS NetX requiere una instancia de IP de NetX creada anteriormente mediante *nx_ip_create* y un grupo de paquetes NetX creado previamente mediante *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="f0ac2-112">Como el cliente POP3 de NetX usa servicios TCP, se debe habilitar TCP con la llamada *nx_tcp_enable* antes de usar los servicios del cliente POP3 de NetX en esa misma instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="f0ac2-113">El cliente POP3 usa un socket TCP para conectarse a un servidor POP3 en el puerto POP3 del servidor.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="f0ac2-114">Por lo general, se establece en el *puerto 110 conocido, aunque no se requiere ningún servidor ni cliente POP3 para usar este puerto.*</span><span class="sxs-lookup"><span data-stu-id="f0ac2-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="f0ac2-115">El usuario puede configurar el tamaño del grupo de paquetes utilizado al crear el cliente POP3 en términos de carga de paquetes y cantidad de paquetes disponibles.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="f0ac2-116">Si el paquete solo se usa en el servicio de creación del cliente POP3, la carga del paquete no necesita más de 100 a 120 bytes en función de la longitud del nombre de usuario y la contraseña, o la síntesis APOP.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="f0ac2-117">El comando USER con el nombre de usuario del host local es probablemente el mensaje más grande enviado por el cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="f0ac2-118">Es posible compartir el mismo grupo de paquetes en nx_ip_create (grupo de paquetes IP predeterminado), ya que las operaciones internas de IP no requieren una carga de paquetes muy grande para enviar y recibir datos de control de TCP.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="f0ac2-119">Sin embargo, es posible que el controlador de red no sea ventajoso para usar el mismo grupo de paquetes que el grupo de paquetes del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="f0ac2-120">Normalmente, la carga del grupo de paquetes de recepción se establece en la instancia de IP MTU (por lo general, 1500 bytes) de la interfaz de red, que es mucho más grande que los mensajes del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="f0ac2-121">Los mensajes POP3 entrantes suelen ser datos mucho más grandes que los mensajes del cliente POP3 salientes.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="f0ac2-122">Creación del cliente POP3 de NetX</span><span class="sxs-lookup"><span data-stu-id="f0ac2-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="f0ac2-123">El servicio de creación del cliente POP3, *nx_pop3_client_create*, crea el socket TCP y se conecta con el servidor POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="f0ac2-124">Después de conectar con el servidor POP3, la aplicación cliente POP3 puede llamar a *nx_pop3_client _mail_items_get* para obtener el número de elementos de correo que se encuentran en el cuadro maildrop:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="f0ac2-125">Si uno o más elementos están en el maildrop del cliente, la aplicación puede obtener el tamaño de un elemento de correo específico mediante el servicio *nx_pop3_client_get_mail_item*:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="f0ac2-126">El primer elemento de correo del maildrop se encuentra en el índice 1.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="f0ac2-127">Para obtener el mensaje de correo real, la aplicación puede llamar al servicio *nx_pop3_client_mail_item_get_message_data* a fin de recuperar los paquetes de mensajes de correo hasta que el servicio indique que el argumento de entrada final_packet recibe el último paquete:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="f0ac2-128">Para eliminar un elemento de correo específico, la aplicación llama a *nx_pop3_client_mail_item_delete* con el mismo índice que se utilizó en la llamada a *nx_pop3_client_get_mail_item* anterior.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="f0ac2-129">Se puede eliminar el cliente mediante el servicio *nx_pop3_client_delete*.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="f0ac2-130">Tenga en cuenta que depende de la aplicación eliminar el grupo de paquetes del cliente POP3 mediante el servicio *nx_packet_pool_delete* si ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="f0ac2-131">Restricciones del cliente POP3 de NetX</span><span class="sxs-lookup"><span data-stu-id="f0ac2-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="f0ac2-132">Existen algunas restricciones en la implementación del cliente POP3 de NetX:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="f0ac2-133">El cliente POP3 de NetX no admite el comando AUTH, aunque implementa la autenticación APOP mediante DIGEST-MD5 para el intercambio de autenticación cliente-servidor.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="f0ac2-134">El cliente POP3 de NetX no implementa todos los comandos de POP3 (por ejemplo, los comandos TOP o UIDL).</span><span class="sxs-lookup"><span data-stu-id="f0ac2-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="f0ac2-135">A continuación se muestra una lista de los comandos que admite:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="f0ac2-136">NOOP</span><span class="sxs-lookup"><span data-stu-id="f0ac2-136">NOOP</span></span>
   - <span data-ttu-id="f0ac2-137">RSET</span><span class="sxs-lookup"><span data-stu-id="f0ac2-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="f0ac2-138">Inicio de sesión del cliente POP3 de NetX</span><span class="sxs-lookup"><span data-stu-id="f0ac2-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="f0ac2-139">Un cliente POP3 de NetX debe autenticarse (iniciar sesión) en un servidor POP3 para tener acceso a un maildrop.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="f0ac2-140">Para ello, puede usar los comandos USER/PASS y proporcionar un nombre de usuario y una contraseña conocidos para el servidor POP3, o bien mediante el comando APOP y la síntesis MD5 que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="f0ac2-141">El nombre de usuario suele ser un nombre de dominio completo (contiene una parte local y un nombre de dominio, separados por un carácter "@").</span><span class="sxs-lookup"><span data-stu-id="f0ac2-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="f0ac2-142">Al usar los comandos USER y PASS de POP3, el cliente envía su nombre de usuario y contraseña sin cifrar a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="f0ac2-143">Para evitar el riesgo de seguridad de ingresar el nombre de usuario y la contraseña en texto sin formato, el cliente POP3 de NetX se puede configurar para usar la autenticación APOP configurando el parámetro *APOP_authentication* en el servicio *nx_pop3_client_create*:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="f0ac2-144">O bien, solo para las aplicaciones IPv4, el servicio *nx_pop3_client_create*:</span><span class="sxs-lookup"><span data-stu-id="f0ac2-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="f0ac2-145">Cuando el cliente envía el comando APOP, toma una síntesis MD5 que contiene el dominio del servidor, la hora local y el id. de proceso extraídos del saludo del servidor, además de la contraseña del cliente.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="f0ac2-146">El servidor POP3 creará una síntesis MD5 que contiene la misma información y, si su síntesis MD5 coincide con el resumen MD5 del cliente, el cliente se autentica.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="f0ac2-147">Si se produce un error en la autenticación de APOP, el cliente POP3 de NetX intentará la autenticación con USER/PASS.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="f0ac2-148">Maildrop de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="f0ac2-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="f0ac2-149">El correo del cliente se almacena en un servidor POP3 en un buzón o "maildrop".</span><span class="sxs-lookup"><span data-stu-id="f0ac2-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="f0ac2-150">Un maildrop de cliente en un servidor POP3 se representa como una lista de elementos de correo electrónico basada en 1.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="f0ac2-151">Es decir, para hacer referencia a cada correo, se hace mediante su índice en la lista del maildrop con el primer elemento de correo en el índice 1 (no cero).</span><span class="sxs-lookup"><span data-stu-id="f0ac2-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="f0ac2-152">Los comandos de POP3 hacen referencia a elementos de correo específicos según su índice en esta lista.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="f0ac2-153">Máquina de estados del protocolo POP3</span><span class="sxs-lookup"><span data-stu-id="f0ac2-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="f0ac2-154">El protocolo POP3 requiere que tanto el cliente como el servidor mantengan el estado de la sesión POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="f0ac2-155">En primer lugar, el cliente intenta conectarse al servidor POP3.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="f0ac2-156">Si se ejecuta correctamente, entra en el protocolo POP3 que tiene tres estados distintos que se definen en RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="f0ac2-157">El estado inicial es el estado de autorización con el que debe identificarse en el servidor.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="f0ac2-158">En el estado de autorización, el cliente POP3 solo puede emitir los comandos USER y PASS, y en ese orden, o el comando APOP.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="f0ac2-159">Una vez que se autentica el cliente POP3, la sesión del cliente entra en el estado de transacción.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="f0ac2-160">En este estado, el cliente puede descargar correo y solicitar su eliminación.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="f0ac2-161">Los comandos que permite el estado de transacción son LIST, STAT, RETR, DELE, RSET y QUIT.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="f0ac2-162">Por lo general, el cliente POP3 envía un comando STAT seguido de una serie de comandos RETR (uno para cada elemento de correo en su maildrop).</span><span class="sxs-lookup"><span data-stu-id="f0ac2-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="f0ac2-163">Una vez que el cliente emite el comando QUIT, la sesión POP3 entra en el estado de actualización en el que se inicia la desconexión TCP del servidor.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="f0ac2-164">Para descargar correo más tarde, la aplicación cliente POP3 puede llamar a `nx_pop3_client_mail_items_get` en cualquier momento para comprobar si hay correo nuevo en el maildrop.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="f0ac2-165">Códigos de respuesta del servidor POP3</span><span class="sxs-lookup"><span data-stu-id="f0ac2-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="f0ac2-166">**+OK**: el servidor utiliza esta respuesta para aceptar un comando de cliente.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="f0ac2-167">El servidor puede incluir información adicional después de "+OK", pero no puede suponer que el cliente procesará esta información, salvo en el caso de la descarga de datos de mensajes de correo o de los comandos LIST o DELE.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="f0ac2-168">En el último caso, el "argumento" después del comando hace referencia al índice del elemento de correo en el maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="f0ac2-169">**+ERR**: el servidor utiliza esta respuesta para rechazar un comando de cliente.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="f0ac2-170">El servidor puede enviar información adicional después de "-ERR", pero no puede suponer que el cliente procesará esta información.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="f0ac2-171">Sesión de cliente-servidor POP3 de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f0ac2-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="f0ac2-172">**Ejemplo básico de POP3 con USER/PASS:**</span><span class="sxs-lookup"><span data-stu-id="f0ac2-172">**Basic POP3 example using USER/PASS:**</span></span>

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

<span data-ttu-id="f0ac2-173">**Ejemplo básico de POP3 con APOP (y LIST en lugar de STAT):**</span><span class="sxs-lookup"><span data-stu-id="f0ac2-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="f0ac2-174">RFC admitidos por el cliente POP3 de NetX</span><span class="sxs-lookup"><span data-stu-id="f0ac2-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="f0ac2-175">El cliente POP3 de NetX es compatible con RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="f0ac2-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
