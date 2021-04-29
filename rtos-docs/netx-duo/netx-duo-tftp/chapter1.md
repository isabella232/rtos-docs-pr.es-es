---
title: 'Capítulo 1: Introducción a TFTP de Azure RTOS NetX Duo'
description: El protocolo trivial de transferencia de archivos trivial (TFTP) es un protocolo ligero diseñado para las transferencias de archivos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814526"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="79af3-103">Capítulo 1: Introducción a TFTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="79af3-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="79af3-104">El protocolo trivial de transferencia de archivos trivial (TFTP) es un protocolo ligero diseñado para las transferencias de archivos.</span><span class="sxs-lookup"><span data-stu-id="79af3-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="79af3-105">A diferencia de otros protocolos más sólidos, TFTP no realiza una comprobación exhaustiva de errores y puede ofrecer un rendimiento limitado, ya que es un protocolo de detención y espera.</span><span class="sxs-lookup"><span data-stu-id="79af3-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="79af3-106">Después de enviar un paquete de datos TFTP, el remitente espera a que el destinatario devuelva una confirmación.</span><span class="sxs-lookup"><span data-stu-id="79af3-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="79af3-107">Aunque es sencillo, limita el rendimiento general de TFTP.</span><span class="sxs-lookup"><span data-stu-id="79af3-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="79af3-108">El paquete TFTP permite que los hosts usen este protocolo a través de las redes IP.</span><span class="sxs-lookup"><span data-stu-id="79af3-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="79af3-109">Requisitos de TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-109">TFTP Requirements</span></span>

<span data-ttu-id="79af3-110">Para que funcione correctamente, la parte de cliente TFTP del paquete TFTP de NetX Duo requiere que ya se haya creado una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="79af3-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="79af3-111">Además, UDP debe estar habilitado en la misma instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="79af3-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="79af3-112">La parte del cliente del paquete TFTP de NetX Duo no tiene ningún otro requisito.</span><span class="sxs-lookup"><span data-stu-id="79af3-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="79af3-113">La parte del servidor TFTP del paquete TFTP de NetX Duo tiene varios requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="79af3-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="79af3-114">En primer lugar, se necesita acceso completo al *puerto 69 conocido* de UDP para controlar todas las solicitudes TFTP del cliente.</span><span class="sxs-lookup"><span data-stu-id="79af3-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="79af3-115">El servidor TFTP también está diseñado para su uso con el sistema de archivos incrustados FileX.</span><span class="sxs-lookup"><span data-stu-id="79af3-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="79af3-116">Si FileX no está disponible, el usuario puede distribuir las partes de FileX usadas a su propio entorno.</span><span class="sxs-lookup"><span data-stu-id="79af3-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="79af3-117">Esto se describe en secciones posteriores de esta guía.</span><span class="sxs-lookup"><span data-stu-id="79af3-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="79af3-118">Nombres de archivos TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-118">TFTP File Names</span></span> 

<span data-ttu-id="79af3-119">Los nombres de archivos TFTP deben tener el formato del sistema de archivos de destino.</span><span class="sxs-lookup"><span data-stu-id="79af3-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="79af3-120">Deben ser cadenas ASCII terminadas en NULL, con información de ruta de acceso completa si es necesario.</span><span class="sxs-lookup"><span data-stu-id="79af3-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="79af3-121">No hay ningún límite especificado para el tamaño de los nombres de archivos TFTP en la implementación de TFTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="79af3-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="79af3-122">Mensajes TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-122">TFTP Messages</span></span>

<span data-ttu-id="79af3-123">El protocolo TFTP sigue un mecanismo muy sencillo para abrir, leer, escribir y cerrar archivos.</span><span class="sxs-lookup"><span data-stu-id="79af3-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="79af3-124">Básicamente, hay de 2 a 4 bytes de encabezado TFTP bajo el encabezado UDP.</span><span class="sxs-lookup"><span data-stu-id="79af3-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="79af3-125">La definición de los mensajes para abrir archivos TFTP tiene el siguiente formato:</span><span class="sxs-lookup"><span data-stu-id="79af3-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="79af3-126">**oooof…f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="79af3-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="79af3-127">Donde:</span><span class="sxs-lookup"><span data-stu-id="79af3-127">Where:</span></span>

- <span data-ttu-id="79af3-128">**oooo**: campo de código de operación de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="79af3-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="79af3-129">0x0001 -> Apertura para lectura</span><span class="sxs-lookup"><span data-stu-id="79af3-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="79af3-130">0x0002 -> Apertura para escritura</span><span class="sxs-lookup"><span data-stu-id="79af3-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="79af3-131">**f…f**: campo de nombre de archivo de n bytes</span><span class="sxs-lookup"><span data-stu-id="79af3-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="79af3-132">0: carácter de terminación NULL de 1 byte</span><span class="sxs-lookup"><span data-stu-id="79af3-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="79af3-133">**OCTET**: "octeto" ASCII para especificar la transferencia binaria</span><span class="sxs-lookup"><span data-stu-id="79af3-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="79af3-134">0: carácter de terminación NULL de 1 byte</span><span class="sxs-lookup"><span data-stu-id="79af3-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="79af3-135">La definición de los mensajes de escritura, confirmación y error de TFTP es ligeramente diferente y se define de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="79af3-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="79af3-136">**oooobbbbd…d**</span><span class="sxs-lookup"><span data-stu-id="79af3-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="79af3-137">Donde:</span><span class="sxs-lookup"><span data-stu-id="79af3-137">Where:</span></span>

- <span data-ttu-id="79af3-138">**oooo**: campo de código de operación de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="79af3-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="79af3-139">0x0003 -> Paquete de datos</span><span class="sxs-lookup"><span data-stu-id="79af3-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="79af3-140">0x0004 -> Confirmación de última lectura</span><span class="sxs-lookup"><span data-stu-id="79af3-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="79af3-141">0x0005 -> Condición de error</span><span class="sxs-lookup"><span data-stu-id="79af3-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="79af3-142">**bbbb**: campo de número de bloque de 2 bytes (1-n)</span><span class="sxs-lookup"><span data-stu-id="79af3-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="79af3-143">**d…d**: campo de datos de n bytes</span><span class="sxs-lookup"><span data-stu-id="79af3-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="79af3-144">0x0001 (lectura): nombre de archivo 0 octeto 0</span><span class="sxs-lookup"><span data-stu-id="79af3-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="79af3-145">0x0002 (escritura): nombre de archivo 0 octeto 0</span><span class="sxs-lookup"><span data-stu-id="79af3-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="79af3-146">Comunicación TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-146">TFTP Communication</span></span>

<span data-ttu-id="79af3-147">Los servidores TFTP usan el puerto UDP 69 conocido para escuchar las solicitudes de cliente.</span><span class="sxs-lookup"><span data-stu-id="79af3-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="79af3-148">Los sockets del cliente TFTP se pueden enlazar a cualquier puerto UDP disponible.</span><span class="sxs-lookup"><span data-stu-id="79af3-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="79af3-149">La carga del paquete de datos que contiene el archivo que se va a cargar o descargar se envía en fragmentos de 512 bytes, hasta el último paquete que contiene menos de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="79af3-150">Por lo tanto, un paquete que contenga menos de 512 bytes señala el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="79af3-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="79af3-151">La secuencia general de eventos es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="79af3-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="79af3-152">Solicitudes TFTP de lectura de archivos:</span><span class="sxs-lookup"><span data-stu-id="79af3-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="79af3-153">El cliente emite una solicitud de apertura para lectura con el nombre de archivo y espera una respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="79af3-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="79af3-154">El servidor envía los primeros 512 bytes del archivo, o menos si el tamaño del archivo es inferior a 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="79af3-155">El cliente recibe los datos, envía una confirmación y espera el siguiente paquete del servidor en el caso de los archivos que contienen más de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="79af3-156">La secuencia finaliza cuando el cliente recibe un paquete que contiene menos de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="79af3-157">Solicitudes TFTP de escritura:</span><span class="sxs-lookup"><span data-stu-id="79af3-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="79af3-158">El cliente emite una solicitud de apertura para escritura con el nombre de archivo y espera una confirmación con un número de bloque 0 del servidor.</span><span class="sxs-lookup"><span data-stu-id="79af3-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="79af3-159">Cuando el servidor está listo para escribir el archivo, envía una confirmación con un número de bloque cero.</span><span class="sxs-lookup"><span data-stu-id="79af3-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="79af3-160">El cliente envía los primeros 512 bytes del archivo (o menos en el caso de los archivos con un tamaño inferior a 512 bytes) al servidor y espera una confirmación.</span><span class="sxs-lookup"><span data-stu-id="79af3-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="79af3-161">El servidor envía una confirmación después de escribir los bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="79af3-162">La secuencia finaliza cuando el cliente completa la escritura de un paquete que contiene menos de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="79af3-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="79af3-163">Temporizador de sesiones del servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="79af3-164">El servidor TFTP tiene un número limitado de espacios para las solicitudes de cliente.</span><span class="sxs-lookup"><span data-stu-id="79af3-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="79af3-165">Si se anula una sesión de cliente, ese espacio no se podrá reutilizar.</span><span class="sxs-lookup"><span data-stu-id="79af3-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="79af3-166">Sin embargo, si se habilita la opción NX_TFTP_SERVER_RETRANSMIT_ENABLE, el servidor TFTP de NetX Duo crea un temporizador de sesión que supervisa el tiempo de espera de cada una de sus sesiones de cliente.</span><span class="sxs-lookup"><span data-stu-id="79af3-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="79af3-167">Cuando expira el tiempo de espera de una sesión, se termina y se cierran los archivos abiertos.</span><span class="sxs-lookup"><span data-stu-id="79af3-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="79af3-168">De este modo, el espacio pasa a estar disponible para otra solicitud del cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="79af3-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="79af3-169">Para establecer el tiempo de espera, ajuste la opción de configuración NX_TFTP_SERVER_RETRANSMIT_TIMEOUT que, de forma predeterminada, se establece en 200 tics del temporizador.</span><span class="sxs-lookup"><span data-stu-id="79af3-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="79af3-170">El intervalo con el que se comprueban los tiempos de espera de la sesión se establece mediante la opción NX_TFTP_SERVER_TIMEOUT_PERIOD; su valor predeterminado es de 20 tics del temporizador.</span><span class="sxs-lookup"><span data-stu-id="79af3-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="79af3-171">Cuando el cliente TFTP ha cargado (escrito) archivos en el soporte FileX de TFTP, es necesario vaciar el soporte para que los datos se puedan escribir desde el disco RAM del servidor TFTP en el soporte subyacente (memoria del disco del cliente TFTP).</span><span class="sxs-lookup"><span data-stu-id="79af3-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="79af3-172">Esto puede hacerse mediante el servicio fx_media_flush si la aplicación no desea cerrar el servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="79af3-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="79af3-173">Sin embargo, después de cerrar el servidor TFTP, la aplicación debe cerrar el soporte FileX con el servicio fx_media_close si ya no va a usarlo.</span><span class="sxs-lookup"><span data-stu-id="79af3-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="79af3-174">Esto hará que los datos de los archivos se vacíen en el disco del cliente TFTP, se cierren los archivos abiertos y se actualice la información del directorio en el soporte.</span><span class="sxs-lookup"><span data-stu-id="79af3-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="79af3-175">Se puede ver una demostración en la sección "Sistema de ejemplo pequeño" de esta guía.</span><span class="sxs-lookup"><span data-stu-id="79af3-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="79af3-176">Una tercera opción para actualizar el soporte FileX es compilar la biblioteca de FileX con las opciones FX_FAULT_TOLERANT o FX_FAULT_TOLERANT_DATA en lugar de usar los servicios de FileX explícitamente.</span><span class="sxs-lookup"><span data-stu-id="79af3-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="79af3-177">En este caso, FileX pasa automáticamente las solicitudes de escritura al controlador del soporte.</span><span class="sxs-lookup"><span data-stu-id="79af3-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="79af3-178">Estas opciones pueden limitar el rendimiento pero ofrecen una mayor protección ante la pérdida de datos de archivo o de clústeres.</span><span class="sxs-lookup"><span data-stu-id="79af3-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="79af3-179">Para obtener más información sobre esta cuestión y sobre FileX en general, consulte el manual del usuario de FileX de Express Logic.</span><span class="sxs-lookup"><span data-stu-id="79af3-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="79af3-180">Compatibilidad con varios subprocesos TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="79af3-181">Se puede llamar a los servicios del cliente TFTP de NetX Duo desde varios subprocesos simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="79af3-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="79af3-182">Sin embargo, las solicitudes de lectura o escritura de una determinada instancia del cliente TFTP deben realizarse consecutivamente desde el mismo subproceso.</span><span class="sxs-lookup"><span data-stu-id="79af3-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="79af3-183">Publicaciones RFC para TFTP</span><span class="sxs-lookup"><span data-stu-id="79af3-183">TFTP RFCs</span></span>

<span data-ttu-id="79af3-184">TFTP de NetX Duo es compatible con la RFC1350 y las RFC relacionadas.</span><span class="sxs-lookup"><span data-stu-id="79af3-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

