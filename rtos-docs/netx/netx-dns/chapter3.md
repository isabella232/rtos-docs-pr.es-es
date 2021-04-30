---
title: 'Capítulo 3: Descripción de los servicios del cliente DNS de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815221"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="381f0-103">Capítulo 3: Descripción de los servicios del cliente DNS de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="381f0-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="381f0-104">Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="381f0-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="381f0-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="381f0-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="381f0-106">**nx_dns_authority_zone_start_get**: *permite buscar el inicio de una zona de autoridad asociada con el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="381f0-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="381f0-107">**nx_dns_cache_initialize**: *permite inicializar una caché de DNS.*</span><span class="sxs-lookup"><span data-stu-id="381f0-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="381f0-108">**nx_dns_cache_notify_clear**: *permite borrar la función de notificación completa de la memoria caché.*</span><span class="sxs-lookup"><span data-stu-id="381f0-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="381f0-109">**nx_dns_cache_notify_set**: *permite establecer la función de notificación completa de la memoria caché.*</span><span class="sxs-lookup"><span data-stu-id="381f0-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="381f0-110">**nx_dns_cname_get**: *permite buscar el nombre de dominio canónico para el alias de nombre de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="381f0-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="381f0-111">**nx_dns_create**: *permite crear una instancia de cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="381f0-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="381f0-112">**nx_dns_delete**: *permite eliminar una instancia de cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="381f0-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="381f0-113">**nx_dns_domain_name_server_get**: *permite buscar los servidores de nombres autoritativos para la zona de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="381f0-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="381f0-114">**nx_dns_domain_mail_exchange_get**: *permite buscar el intercambio de correo asociado al nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="381f0-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="381f0-115">**nx_dns_domain_service_get**: *permite buscar los servicios asociados con el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="381f0-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="381f0-116">**nx_dns_get_serverlist_size**: *permite devolver el tamaño de la lista de servidores del cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="381f0-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="381f0-117">**nx_dns_info_by_name_get**: *permite devolver la dirección IP y la consulta de puertos en el nombre de host de entrada.*</span><span class="sxs-lookup"><span data-stu-id="381f0-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="381f0-118">**nx_dns_ipv4_address_by_name_get**: *permite buscar la dirección IPv4 desde el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="381f0-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="381f0-119">**nx_dns_host_by_address_get**: *permite buscar un nombre de host desde una dirección IP especificada.*</span><span class="sxs-lookup"><span data-stu-id="381f0-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="381f0-120">**nx_dns_host_by_name_get**: *permite buscar la dirección IPv4 desde el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="381f0-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="381f0-121">**nx_dns_host_text_get**: *permite buscar los datos de texto para el nombre de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="381f0-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="381f0-122">**nx_dns_packet_pool_set**: *permite establecer el grupo de paquetes del cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="381f0-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="381f0-123">**nx_dns_server_add**: *permite agregar un servidor DNS en la dirección especificada a la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="381f0-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="381f0-124">**nx_dns_server_get**: *permite devolver el servidor DNS en la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="381f0-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="381f0-125">**nx_dns_server_remove**: *permite quitar un servidor DNS de la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="381f0-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="381f0-126">**nx_dns_server_remove_all**: *permite quitar todos los servidores DNS de la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="381f0-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="381f0-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="381f0-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="381f0-128">Búsqueda del inicio de la zona de autoridad del host de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-129">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="381f0-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-130">Description</span></span>

<span data-ttu-id="381f0-131">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SOA con el nombre de dominio especificado para obtener el inicio de la zona de autoridad para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="381f0-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="381f0-132">El cliente DNS copia los registros SOA devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="381f0-133">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="381f0-134">En el cliente DNS de NetX, el tipo de registro SOA, NX_DNS_SOA_ENTRY, se guarda como siete parámetros de 4 bytes, que suman un total de 28 bytes:</span><span class="sxs-lookup"><span data-stu-id="381f0-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="381f0-135">**nx_dns_soa_host_mname_ptr**: puntero al origen de datos principal para esta zona.</span><span class="sxs-lookup"><span data-stu-id="381f0-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="381f0-136">**nx_dns_soa_host_rname_ptr**: puntero al responsable del buzón para esta zona.</span><span class="sxs-lookup"><span data-stu-id="381f0-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="381f0-137">**nx_dns_soa_serial**: número de versión de zona.</span><span class="sxs-lookup"><span data-stu-id="381f0-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="381f0-138">**nx_dns_soa_refresh**: intervalo de actualización.</span><span class="sxs-lookup"><span data-stu-id="381f0-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="381f0-139">**nx_dns_soa_retry**: intervalo entre reintentos de consultas SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="381f0-140">**nx_dns_soa_expire**: duración del tiempo de expiración de SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="381f0-141">**nx_dns_soa_minmum**: campo TTL mínimo en los mensajes de respuesta DNS del nombre de host SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="381f0-142">A continuación se muestra el almacenamiento de dos registros SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="381f0-143">Los registros SOA que contienen datos de longitud fija se introducen empezando por la parte superior del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="381f0-144">Los punteros MNAME y RNAME apuntan a los datos de longitud variable (nombres de host) que se almacenan en la parte inferior del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="381f0-145">Los registros SOA adicionales se escriben después del primer registro ("registros SOA adicionales…") y sus datos de longitud variable se almacenan encima de los datos de longitud variable de la última entrada ("datos de longitud variable de SOA adicionales"):</span><span class="sxs-lookup"><span data-stu-id="381f0-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Diagrama que representa el almacenamiento de dos registros SOA](media/image2.png)

<span data-ttu-id="381f0-147">Si la ubicación *record_buffer* de entrada no puede contener todos los datos SOA de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="381f0-148">Con el número de registros SOA devueltos en \**record_count,* la aplicación puede analizar los datos de *record_buffer* y extraer el inicio de las cadenas de nombre de host de la entidad de zona.</span><span class="sxs-lookup"><span data-stu-id="381f0-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-149">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-149">Input Parameters</span></span>

- <span data-ttu-id="381f0-150">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-151">**host_name**: puntero al nombre de host para el que se van a obtener datos SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="381f0-152">**record_buffer**: puntero a la ubicación en la que se van a extraer datos SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="381f0-153">**buffer_size**: tamaño del búfer que contendrá datos SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="381f0-154">**record_count**: puntero al número de registros SOA recuperados.</span><span class="sxs-lookup"><span data-stu-id="381f0-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="381f0-155">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-156">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-156">Return Values</span></span>

- <span data-ttu-id="381f0-157">**NX_SUCCESS** (0x00): los datos SOA se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="381f0-158">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-159">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-160">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-161">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="381f0-162">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-163">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-163">Allowed From</span></span>

<span data-ttu-id="381f0-164">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-165">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-165">Example</span></span>
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

/* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    
    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="381f0-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="381f0-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="381f0-167">Inicialización de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-168">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="381f0-169">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-169">Description</span></span>

<span data-ttu-id="381f0-170">Este servicio crea e inicializa una caché de DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-171">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-171">Input Parameters</span></span>

- <span data-ttu-id="381f0-172">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="381f0-173">**cache_ptr**: puntero a la caché de DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="381f0-174">**cache_size**: tamaño de la caché de DNS, en bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-175">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-175">Return Values</span></span>

- <span data-ttu-id="381f0-176">**NX_SUCCESS** (0x00): la caché de DNS se inicializó correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="381f0-177">NX_DNS_ERROR (0xA0): la caché no es alineada de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="381f0-178">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-179">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="381f0-180">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-181">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-181">Allowed From</span></span>

<span data-ttu-id="381f0-182">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-183">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="381f0-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="381f0-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="381f0-185">Borrado de la función de notificación completa de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-186">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="381f0-187">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-187">Description</span></span>

<span data-ttu-id="381f0-188">Este servicio borra la función de notificación completa de la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="381f0-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-189">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-189">Input Parameters</span></span>

- <span data-ttu-id="381f0-190">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-191">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-191">Return Values</span></span>

- <span data-ttu-id="381f0-192">**NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="381f0-193">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-194">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-195">Allowed From</span></span>

<span data-ttu-id="381f0-196">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-197">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="381f0-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="381f0-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="381f0-199">Establecimiento de la función de notificación completa de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="381f0-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-201">Description</span></span>

<span data-ttu-id="381f0-202">Este servicio establece la función de notificación completa de la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="381f0-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-203">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-203">Input Parameters</span></span>

- <span data-ttu-id="381f0-204">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="381f0-205">**cache_full_notify_cb**: función de devolución de llamada que se va a invocar cuando la memoria caché se llene.</span><span class="sxs-lookup"><span data-stu-id="381f0-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-206">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-206">Return Values</span></span>

- <span data-ttu-id="381f0-207">**NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="381f0-208">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-209">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-210">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-210">Allowed From</span></span>

<span data-ttu-id="381f0-211">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-212">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="381f0-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="381f0-213">nx_dns_cname_get</span></span>

<span data-ttu-id="381f0-214">Búsqueda del nombre canónico del nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-215">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-216">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-216">Description</span></span>

<span data-ttu-id="381f0-217">Si NX_DNS_ENABLE_EXTENDED_RR_TYPES se define en *nxd_dns.h*, este servicio envía una consulta de tipo CNAME con el nombre de dominio especificado para obtener el nombre de dominio canónico.</span><span class="sxs-lookup"><span data-stu-id="381f0-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="381f0-218">El cliente DNS copia la cadena CNAME devuelta en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-219">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-219">Input Parameters</span></span>

- <span data-ttu-id="381f0-220">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-221">**host_name**: puntero al nombre de host para el que se van a obtener datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="381f0-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="381f0-222">**record_buffer**: puntero a la ubicación en la que se van a extraer datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="381f0-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="381f0-223">**buffer_size**: tamaño del búfer que contendrá datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="381f0-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="381f0-224">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-225">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-225">Return Values</span></span>

- <span data-ttu-id="381f0-226">**NX_SUCCESS** (0x00): los datos CNAME se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="381f0-227">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-228">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-229">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-230">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="381f0-231">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-232">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-232">Allowed From</span></span>

<span data-ttu-id="381f0-233">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-234">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-234">Example</span></span>

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a><span data-ttu-id="381f0-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="381f0-235">nx_dns_create</span></span>

<span data-ttu-id="381f0-236">Creación de una instancia de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-237">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="381f0-238">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-238">Description</span></span>

<span data-ttu-id="381f0-239">Este servicio crea una instancia de cliente DNS para la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="381f0-240">La aplicación debe asegurarse de que la carga de paquetes del grupo de paquetes utilizada por el cliente DNS es lo suficientemente grande para el mensaje DNS máximo de 512 bytes, más los encabezados UDP, IP y Ethernet.</span><span class="sxs-lookup"><span data-stu-id="381f0-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="381f0-241">Si el cliente DNS crea su propio grupo de paquetes, se define mediante NX_DNS_PACKET_POOL_SIZE y NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="381f0-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="381f0-242">Si la aplicación cliente DNS prefiere proporcionar un grupo de paquetes creado previamente, la carga para el cliente DNS IPv4 debe ser de 512 bytes para el DNS máximo más 20 bytes para el encabezado IP, 8 bytes para el encabezado UDP y 14 bytes para el encabezado Ethernet.</span><span class="sxs-lookup"><span data-stu-id="381f0-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-243">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-243">Input Parameters</span></span>

- <span data-ttu-id="381f0-244">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-245">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="381f0-246">**domain_name**: puntero al nombre de dominio para la instancia DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-247">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-247">Return Values</span></span>

- <span data-ttu-id="381f0-248">**NX_SUCCESS** (0x00): DNS creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="381f0-249">**NX_DNS_ERROR** (0xA0): error de creación de DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="381f0-250">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-251">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-252">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-252">Allowed From</span></span>

<span data-ttu-id="381f0-253">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-254">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="381f0-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="381f0-255">nx_dns_delete</span></span>

<span data-ttu-id="381f0-256">Eliminación de una instancia de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-257">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="381f0-258">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-258">Description</span></span>

<span data-ttu-id="381f0-259">Este servicio elimina una instancia de cliente DNS creada anteriormente y libera sus recursos.</span><span class="sxs-lookup"><span data-stu-id="381f0-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="381f0-260">Si se define **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** y se asignó al cliente DNS un grupo de paquetes definido por el usuario, depende de la aplicación que se elimine el grupo de paquetes del cliente DNS si ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="381f0-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-261">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-261">Input Parameters</span></span>

- <span data-ttu-id="381f0-262">**dns_ptr**: puntero a la instancia de **cliente** DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-263">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-263">Return Values</span></span>

- <span data-ttu-id="381f0-264">**NX_SUCCESS** (0x00): cliente DNS eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="381f0-265">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="381f0-266">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-267">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-267">Allowed From</span></span>

<span data-ttu-id="381f0-268">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-269">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="381f0-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="381f0-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="381f0-271">Búsqueda de los servidores de nombres autoritativos para la zona de dominio de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-272">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-273">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-273">Description</span></span>

<span data-ttu-id="381f0-274">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo NS con el nombre de dominio especificado para obtener los servidores de nombres para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="381f0-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="381f0-275">El cliente DNS copia los registros NS devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="381f0-276">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="381f0-277">En el cliente DNS de NetX, el tipo de datos NS, NX_DNS_NS_ENTRY, se guarda como dos parámetros de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="381f0-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="381f0-278">**nx_dns_ns_ipv4_address**: dirección IPv4 del servidor de nombres.</span><span class="sxs-lookup"><span data-stu-id="381f0-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="381f0-279">**nx_dns_ns_hostname_ptr**: puntero al nombre de host del servidor de nombres.</span><span class="sxs-lookup"><span data-stu-id="381f0-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="381f0-280">El búfer que se muestra a continuación contiene cuatro registros NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="381f0-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="381f0-281">El puntero a la cadena de nombre de host en cada entrada apunta a la cadena de nombre de host correspondiente en la mitad inferior del búfer:</span><span class="sxs-lookup"><span data-stu-id="381f0-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Diagrama del búfer que contiene cuatro registros de entrada N X D N S N S.](media/image3.png)

<span data-ttu-id="381f0-283">Si la ubicación *record_buffer* de entrada no puede contener todos los datos NS de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="381f0-284">Con el número de registros NS devueltos en \**record_count,* la aplicación puede analizar la dirección IP y el nombre de host de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-285">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-285">Input Parameters</span></span>

- <span data-ttu-id="381f0-286">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-287">**host_name**: puntero al nombre de host para el que se van a obtener datos NS.</span><span class="sxs-lookup"><span data-stu-id="381f0-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="381f0-288">**record_buffer**: puntero a la ubicación en la que se van a extraer datos NS.</span><span class="sxs-lookup"><span data-stu-id="381f0-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="381f0-289">**buffer_size**: tamaño del búfer que contendrá datos NS.</span><span class="sxs-lookup"><span data-stu-id="381f0-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="381f0-290">**record_count**: puntero al número de registros NS recuperados.</span><span class="sxs-lookup"><span data-stu-id="381f0-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="381f0-291">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-292">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-292">Return Values</span></span>

- <span data-ttu-id="381f0-293">**NX_SUCCESS** (0x00): los datos NS se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="381f0-294">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-295">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-296">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-297">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-298">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-299">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-299">Allowed From</span></span>

<span data-ttu-id="381f0-300">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-301">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-301">Example</span></span>
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        }
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="381f0-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="381f0-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="381f0-303">Búsqueda de los intercambios de correo para el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-304">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="381f0-305">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-305">Description</span></span>

<span data-ttu-id="381f0-306">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo MX con el nombre de dominio especificado para obtener el intercambio de correo para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="381f0-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="381f0-307">El cliente DNS copia los registros MX devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="381f0-308">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="381f0-309">En el cliente DNS de NetX, el tipo de registro de intercambio de correo, NX_DNS_MAIL_EXCHANGE_ENTRY, se guarda como cuatro parámetros que suman un total de 12 bytes:</span><span class="sxs-lookup"><span data-stu-id="381f0-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="381f0-310">**nx_dns_mx_ipv4_address**: dirección IPv4 de intercambio de correo de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="381f0-311">**nx_dns_mx_preference**: preferencia de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="381f0-312">**nx_dns_mx_reserved0**: 2 bytes reservados.</span><span class="sxs-lookup"><span data-stu-id="381f0-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="381f0-313">**nx_dns_mx_hostname_ptr**: puntero al nombre de host del servidor de intercambio de correo de 4 bytes</span><span class="sxs-lookup"><span data-stu-id="381f0-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="381f0-314">A continuación se muestra un búfer que contiene cuatro registros MX.</span><span class="sxs-lookup"><span data-stu-id="381f0-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="381f0-315">Cada registro contiene los datos de longitud fija de la lista anterior.</span><span class="sxs-lookup"><span data-stu-id="381f0-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="381f0-316">El puntero al nombre de host del servidor de intercambio de correo apunta al nombre de host correspondiente en la parte inferior del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Diagrama que muestra el búfer que contiene cuatro registros M X.](media/image4.png)

<span data-ttu-id="381f0-318">Si la ubicación *record_buffer* de entrada no puede contener todos los datos MX de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="381f0-319">Con el número de registros MX devueltos en \**record_count,* la aplicación puede analizar los parámetros MX, incluido el nombre de host de correo de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-320">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-320">Input Parameters</span></span>

- <span data-ttu-id="381f0-321">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-322">**host_name**: puntero al nombre de host para el que se van a obtener datos SOA.</span><span class="sxs-lookup"><span data-stu-id="381f0-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="381f0-323">**record_buffer**: puntero a la ubicación en la que se van a extraer datos MX.</span><span class="sxs-lookup"><span data-stu-id="381f0-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="381f0-324">**buffer_size**: tamaño del búfer que contendrá datos MX.</span><span class="sxs-lookup"><span data-stu-id="381f0-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="381f0-325">**record_count**: puntero al número de registros MX recuperados.</span><span class="sxs-lookup"><span data-stu-id="381f0-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="381f0-326">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-327">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-327">Return Values</span></span>

- <span data-ttu-id="381f0-328">**NX_SUCCESS** (0x00): los datos MX se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="381f0-329">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-330">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-331">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-332">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-333">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-334">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-334">Allowed From</span></span>

<span data-ttu-id="381f0-335">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-336">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-336">Example</span></span>
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="381f0-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="381f0-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="381f0-338">Búsqueda de los servicios proporcionados por el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-339">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-340">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-340">Description</span></span>

<span data-ttu-id="381f0-341">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SRV con el nombre de dominio especificado para buscar los servicios y su número de puerto asociado con el dominio especificado.</span><span class="sxs-lookup"><span data-stu-id="381f0-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="381f0-342">El cliente DNS copia los registros SRV devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="381f0-343">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="381f0-344">En el cliente DNS de NetX, el tipo de registro del servicio, NX_DNS_SRV_ENTRY, se guarda como seis parámetros que suman un total de 16 bytes:</span><span class="sxs-lookup"><span data-stu-id="381f0-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="381f0-345">Esto permite almacenar datos SRV de longitud variable de manera eficaz para la memoria:</span><span class="sxs-lookup"><span data-stu-id="381f0-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="381f0-346">**Dirección IPv4 del servidor**: nx_dns_srv_ipv4_address de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="381f0-347">**Prioridad del servidor**: nx_dns_srv_priority de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="381f0-348">**Peso del servidor**: nx_dns_srv_weight de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="381f0-349">**Número de puerto de servicio**: nx_dns_srv_port_number de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="381f0-350">**Reservado para la alineación de 4 bytes**: nx_dns_srv_reserved0 de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="381f0-351">**Puntero al nombre de host del servidor**: \*nx_dns_srv_hostname_ptr de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="381f0-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="381f0-352">Se almacenan cuatro registros SRV en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="381f0-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="381f0-353">Cada registro de NX_DNS_SRV_ENTRY contiene un puntero, *nx_dns_srv_hostname_ptr*, que apunta a la cadena de nombre de host correspondiente en la parte inferior del búfer de registro:</span><span class="sxs-lookup"><span data-stu-id="381f0-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Diagrama de cuatro registros S R V almacenados en el búfer proporcionado.](media/image5.png)

<span data-ttu-id="381f0-355">Si la ubicación *record_buffer* de entrada no puede contener todos los datos SRV de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="381f0-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="381f0-356">Con el número de registros SRV devueltos en \**record_count,* la aplicación puede analizar los parámetros SRV, incluido el nombre de host del servidor de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-357">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-357">Input Parameters</span></span>

- <span data-ttu-id="381f0-358">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-359">**host_name**: puntero al nombre de host para el que se van a obtener datos SRV.</span><span class="sxs-lookup"><span data-stu-id="381f0-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="381f0-360">**record_buffer**: puntero a la ubicación en la que se van a extraer datos SRV.</span><span class="sxs-lookup"><span data-stu-id="381f0-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="381f0-361">**buffer_size**: tamaño del búfer que contendrá datos SRV.</span><span class="sxs-lookup"><span data-stu-id="381f0-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="381f0-362">**record_count**: puntero al número de registros SRV recuperados.</span><span class="sxs-lookup"><span data-stu-id="381f0-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="381f0-363">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-364">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-364">Return Values</span></span>

- <span data-ttu-id="381f0-365">**NX_SUCCESS** (0x00): los datos SRV se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="381f0-366">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-367">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-368">NX_DNS_PARAM_ERROR (0xA8): ID de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="381f0-369">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-370">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-371">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-371">Allowed From</span></span>

<span data-ttu-id="381f0-372">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-373">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-373">Example</span></span>

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

       printf("port number = %d\n", 
               nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
               printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
       printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

       if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
       {
            printf("hostname = %s\n", 
            nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        }
       else
            printf("hostname is not set\n");
    }
}
```

```Output
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="381f0-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="381f0-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="381f0-375">Devolución del tamaño de la lista de servidores del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-376">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="381f0-377">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-377">Description</span></span>

<span data-ttu-id="381f0-378">Este servicio devuelve el número de servidores DNS válidos en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="381f0-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-379">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-379">Input Parameters</span></span>

- <span data-ttu-id="381f0-380">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="381f0-381">**size**: devuelve el número de servidores de la lista.</span><span class="sxs-lookup"><span data-stu-id="381f0-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-382">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-382">Return Values</span></span>

- <span data-ttu-id="381f0-383">**NX_SUCCESS** (0x00): el tamaño de la lista de servidores DNS se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="381f0-384">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="381f0-385">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-386">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-386">Allowed From</span></span>

<span data-ttu-id="381f0-387">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-388">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="381f0-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="381f0-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="381f0-390">Devolución de la dirección IP y el puerto del servidor DNS por nombre de host</span><span class="sxs-lookup"><span data-stu-id="381f0-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-391">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-392">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-392">Description</span></span>

<span data-ttu-id="381f0-393">Este servicio devuelve la dirección IP del servidor y el puerto (registro de servicio) basados en el nombre de host de entrada mediante la consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="381f0-394">Si no se encuentra un registro de servicio, esta rutina devuelve una dirección IP cero en el puntero de la dirección de entrada y una devolución de estado de error distinto de cero para indicar un error.</span><span class="sxs-lookup"><span data-stu-id="381f0-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-395">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-395">Input Parameters</span></span>

- <span data-ttu-id="381f0-396">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="381f0-397">**host_name**: puntero al búfer de nombre de host.</span><span class="sxs-lookup"><span data-stu-id="381f0-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="381f0-398">**host_address_ptr**: puntero a la dirección que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="381f0-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="381f0-399">**host_port_ptr**: puntero a puerto para devolver la opción de espera wait_option para la respuesta DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-400">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-400">Return Values</span></span>

- <span data-ttu-id="381f0-401">**NX_SUCCESS** (0x00): el registro del servidor DNS se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="381f0-402">**NX_DNS_NO_SERVER** (0XA1): no hay ningún servidor DNS registrado en el cliente para enviar la consulta en el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="381f0-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="381f0-403">**NX_DNS_QUERY_FAILED** (0xA3): error de la consulta de DNS; no hay ninguna respuesta de ningún servidor DNS en la lista del cliente o no existe ningún registro de servicio disponible para el nombre de host de entrada.</span><span class="sxs-lookup"><span data-stu-id="381f0-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="381f0-404">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-405">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-406">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-406">Allowed From</span></span>

<span data-ttu-id="381f0-407">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-408">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="381f0-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="381f0-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="381f0-410">Búsqueda de la dirección IPv4 para el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-411">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-412">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-412">Description</span></span>

<span data-ttu-id="381f0-413">Este servicio envía una consulta de tipo A con el nombre de host especificado para obtener las direcciones IP para el nombre de host de entrada.</span><span class="sxs-lookup"><span data-stu-id="381f0-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="381f0-414">El cliente DNS copia la dirección IPv4 de los registros A devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="381f0-415">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="381f0-416">Varias direcciones IPv4 se almacenan en el búfer alineado de 4 bytes, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="381f0-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Diagrama de varias direcciones I P v 4 que se almacenan en el búfer alineado de 4 bytes.](media/image6.png)

<span data-ttu-id="381f0-418">Si el búfer proporcionado no puede contener todos los datos de las direcciones IP, los registros A restantes no se almacenan en *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="381f0-419">Esto permite que la aplicación recupere uno, algunos o todos los datos de direcciones IP disponibles en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="381f0-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="381f0-420">Con el número de registros A devueltos en \**record_count*, la aplicación puede analizar los datos de dirección IPv4 desde la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-421">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-421">Input Parameters</span></span>

- <span data-ttu-id="381f0-422">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-423">**host_name_ptr**: puntero al nombre de host para obtener el puntero de búfer de dirección IPv4 a la ubicación en la que se van a extraer los datos IPv4.</span><span class="sxs-lookup"><span data-stu-id="381f0-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="381f0-424">**buffer_size**: tamaño del búfer que contendrá datos IPv4.</span><span class="sxs-lookup"><span data-stu-id="381f0-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="381f0-425">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-426">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-426">Return Values</span></span>

- <span data-ttu-id="381f0-427">**NX_SUCCESS** (0x00): los datos IPv4 se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="381f0-428">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-429">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-430">NX_DNS_PARAM_ERROR (0xA8): parámetro de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="381f0-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="381f0-431">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="381f0-432">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-433">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-433">Allowed From</span></span>

<span data-ttu-id="381f0-434">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-435">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-435">Example</span></span>

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }
}
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="381f0-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="381f0-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="381f0-437">Búsqueda de un nombre de host desde una dirección IP</span><span class="sxs-lookup"><span data-stu-id="381f0-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-438">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-439">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-439">Description</span></span>

<span data-ttu-id="381f0-440">Este servicio solicita la resolución de nombres de la dirección IP suministrada de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="381f0-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="381f0-441">Si la operación se realiza correctamente, se devuelve el nombre de host terminado en NULL en la cadena especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="381f0-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-442">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-442">Input Parameters</span></span>

- <span data-ttu-id="381f0-443">**dns_ptr**: puntero a la instancia de DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="381f0-444">**ip_address**: dirección IP que se va a resolver en un nombre.</span><span class="sxs-lookup"><span data-stu-id="381f0-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="381f0-445">**host_name_ptr**: puntero al área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="381f0-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="381f0-446">**max_host_name_size**: tamaño del área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="381f0-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="381f0-447">**wait_option**: define cuánto tiempo esperará el servicio en tics de temporizador para una respuesta del servidor DNS después de cada consulta de DNS y reintento de consulta. Las opciones de espera se definen como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="381f0-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="381f0-448">**timeout value** (0x00000001-0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la resolución DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="381f0-449">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende de manera indefinida hasta que el servidor DNS responde la solicitud.</span><span class="sxs-lookup"><span data-stu-id="381f0-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-450">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-450">Return Values</span></span>

- <span data-ttu-id="381f0-451">**NX_SUCCESS** (0x00): resolución DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="381f0-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="381f0-452">**NX_DNS_TIMEOUT** (0xA2): se agotó el tiempo de espera al obtener la exclusión mutua de DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="381f0-453">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="381f0-454">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="381f0-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="381f0-455">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.</span><span class="sxs-lookup"><span data-stu-id="381f0-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="381f0-456">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="381f0-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="381f0-457">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="381f0-458">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="381f0-459">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-460">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-460">Allowed From</span></span>

<span data-ttu-id="381f0-461">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-462">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="381f0-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="381f0-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="381f0-464">Búsqueda de una dirección IP desde el nombre de host</span><span class="sxs-lookup"><span data-stu-id="381f0-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-465">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-466">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-466">Description</span></span>

<span data-ttu-id="381f0-467">Este servicio solicita la resolución de nombres del nombre suministrado, al que apunta *host_name*, de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="381f0-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="381f0-468">Si la operación se realiza correctamente, se devuelve la dirección IP asociada en el destino al que apunta *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="381f0-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-469">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-469">Input Parameters</span></span>

- <span data-ttu-id="381f0-470">**dns_ptr**: puntero a la instancia de DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="381f0-471">**host_name**: puntero al nombre de host.</span><span class="sxs-lookup"><span data-stu-id="381f0-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="381f0-472">**host_address_ptr**: puntero a la dirección IP del host DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="381f0-473">**wait_option**: define cuánto tiempo esperará el servicio para la resolución DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="381f0-474">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="381f0-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="381f0-475">**timeout value** (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la resolución DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="381f0-476">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende de manera indefinida hasta que el servidor DNS responde la solicitud.</span><span class="sxs-lookup"><span data-stu-id="381f0-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-477">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-477">Return Values</span></span>

- <span data-ttu-id="381f0-478">**NX_SUCCESS** (0x00): resolución DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="381f0-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="381f0-479">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="381f0-480">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="381f0-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="381f0-481">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="381f0-482">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="381f0-483">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-484">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-484">Allowed From</span></span>

<span data-ttu-id="381f0-485">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-486">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-486">Example</span></span>
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="381f0-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="381f0-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="381f0-488">Búsqueda de la cadena de texto para el nombre de dominio de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-489">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="381f0-490">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-490">Description</span></span>

<span data-ttu-id="381f0-491">Este servicio envía una consulta de tipo TXT con el nombre de dominio y el búfer especificados para obtener los datos de cadena arbitrarios.</span><span class="sxs-lookup"><span data-stu-id="381f0-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="381f0-492">El cliente DNS copia la cadena de texto del registro TXT de la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="381f0-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="381f0-493">La ubicación *record_buffer* no necesita tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="381f0-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-494">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-494">Input Parameters</span></span>

- <span data-ttu-id="381f0-495">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="381f0-496">**host_name**: puntero al nombre del host en el que se realizará la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="381f0-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="381f0-497">**record_buffer**: puntero a la ubicación en la que se van a extraer datos TXT.</span><span class="sxs-lookup"><span data-stu-id="381f0-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="381f0-498">**buffer_size**: tamaño del búfer que contendrá datos TXT.</span><span class="sxs-lookup"><span data-stu-id="381f0-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="381f0-499">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-500">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-500">Return Values</span></span>

- <span data-ttu-id="381f0-501">**NX_SUCCESS** (0x00): se obtuvo correctamente la cadena TXT.</span><span class="sxs-lookup"><span data-stu-id="381f0-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="381f0-502">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="381f0-503">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="381f0-504">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="381f0-505">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="381f0-506">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-507">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-507">Allowed From</span></span>

<span data-ttu-id="381f0-508">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-509">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-509">Example</span></span>

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="381f0-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="381f0-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="381f0-511">Establecimiento del grupo de paquetes del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-512">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="381f0-513">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-513">Description</span></span>

<span data-ttu-id="381f0-514">Este servicio establece un grupo de paquetes creado anteriormente como el grupo de paquetes del **cliente** DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="381f0-515">El cliente DNS usará este grupo de paquetes para enviar consultas de DNS, por lo que la carga de paquetes no debe ser inferior al valor de NX_DNS_PACKET_PAYLOAD_UNALIGNED, que incluye los encabezados Marco Ethernet, IP y UDP, y se define en *nxd_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="381f0-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="381f0-516">Cuando se elimina el cliente DNS, el grupo de paquetes no se elimina con este y es responsabilidad de la aplicación eliminarlo cuando ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="381f0-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="381f0-517">Este servicio solo está disponible si la opción de configuración NX_DNS_CLIENT_USER_CREATE_PACKET_POOL se define en *nx_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="381f0-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-518">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-518">Input Parameters</span></span>

- <span data-ttu-id="381f0-519">**dns_ptr**: puntero a la instancia de **cliente** DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="381f0-520">**pool_ptr**: puntero a un grupo de paquetes creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="381f0-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-521">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-521">Return Values</span></span>

- <span data-ttu-id="381f0-522">**NX_SUCCESS** (0x00): operación finalizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="381f0-523">**NX_NOT_ENABLED** (0x14): cliente no configurado para esta opción.</span><span class="sxs-lookup"><span data-stu-id="381f0-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="381f0-524">NX_PTR_ERROR (0X07): puntero de **cliente** DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="381f0-525">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-526">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-526">Allowed From</span></span>

<span data-ttu-id="381f0-527">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-528">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-528">Example</span></span>
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="381f0-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="381f0-529">nx_dns_server_add</span></span>

<span data-ttu-id="381f0-530">Incorporación de dirección IP del servidor DNS</span><span class="sxs-lookup"><span data-stu-id="381f0-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-531">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="381f0-532">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-532">Description</span></span>

<span data-ttu-id="381f0-533">Este servicio agrega un servidor DNS IPv4 a la lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="381f0-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-534">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-534">Input Parameters</span></span>

- <span data-ttu-id="381f0-535">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="381f0-536">**server_address**: dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-537">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-537">Return Values</span></span>

- <span data-ttu-id="381f0-538">**NX_SUCCESS** (0x00): servidor agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="381f0-539">**NX_DNS_DUPLICATE_ENTRY** o **NX_NO_MORE_ENTRIES** (0x17): no se permiten más servidores DNS (la lista está llena).</span><span class="sxs-lookup"><span data-stu-id="381f0-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="381f0-540">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="381f0-541">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="381f0-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="381f0-542">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="381f0-543">NX_DNS_BAD_ADDRESS_ERROR (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="381f0-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-544">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-544">Allowed From</span></span>

<span data-ttu-id="381f0-545">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-546">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="381f0-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="381f0-547">nx_dns_server_get</span></span>

<span data-ttu-id="381f0-548">Devolución de un servidor DNS IPv4 de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="381f0-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-549">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="381f0-550">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-550">Description</span></span>

<span data-ttu-id="381f0-551">Este servicio devuelve la dirección del servidor DNS IPv4 de la lista de servidores en el índice especificado.</span><span class="sxs-lookup"><span data-stu-id="381f0-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="381f0-552">Tenga en cuenta que el índice es de base cero.</span><span class="sxs-lookup"><span data-stu-id="381f0-552">Note that the index is zero based.</span></span> <span data-ttu-id="381f0-553">Si el índice de entrada supera el tamaño de la lista de clientes DNS, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="381f0-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="381f0-554">Se puede llamar al servicio *nx_dns_get_serverlist_size* primero para obtener el número de servidores DNS en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="381f0-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-555">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-555">Input Parameters</span></span>

- <span data-ttu-id="381f0-556">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="381f0-557">**index**: índice de la lista de servidores del cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="381f0-558">**dns_server_address**: puntero a la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-559">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-559">Return Values</span></span>

- <span data-ttu-id="381f0-560">**NX_SUCCESS** (0x00): el servidor se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="381f0-561">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el índice apunta a una ranura vacía.</span><span class="sxs-lookup"><span data-stu-id="381f0-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="381f0-562">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): el índice apunta a una dirección nula.</span><span class="sxs-lookup"><span data-stu-id="381f0-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="381f0-563">**NX_DNS_PARAM_ERROR** (0xA8): el índice supera el tamaño de la lista.</span><span class="sxs-lookup"><span data-stu-id="381f0-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="381f0-564">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="381f0-565">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-566">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-566">Allowed From</span></span>

<span data-ttu-id="381f0-567">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-568">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="381f0-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="381f0-569">nx_dns_server_remove</span></span>

<span data-ttu-id="381f0-570">Eliminación de un servidor DNS IPv4 de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="381f0-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-571">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="381f0-572">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-572">Description</span></span>

<span data-ttu-id="381f0-573">Este servicio quita un servidor DNS IPv4 de la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="381f0-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-574">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-574">Input Parameters</span></span>

- <span data-ttu-id="381f0-575">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="381f0-576">**server_address**: dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-577">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-577">Return Values</span></span>

- <span data-ttu-id="381f0-578">**NX_SUCCESS** (0x00): el servidor DNS se quitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="381f0-579">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el servidor no está en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="381f0-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="381f0-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="381f0-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="381f0-581">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="381f0-582">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-583">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-583">Allowed From</span></span>

<span data-ttu-id="381f0-584">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-585">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="381f0-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="381f0-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="381f0-587">Eliminación de todos los servidores DNS de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="381f0-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="381f0-588">Prototipo</span><span class="sxs-lookup"><span data-stu-id="381f0-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="381f0-589">Descripción</span><span class="sxs-lookup"><span data-stu-id="381f0-589">Description</span></span>

<span data-ttu-id="381f0-590">Este servicio quita todos los servidores DNS de la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="381f0-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="381f0-591">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="381f0-591">Input Parameters</span></span>

- <span data-ttu-id="381f0-592">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="381f0-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="381f0-593">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="381f0-593">Return Values</span></span>

- <span data-ttu-id="381f0-594">**NX_SUCCESS** (0x00): los servidores DNS se quitaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="381f0-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="381f0-595">**NX_DNS_ERROR** (0XA0): no se puede obtener la exclusión mutua de protección.</span><span class="sxs-lookup"><span data-stu-id="381f0-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="381f0-596">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="381f0-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="381f0-597">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="381f0-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="381f0-598">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="381f0-598">Allowed From</span></span>

<span data-ttu-id="381f0-599">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="381f0-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="381f0-600">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="381f0-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```