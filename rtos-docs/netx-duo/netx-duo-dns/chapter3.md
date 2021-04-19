---
title: 'Capítulo 3: Descripción de los servicios del cliente DNS de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814730"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="0b1ae-103">Capítulo 3: Descripción de los servicios del cliente DNS de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="0b1ae-104">Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0b1ae-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0b1ae-106">**nx_dns_authority_zone_start_get** *permite buscar el inicio de una zona de autoridad asociada con el nombre de host especificado*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="0b1ae-107">**nx_dns_cache_initialize** *permite inicializar una caché de DNS.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="0b1ae-108">**nx_dns_cache_notify_clear** *permite borrar la función de notificación completa de la memoria caché.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="0b1ae-109">**nx_dns_cache_notify_set** *permite establecer la función de notificación completa de la memoria caché.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="0b1ae-110">**nx_dns_cname_get** *permite buscar el nombre de dominio canónico para el alias de nombre de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="0b1ae-111">**nx_dns_create** *permite crear una instancia de cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="0b1ae-112">**nx_dns_delete** *permite eliminar una instancia de cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="0b1ae-113">**nx_dns_domain_name_server_get** *permite buscar los servidores de nombres autoritativos para la zona de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="0b1ae-114">**nx_dns_domain_mail_exchange_get** *permite buscar el intercambio de correo asociado al nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="0b1ae-115">**nx_dns_domain_service_get** *permite buscar los servicios asociados con el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="0b1ae-116">**nx_dns_get_serverlist_size** *permite devolver el tamaño de la lista de servidores del cliente DNS.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="0b1ae-117">**nx_dns_info_by_name_get** *permite devolver la dirección IP y la consulta de puertos en el nombre de host de entrada.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="0b1ae-118">**nx_dns_ipv4_address_by_name_get** *permite buscar la dirección IPv4 desde el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="0b1ae-119">**nxd_dns_ipv6_address_by_name_get** *permite buscar la dirección IPv6 desde el nombre de host especificado.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="0b1ae-120">**nx_dns_host_by_address_get** *función de contenedor para que nxd_dns_host_by_address_get busque un nombre de host desde una dirección IP especificada (solo admite direcciones IPv4).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="0b1ae-121">**nxd_dns_host_by_address_get** *permite buscar una dirección IP desde el nombre de host de entrada (admite direcciones IPv4 e IPv6).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="0b1ae-122">**nx_dns_host_by_name_get** *función de contenedor para que nxd_dns_host_by_address_get busque un nombre de host desde la dirección especificada (solo admite direcciones IPv4).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="0b1ae-123">**nxd_dns_host_by_name_get** *permite buscar una dirección IP desde el nombre de host de entrada (admite direcciones IPv4 e IPv6).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="0b1ae-124">**nx_dns_host_text_get** *permite buscar los datos de texto para el nombre de dominio de entrada.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="0b1ae-125">**nx_dhcp_packet_pool_set**: *permite establecer el grupo de paquetes del cliente DNS*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="0b1ae-126">**nx_dns_server_add** *función de contenedor de* nxd_dns_server_add *para agregar un servidor DNS en la dirección especificada a la lista de clientes (solo admite IPv4).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="0b1ae-127">**nxd_dns_server_add** *permite agregar un servidor DNS de la dirección IP especificada a la lista de servidores de cliente (admite direcciones IPv4 o IPv6).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="0b1ae-128">**nx_dns_server_get** *permite devolver el servidor DNS en la lista de clientes (solo admite direcciones IPv4).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="0b1ae-129">**nx_dns_server_get** *permite devolver el servidor DNS en la lista de clientes (admite direcciones IPv4 e IPv6).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="0b1ae-130">**nx_dns_server_remove** *función de contenedor de nxd_dns_server_remove para quitar un servidor DNS de la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="0b1ae-131">**nxd_dns_server_remove** *permite quitar un servidor DNS de la dirección IP especificada de la lista de clientes (admite direcciones IPv4 e IPv6).*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="0b1ae-132">**nx_dns_server_remove_all** *permite quitar todos los servidores DNS de la lista de clientes.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="0b1ae-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="0b1ae-134">Buscar el inicio de la zona de autoridad del host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-135">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="0b1ae-136">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-136">Description</span></span>

<span data-ttu-id="0b1ae-137">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SOA con el nombre de dominio especificado para obtener el inicio de la zona de autoridad para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="0b1ae-138">El cliente DNS copia los registros SOA devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="0b1ae-139">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-140">En el cliente DNS de NetX Duo, el tipo de registro SOA, NX_DNS_SOA_ENTRY, se guarda como siete parámetros de 4 bytes, que suman un total de 28 bytes:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="0b1ae-141">**nx_dns_soa_host_mname_ptr**: puntero al origen de datos principal para esta zona.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="0b1ae-142">**nx_dns_soa_host_rname_ptr**: puntero al responsable del buzón para esta zona.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="0b1ae-143">**nx_dns_soa_serial**: número de versión de zona.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="0b1ae-144">**nx_dns_soa_refresh**: intervalo de actualización.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="0b1ae-145">**nx_dns_soa_retry**: intervalo entre reintentos de consultas SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="0b1ae-146">**nx_dns_soa_expire**: duración del tiempo de expiración de SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="0b1ae-147">**nx_dns_soa_minmum**: campo TTL mínimo en los mensajes de respuesta DNS del nombre de host SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="0b1ae-148">A continuación se muestra el almacenamiento de dos registros SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="0b1ae-149">Los registros SOA que contienen datos de longitud fija se introducen empezando por la parte superior del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="0b1ae-150">Los punteros MNAME y RNAME apuntan a los datos de longitud variable (nombres de host) que se almacenan en la parte inferior del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="0b1ae-151">Los registros SOA adicionales se escriben después del primer registro ("registros SOA adicionales...") y sus datos de longitud variable se almacenan encima de los datos de longitud variable de la última entrada ("datos de longitud variable de SOA adicionales"):</span><span class="sxs-lookup"><span data-stu-id="0b1ae-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Almacenamiento de dos registros SOA](media/image4.png)

<span data-ttu-id="0b1ae-153">Si la ubicación *record_buffer* de entrada no puede contener todos los datos SOA de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="0b1ae-154">Con el número de registros SOA devueltos en \**record_count,* la aplicación puede analizar los datos de *record_buffer* y extraer el inicio de las cadenas de nombre de host de la entidad de zona.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-155">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-155">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-156">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-157">**host_name**: puntero al nombre de host para el que se van a obtener datos SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="0b1ae-158">**record_buffer**: puntero a la ubicación en la que se van a extraer datos SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="0b1ae-159">**buffer_size**: tamaño del búfer que contendrá datos SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="0b1ae-160">**record_count**: puntero al número de registros SOA recuperados.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="0b1ae-161">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-162">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-162">Return Values</span></span>

- <span data-ttu-id="0b1ae-163">**NX_SUCCESS** (0x00): los datos SOA se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="0b1ae-164">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-165">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-166">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-167">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-168">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-169">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-169">Allowed From</span></span>

<span data-ttu-id="0b1ae-170">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-171">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-171">Example</span></span>
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

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

[Output]
----------------------------------------------------
Test SOA: 
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="0b1ae-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="0b1ae-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="0b1ae-173">Inicialización de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-174">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="0b1ae-175">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-175">Description</span></span>

<span data-ttu-id="0b1ae-176">Este servicio crea e inicializa una caché de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-177">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-177">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-178">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="0b1ae-179">**cache_ptr**: puntero a la caché de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="0b1ae-180">**cache_size**: tamaño de la caché de DNS, en bytes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-181">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-181">Return Values</span></span>

- <span data-ttu-id="0b1ae-182">**NX_SUCCESS** (0x00): la caché de DNS se inicializó correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="0b1ae-183">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-184">NX_DNS_CACHE_ERROR (0xB7): puntero de caché no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="0b1ae-185">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="0b1ae-186">NX_DNS_ERROR (0xA0): la memoria caché no es alineada de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-187">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-187">Allowed From</span></span>

<span data-ttu-id="0b1ae-188">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-189">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="0b1ae-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="0b1ae-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="0b1ae-191">Borrar la función de notificación completa de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="0b1ae-193">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-193">Description</span></span>

<span data-ttu-id="0b1ae-194">Este servicio borra la función de notificación completa de la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-195">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-195">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-196">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-197">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-197">Return Values</span></span>

- <span data-ttu-id="0b1ae-198">**NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="0b1ae-199">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="0b1ae-200">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-201">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-201">Allowed From</span></span>

<span data-ttu-id="0b1ae-202">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-203">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="0b1ae-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="0b1ae-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="0b1ae-205">Establecer la función de notificación completa de la caché de DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-206">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="0b1ae-207">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-207">Description</span></span>

<span data-ttu-id="0b1ae-208">Este servicio establece la función de notificación completa de la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-209">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-209">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-210">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="0b1ae-211">**cache_full_notify_cb**: función de devolución de llamada que se va a invocar cuando la memoria caché se llene.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-212">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-212">Return Values</span></span>

- <span data-ttu-id="0b1ae-213">**NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="0b1ae-214">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="0b1ae-215">NX_PTR_ERROR (0x07): puntero de DNS no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-216">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-216">Allowed From</span></span>

<span data-ttu-id="0b1ae-217">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-218">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="0b1ae-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-219">nx_dns_cname_get</span></span>

<span data-ttu-id="0b1ae-220">Buscar el nombre canónico del nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-221">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-222">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-222">Description</span></span>

<span data-ttu-id="0b1ae-223">Si NX_DNS_ENABLE_EXTENDED_RR_TYPES se define en *nxd_dns.h*, este servicio envía una consulta de tipo CNAME con el nombre de dominio especificado para obtener el nombre de dominio canónico.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="0b1ae-224">El cliente DNS copia la cadena CNAME devuelta en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-225">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-225">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-226">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-227">**host_name**: puntero al nombre de host para el que se van a obtener datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="0b1ae-228">**record_buffer**: puntero a la ubicación en la que se van a extraer datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="0b1ae-229">**buffer_size**: tamaño del búfer que contendrá datos CNAME.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="0b1ae-230">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-231">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-231">Return Values</span></span>

- <span data-ttu-id="0b1ae-232">**NX_SUCCESS** (0x00): los datos CNAME se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="0b1ae-233">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-234">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-235">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-236">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-237">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-238">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-238">Allowed From</span></span>

<span data-ttu-id="0b1ae-239">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-240">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-240">Example</span></span>
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a><span data-ttu-id="0b1ae-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="0b1ae-241">nx_dns_create</span></span>

<span data-ttu-id="0b1ae-242">Crear una instancia de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-243">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="0b1ae-244">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-244">Description</span></span>

<span data-ttu-id="0b1ae-245">Este servicio crea una instancia de cliente DNS para la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b1ae-246">La aplicación debe asegurarse de que la carga de paquetes del grupo de paquetes utilizada por el cliente DNS es lo suficientemente grande para el mensaje DNS máximo de 512 bytes, más los encabezados UDP, IP y Ethernet.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="0b1ae-247">Si el cliente DNS crea su propio grupo de paquetes, se define mediante NX_DNS_PACKET_PAYLOAD y NX_DNS_PACKET_POOL_SIZE.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="0b1ae-248">Si la aplicación cliente DNS prefiere proporcionar un grupo de paquetes creado previamente, la carga para el cliente DNS IPv4 debe ser de 512 bytes para el DNS máximo más 20 bytes para el encabezado IP, 8 bytes para el encabezado UDP y 14 bytes para el encabezado Ethernet.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="0b1ae-249">En el caso de IPv6, la única diferencia es que el encabezado IP es de 40 bytes, por lo que el paquete debe contener el encabezado IPv6 de 40 bytes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-250">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-250">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-251">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-252">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="0b1ae-253">**domain_name**: puntero al nombre de dominio para la instancia DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-254">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-254">Return Values</span></span>

- <span data-ttu-id="0b1ae-255">**NX_SUCCESS** (0x00): DNS creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="0b1ae-256">**NX_DNS_ERROR** (0xA0): error de creación de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="0b1ae-257">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-258">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-259">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-259">Allowed From</span></span>

<span data-ttu-id="0b1ae-260">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-261">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="0b1ae-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="0b1ae-262">nx_dns_delete</span></span>

<span data-ttu-id="0b1ae-263">Eliminar una instancia de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-264">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="0b1ae-265">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-265">Description</span></span>

<span data-ttu-id="0b1ae-266">Este servicio elimina una instancia de cliente DNS creada anteriormente y libera sus recursos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-267">Si se define NX_DNS_CLIENT_USER_CREATE_PACKET_POOL y se asignó al cliente DNS un grupo de paquetes definido por el usuario, depende de la aplicación que se elimine el grupo de paquetes del cliente DNS si ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-268">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-268">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-269">**dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-270">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-270">Return Values</span></span>

- <span data-ttu-id="0b1ae-271">**NX_SUCCESS** (0x00): cliente DNS eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="0b1ae-272">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="0b1ae-273">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-274">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-274">Allowed From</span></span>

<span data-ttu-id="0b1ae-275">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-276">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="0b1ae-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="0b1ae-278">Buscar los servidores de nombres autoritativos para la zona de dominio de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-279">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-280">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-280">Description</span></span>

<span data-ttu-id="0b1ae-281">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo NS con el nombre de dominio especificado para obtener los servidores de nombres para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="0b1ae-282">El cliente DNS copia los registros NS devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="0b1ae-283">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-284">En el cliente DNS de NetX Duo, el tipo de datos NS, NX_DNS_NS_ENTRY, se guarda como dos parámetros de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="0b1ae-285">**nx_dns_ns_ipv4_address**: dirección IPv4 del servidor de nombres.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="0b1ae-286">**nx_dns_ns_hostname_ptr**: puntero al nombre de host del servidor de nombres.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="0b1ae-287">El búfer que se muestra a continuación contiene cuatro registros NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="0b1ae-288">El puntero a la cadena de nombre de host en cada entrada apunta a la cadena de nombre de host correspondiente en la mitad inferior del búfer:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Contiene cuatro registros NX_DNS_NS_ENTRY](media/image5.png)

<span data-ttu-id="0b1ae-290">Si la ubicación *record_buffer* de entrada no puede contener todos los datos NS de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="0b1ae-291">Con el número de registros NS devueltos en \**record_count,* la aplicación puede analizar la dirección IP y el nombre de host de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-292">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-292">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-293">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-294">**host_name**: puntero al nombre de host para el que se van a obtener datos NS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="0b1ae-295">**record_buffer**: puntero a la ubicación en la que se van a extraer datos NS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="0b1ae-296">**buffer_size**: tamaño del búfer que contendrá datos NS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="0b1ae-297">**record_count**: puntero al número de registros NS recuperados.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="0b1ae-298">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-299">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-299">Return Values</span></span>

- <span data-ttu-id="0b1ae-300">**NX_SUCCESS** (0x00): los datos NS se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="0b1ae-301">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-302">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-303">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="0b1ae-304">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-305">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-306">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-306">Allowed From</span></span>

<span data-ttu-id="0b1ae-307">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-308">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-308">Example</span></span>
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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

[Output]
------------------------------------------------------
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="0b1ae-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="0b1ae-310">Buscar los intercambios de correo para el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-311">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-312">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-312">Description</span></span>

<span data-ttu-id="0b1ae-313">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo MX con el nombre de dominio especificado para obtener el intercambio de correo para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="0b1ae-314">El cliente DNS copia los registros MX devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-315">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-316">En el cliente DNS de NetX Duo, el tipo de registro de intercambio de correo, NX_DNS_MAIL_EXCHANGE_ENTRY, se guarda como cuatro parámetros que suman un total de 12 bytes:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="0b1ae-317">**nx_dns_mx_ipv4_address**: dirección IPv4 de intercambio de correo de 4 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="0b1ae-318">**nx_dns_mx_preference**: preferencia de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="0b1ae-319">**nx_dns_mx_reserved0**: 2 bytes reservados</span><span class="sxs-lookup"><span data-stu-id="0b1ae-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="0b1ae-320">**nx_dns_mx_hostname_ptr**: puntero al nombre de host del servidor de intercambio de correo de 4 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="0b1ae-321">A continuación se muestra un búfer que contiene cuatro registros MX.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="0b1ae-322">Cada registro contiene los datos de longitud fija de la lista anterior.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="0b1ae-323">El puntero al nombre de host del servidor de intercambio de correo apunta al nombre de host correspondiente en la parte inferior del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Un búfer que contiene cuatro registros MX](media/image6.png)

<span data-ttu-id="0b1ae-325">Si la ubicación *record_buffer* de entrada no puede contener todos los datos MX de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="0b1ae-326">Con el número de registros MX devueltos en \**record_count,* la aplicación puede analizar los parámetros MX, incluido el nombre de host de correo de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-327">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-327">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-328">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-329">**host_name**: puntero al nombre de host para el que se van a obtener datos SOA.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="0b1ae-330">**record_buffer**: puntero a la ubicación en la que se van a extraer datos MX.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="0b1ae-331">**buffer_size**: tamaño del búfer que contendrá datos MX.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="0b1ae-332">**record_count**: puntero al número de registros MX recuperados.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="0b1ae-333">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-334">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-334">Return Values</span></span>

- <span data-ttu-id="0b1ae-335">**NX_SUCCESS** (0x00): los datos MX se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="0b1ae-336">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-337">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-338">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="0b1ae-339">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-340">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-341">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-341">Allowed From</span></span>

<span data-ttu-id="0b1ae-342">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-343">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-343">Example</span></span>
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="0b1ae-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="0b1ae-345">Buscar los servicios proporcionados por el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-346">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-347">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-347">Description</span></span>

<span data-ttu-id="0b1ae-348">Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SRV con el nombre de dominio especificado para buscar los servicios y su número de puerto asociado con el dominio especificado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="0b1ae-349">El cliente DNS copia los registros SRV devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-350">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-351">En el cliente DNS de NetX Duo, el tipo de registro del servicio, NX_DNS_SRV_ENTRY, se guarda como seis parámetros que suman un total de 16 bytes:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="0b1ae-352">Esto permite almacenar datos SRV de longitud variable de manera eficaz para la memoria:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="0b1ae-353">**Dirección IPv4 del servidor**: nx_dns_srv_ipv4_address de 4 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="0b1ae-354">**Prioridad del servidor**: nx_dns_srv_priority de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="0b1ae-355">**Peso del servidor**: nx_dns_srv_weight de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="0b1ae-356">**Número de puerto de servicio**: nx_dns_srv_port_number de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="0b1ae-357">**Reservado para la alineación de 4 bytes**: nx_dns_srv_reserved0 de 2 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="0b1ae-358">**Puntero al nombre de host del servidor**: \*nx_dns_srv_hostname_ptr de 4 bytes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="0b1ae-359">Se almacenan cuatro registros SRV en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="0b1ae-360">Cada registro de NX_DNS_SRV_ENTRY contiene un puntero, *nx_dns_srv_hostname_ptr*, que apunta a la cadena de nombre de host correspondiente en la parte inferior del búfer de registro:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Cuatro registros SRV](media/image7.png)

<span data-ttu-id="0b1ae-362">Si la ubicación *record_buffer* de entrada no puede contener todos los datos SRV de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="0b1ae-363">Con el número de registros SRV devueltos en \**record_count,* la aplicación puede analizar los parámetros SRV, incluido el nombre de host del servidor de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-364">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-364">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-365">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-366">**host_name**: puntero al nombre de host para el que se van a obtener datos SRV.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="0b1ae-367">**record_buffer**: puntero a la ubicación en la que se van a extraer datos SRV.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="0b1ae-368">**buffer_size**: tamaño del búfer que contendrá datos SRV.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="0b1ae-369">**record_count**: puntero al número de registros SRV recuperados.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="0b1ae-370">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-371">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-371">Return Values</span></span>

- <span data-ttu-id="0b1ae-372">**NX_SUCCESS** (0x00): los datos SRV se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="0b1ae-373">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-374">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-375">NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="0b1ae-376">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-377">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-378">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-378">Allowed From</span></span>

<span data-ttu-id="0b1ae-379">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-380">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-380">Example</span></span>
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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

[Output]
----------------------------------------------------
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="0b1ae-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="0b1ae-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="0b1ae-382">Devolver el tamaño de la lista de servidores del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-383">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="0b1ae-384">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-384">Description</span></span>

<span data-ttu-id="0b1ae-385">Este servicio devuelve el número de servidores DNS válidos (tanto IPv4 como IPv6) en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-386">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-386">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-387">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="0b1ae-388">**size**: devuelve el número de servidores de la lista.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-389">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-389">Return Values</span></span>

- <span data-ttu-id="0b1ae-390">**NX_SUCCESS** (0x00): el tamaño de la lista de servidores DNS se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="0b1ae-391">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-392">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-393">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-393">Allowed From</span></span>

<span data-ttu-id="0b1ae-394">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-395">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="0b1ae-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="0b1ae-397">Devolver la dirección IP y el puerto del servidor DNS por nombre de host</span><span class="sxs-lookup"><span data-stu-id="0b1ae-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-398">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-399">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-399">Description</span></span>

<span data-ttu-id="0b1ae-400">Este servicio devuelve la dirección IP del servidor y el puerto (registro de servicio) basados en el nombre de host de entrada mediante la consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="0b1ae-401">Si no se encuentra un registro de servicio, esta rutina devuelve una dirección IP cero en el puntero de la dirección de entrada y una devolución de estado de error distinto de cero para indicar un error.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-402">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-402">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-403">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="0b1ae-404">**host_name**: puntero al búfer de nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="0b1ae-405">**host_address_ptr**: puntero a la dirección que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="0b1ae-406">**host_port_ptr**: puntero al puerto que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="0b1ae-407">**wait_option**: opción de espera para la respuesta de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-408">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-408">Return Values</span></span>

- <span data-ttu-id="0b1ae-409">**NX_SUCCESS** (0x00): el registro del servidor DNS se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="0b1ae-410">**NX_DNS_NO_SERVER** (0XA1): no hay ningún servidor DNS registrado en el cliente para enviar la consulta en el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="0b1ae-411">**NX_DNS_QUERY_FAILED** (0xA3): error de la consulta de DNS; no hay ninguna respuesta de ningún servidor DNS en la lista del cliente o no existe ningún registro de servicio disponible para el nombre de host de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="0b1ae-412">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-413">NX_CALLER_ERROR (0x11): autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-414">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-414">Allowed From</span></span>

<span data-ttu-id="0b1ae-415">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-416">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="0b1ae-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="0b1ae-418">Buscar la dirección IPv4 para el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-419">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-420">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-420">Description</span></span>

<span data-ttu-id="0b1ae-421">Este servicio envía una consulta de tipo A con el nombre de host especificado para obtener las direcciones IP para el nombre de host de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="0b1ae-422">El cliente DNS copia la dirección IPv4 de los registros A devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="0b1ae-423">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-424">Varias direcciones IPv4 se almacenan en el búfer alineado de 4 bytes, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Búfer alineado de 4 bytes con varias direcciones](media/image8.png)

<span data-ttu-id="0b1ae-426">Si el búfer proporcionado no puede contener todos los datos de las direcciones IP, los registros A restantes no se almacenan en *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="0b1ae-427">Esto permite que la aplicación recupere uno, algunos o todos los datos de direcciones IP disponibles en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="0b1ae-428">Con el número de registros A devueltos en \**record_count*, la aplicación puede analizar los datos de dirección IPv4 desde la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-429">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-429">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-430">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-431">**host_name_ptr**: puntero al nombre de host para obtener la dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="0b1ae-432">**buffer**: puntero a la ubicación en la que se van a extraer datos IPv4.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="0b1ae-433">**buffer_size**: tamaño del búfer que contendrá datos IPv4.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="0b1ae-434">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-435">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-435">Return Values</span></span>

- <span data-ttu-id="0b1ae-436">**NX_SUCCESS** (0x00): los datos IPv4 se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="0b1ae-437">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-438">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-439">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-440">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-441">NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-442">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-442">Allowed From</span></span>

<span data-ttu-id="0b1ae-443">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-444">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-444">Example</span></span>
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
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

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="0b1ae-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="0b1ae-446">Buscar la dirección IPv6 para el nombre de host de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-447">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-448">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-448">Description</span></span>

<span data-ttu-id="0b1ae-449">Este servicio envía una consulta de tipo AAAA con el nombre de dominio especificado para obtener las direcciones IP para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="0b1ae-450">El cliente DNS copia la dirección IPv6 de los registros AAAA devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-451">La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="0b1ae-452">A continuación se muestra el formato de las direcciones IPv6 almacenadas en el búfer alineado de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![Formato IPv6 del búfer alineado de 4 bytes](media/image9.png)

<span data-ttu-id="0b1ae-454">Si la ubicación *record_buffer* de entrada no puede contener todos los datos AAAA de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="0b1ae-455">Con el número de registros AAAA devueltos en \**record_count,* la aplicación puede analizar las direcciones IPv6 de cada registro en la ubicación *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-456">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-456">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-457">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-458">**host_name_ptr**: puntero al nombre de host para obtener la dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="0b1ae-459">**buffer**: puntero a la ubicación en la que se van a extraer datos IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="0b1ae-460">**buffer_size**: tamaño del búfer que contendrá datos IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="0b1ae-461">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-462">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-462">Return Values</span></span>

- <span data-ttu-id="0b1ae-463">**NX_SUCCESS** (0x00): los datos IPv6 se obtuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="0b1ae-464">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-465">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-466">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-467">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-468">NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-469">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-469">Allowed From</span></span>

<span data-ttu-id="0b1ae-470">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-471">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-471">Example</span></span>
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="0b1ae-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="0b1ae-473">Buscar un nombre de host desde una dirección IP</span><span class="sxs-lookup"><span data-stu-id="0b1ae-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-474">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-475">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-475">Description</span></span>

<span data-ttu-id="0b1ae-476">Este servicio solicita la resolución de nombres de la dirección IP suministrada de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="0b1ae-477">Si la operación se realiza correctamente, se devuelve el nombre de host terminado en NULL en la cadena especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="0b1ae-478">Se trata de una función de contenedor para el servicio *nxd_dns_host_by_address_get* y no acepta direcciones IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-479">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-479">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-480">**dns_ptr**: puntero a la instancia de DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="0b1ae-481">**ip_address**: dirección IP que se va a resolver en un nombre.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="0b1ae-482">**host_name_ptr**: puntero al área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="0b1ae-483">**max_host_name_size**: tamaño del área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="0b1ae-484">**wait_option**: define cuánto tiempo esperará el servicio en tics de temporizador para una respuesta del servidor DNS después de cada consulta de DNS y reintento de consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="0b1ae-485">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0b1ae-486">valor de tiempo de espera (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0b1ae-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0b1ae-487">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="0b1ae-488">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-489">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-489">Return Values</span></span>

- <span data-ttu-id="0b1ae-490">**NX_SUCCESS** (0x00): resolución de DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="0b1ae-491">**NX_DNS_TIMEOUT** (0xA2): se agotó el tiempo de espera al obtener la exclusión mutua de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="0b1ae-492">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="0b1ae-493">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="0b1ae-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="0b1ae-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="0b1ae-496">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-498">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-499">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-500">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-500">Allowed From</span></span>

<span data-ttu-id="0b1ae-501">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-501">Threads</span></span>

<span data-ttu-id="0b1ae-502">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="0b1ae-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="0b1ae-504">Buscar un nombre de host desde una dirección IP</span><span class="sxs-lookup"><span data-stu-id="0b1ae-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-505">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-506">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-506">Description</span></span>

<span data-ttu-id="0b1ae-507">Este servicio solicita la resolución de nombres de la dirección IPv6 o IPv4 en el argumento de entrada *ip_address* de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="0b1ae-508">Si la operación se realiza correctamente, se devuelve el nombre de host terminado en NULL en la cadena especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-509">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-509">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-510">**dns_ptr**: puntero a la instancia de DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="0b1ae-511">**ip_address**: dirección IP que se va a resolver en un nombre.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="0b1ae-512">**host_name_ptr**: puntero al área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="0b1ae-513">**max_host_name_size**: tamaño del área de destino para el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="0b1ae-514">**wait_option**: define cuánto tiempo esperará el servicio en tics de temporizador para una respuesta del servidor DNS después de cada consulta de DNS y reintento de consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="0b1ae-515">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0b1ae-516">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0b1ae-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="0b1ae-517">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="0b1ae-518">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-519">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-519">Return Values</span></span>

- <span data-ttu-id="0b1ae-520">**NX_SUCCESS** (0x00): resolución de DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="0b1ae-521">**NX_DNS_TIMEOUT** (0xA2): se agotó el tiempo de espera al obtener la exclusión mutua de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="0b1ae-522">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="0b1ae-523">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="0b1ae-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="0b1ae-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-526">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="0b1ae-527">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-528">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-529">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-529">Allowed From</span></span>

<span data-ttu-id="0b1ae-530">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-530">Threads</span></span>

<span data-ttu-id="0b1ae-531">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-531">**Example**</span></span>
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="0b1ae-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="0b1ae-533">Buscar una dirección IP desde el nombre de host</span><span class="sxs-lookup"><span data-stu-id="0b1ae-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-534">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-535">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-535">Description</span></span>

<span data-ttu-id="0b1ae-536">Este servicio solicita la resolución de nombres del nombre suministrado de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="0b1ae-537">Si la operación se realiza correctamente, se devuelve la dirección IP asociada en el destino al que apunta host_address_ptr.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="0b1ae-538">Se trata de una función de contenedor para el servicio *nxd_dns_host_by_name_get* y se limita a la entrada de dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-539">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-539">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-540">**dns_ptr**: puntero a la instancia de DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="0b1ae-541">**host_name**: puntero al nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="0b1ae-542">**host_address_ptr**: dirección IP del servidor DNS devuelta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="0b1ae-543">**wait_option**: define cuánto tiempo esperará el servicio para la resolución de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="0b1ae-544">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0b1ae-545">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0b1ae-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0b1ae-546">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="0b1ae-547">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-548">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-548">Return Values</span></span>

- <span data-ttu-id="0b1ae-549">**NX_SUCCESS** (0x00): resolución de DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="0b1ae-550">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="0b1ae-551">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="0b1ae-552">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-553">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-554">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-555">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-555">Allowed From</span></span>

<span data-ttu-id="0b1ae-556">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-556">Threads</span></span>

<span data-ttu-id="0b1ae-557">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-557">**Example**</span></span>
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="0b1ae-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="0b1ae-559">Buscar una dirección IP desde el nombre de host</span><span class="sxs-lookup"><span data-stu-id="0b1ae-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-560">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="0b1ae-561">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-561">Description</span></span>

<span data-ttu-id="0b1ae-562">Este servicio solicita la resolución de nombres de la dirección IP suministrada de uno o más servidores DNS especificados anteriormente por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="0b1ae-563">Si la operación se realiza correctamente, se devuelve la dirección IP asociada en un servicio NXD_ADDRESS al que apunta *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="0b1ae-564">Si el autor de la llamada establece específicamente la entrada lookup_type en NX_IP_VERSION_V6, este servicio enviará una consulta para una dirección IPv6 de host (registro AAAA).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="0b1ae-565">Si el autor de la llamada establece específicamente la entrada lookup_type en NX_IP_VERSION_V4, este servicio enviará una consulta para una dirección IPv4 de host (registro A).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-566">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-566">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-567">**dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="0b1ae-568">**host_name**: puntero al nombre de host del que se buscará una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="0b1ae-569">**host_address_ptr**: puntero al destino de NXD_ADDRESS que contiene la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="0b1ae-570">**waig_option**: define cuánto tiempo esperará el servicio en tics de temporizador para la respuesta del servidor DNS para cada transmisión y retransmisión de consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="0b1ae-571">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0b1ae-572">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0b1ae-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="0b1ae-573">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="0b1ae-574">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="0b1ae-575">**lookup_type**: indica el tipo de búsqueda (A frente a AAAA).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-576">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-576">Return Values</span></span>

- <span data-ttu-id="0b1ae-577">**NX_SUCCESS** (0x00): resolución de DNS correcta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="0b1ae-578">**NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="0b1ae-579">**NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="0b1ae-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="0b1ae-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-582">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-583">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-584">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-585">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-585">Allowed From</span></span>

<span data-ttu-id="0b1ae-586">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-586">Threads</span></span>

<span data-ttu-id="0b1ae-587">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-587">**Example**</span></span>
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

<span data-ttu-id="0b1ae-588">A continuación se muestra otro ejemplo del uso de este servicio de tiempo, esta vez con direcciones IPv4 y tipos de registro A:</span><span class="sxs-lookup"><span data-stu-id="0b1ae-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="0b1ae-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="0b1ae-590">Buscar la cadena de texto para el nombre de dominio de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-591">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0b1ae-592">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-592">Description</span></span>

<span data-ttu-id="0b1ae-593">Este servicio envía una consulta de tipo TXT con el nombre de dominio y el búfer especificados para obtener los datos de cadena arbitrarios.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="0b1ae-594">El cliente DNS copia la cadena de texto del registro TXT de la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-595">La ubicación record_buffer no necesita tener una alineación de 4 bytes para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-596">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-596">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-597">**dns_ptr**: puntero al cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="0b1ae-598">**host_name**: puntero al nombre del host en el que se realizará la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="0b1ae-599">**record_buffer**: puntero a la ubicación en la que se van a extraer datos TXT.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="0b1ae-600">**buffer_size**: tamaño del búfer que contendrá datos TXT.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="0b1ae-601">**wait_option**: opción de espera que recibirá la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-602">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-602">Return Values</span></span>

- <span data-ttu-id="0b1ae-603">**NX_SUCCESS** (0x00): se obtuvo correctamente la cadena TXT.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="0b1ae-604">**NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="0b1ae-605">**NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="0b1ae-606">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-607">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-608">NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-609">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-609">Allowed From</span></span>

<span data-ttu-id="0b1ae-610">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-610">Threads</span></span>

######   
<span data-ttu-id="0b1ae-611">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-611">Example</span></span>
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="0b1ae-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="0b1ae-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="0b1ae-613">Establecer el grupo de paquetes del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-614">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="0b1ae-615">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-615">Description</span></span>

<span data-ttu-id="0b1ae-616">Este servicio establece un grupo de paquetes creado anteriormente como el grupo de paquetes del cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="0b1ae-617">El cliente DNS usará este grupo de paquetes para enviar consultas de DNS, por lo que la carga de paquetes no debe ser inferior al valor de NX_DNS_PACKET_PAYLOAD, que incluye los encabezados Ethernet, IP y UDP, y se define en *nxd_dns.h.*</span><span class="sxs-lookup"><span data-stu-id="0b1ae-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-618">*C* uando se elimina el cliente DNS, el grupo de paquetes no se elimina con este y es responsabilidad de la aplicación eliminarlo cuando ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="0b1ae-619">Este servicio solo está disponible si la opción de configuración NX_DNS_CLIENT_USER_CREATE_PACKET_POOL se define en *nxd_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-620">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-620">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-621">**dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="0b1ae-622">**pool_ptr** Puntero a un grupo de paquetes creado previamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-623">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-623">Return Values</span></span>

- <span data-ttu-id="0b1ae-624">**NX_SUCCESS** (0x00): operación finalizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="0b1ae-625">**NX_NOT_ENABLED** (0x14): cliente no configurado para esta opción.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="0b1ae-626">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="0b1ae-627">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-628">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-628">Allowed From</span></span>

<span data-ttu-id="0b1ae-629">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-630">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-630">Example</span></span>
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="0b1ae-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="0b1ae-631">nx_dns_server_add</span></span>

<span data-ttu-id="0b1ae-632">Agregar dirección IP del servidor DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-633">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="0b1ae-634">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-634">Description</span></span>

<span data-ttu-id="0b1ae-635">Este servicio agrega un servidor DNS IPv4 a la lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-636">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-636">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-637">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="0b1ae-638">**server_address**: dirección IP del servidor DNS</span><span class="sxs-lookup"><span data-stu-id="0b1ae-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-639">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-639">Return Values</span></span>

- <span data-ttu-id="0b1ae-640">**NX_SUCCESS** (0x00): servidor agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="0b1ae-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="0b1ae-642">**NX_NO_MORE_ENTRIES** (0X17): no se permiten más servidores DNS (la lista está llena).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="0b1ae-643">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-645">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-646">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-648">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-648">Allowed From</span></span>

<span data-ttu-id="0b1ae-649">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-650">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="0b1ae-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="0b1ae-651">nxd_dns_server_add</span></span>

<span data-ttu-id="0b1ae-652">Agregar servidor DNS a la lista del cliente</span><span class="sxs-lookup"><span data-stu-id="0b1ae-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-653">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="0b1ae-654">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-654">Description</span></span>

<span data-ttu-id="0b1ae-655">Este servicio agrega la dirección IP de un servidor DNS a la lista de servidores del cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="0b1ae-656">El valor de server_address puede ser una dirección IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="0b1ae-657">Si el cliente desea poder acceder al mismo servidor mediante la dirección IPv4 o la dirección IPv6, debe agregar ambas direcciones IP como entradas a la lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-658">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-658">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-659">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="0b1ae-660">**server_address**: puntero al servicio NXD_ADDRESS que contiene la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-661">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-661">Return Values</span></span>

- <span data-ttu-id="0b1ae-662">**NX_SUCCESS** (0x00): servidor agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="0b1ae-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="0b1ae-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="0b1ae-664">**NX_NO_MORE_ENTRIES** (0X17): no se permiten más servidores DNS (la lista está llena).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="0b1ae-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-666">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-667">NX_PTR_ERROR (0x07): entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0b1ae-668">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="0b1ae-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-671">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-671">Allowed From</span></span>

<span data-ttu-id="0b1ae-672">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-673">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-673">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="0b1ae-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-674">nx_dns_server_get</span></span>

<span data-ttu-id="0b1ae-675">Devolver un servidor DNS IPv4 de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-676">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="0b1ae-677">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-677">Description</span></span>

<span data-ttu-id="0b1ae-678">Este servicio devuelve la dirección del servidor DNS IPv4 de la lista de servidores en el índice especificado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-679">El índice es de base cero.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-679">The index is zero based.</span></span> <span data-ttu-id="0b1ae-680">Si el índice de entrada supera el tamaño de la lista de clientes DNS, se encuentra una dirección IPv6 en dicho índice o se encuentra una dirección nula en el índice especificado, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="0b1ae-681">Se puede llamar al servicio *nx_dns_get_serverlist_size* primero para obtener el número de servidores DNS en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="0b1ae-682">Este servicio solo admite direcciones IPv4.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="0b1ae-683">Llama al servicio *nxd_dns_server_get* que admite tanto direcciones IPv4 como IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-684">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-684">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-685">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="0b1ae-686">**index**: índice de la lista de servidores del cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="0b1ae-687">**dns_server_address**: puntero a la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-688">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-688">Return Values</span></span>

- <span data-ttu-id="0b1ae-689">**NX_SUCCESS** (0x00): servidor devuelto correcto.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="0b1ae-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el índice apunta a una ranura vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="0b1ae-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): el índice apunta a una dirección nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="0b1ae-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="0b1ae-693">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="0b1ae-694">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-695">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-696">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-696">Allowed From</span></span>

<span data-ttu-id="0b1ae-697">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-698">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="0b1ae-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="0b1ae-699">nxd_dns_server_get</span></span>

<span data-ttu-id="0b1ae-700">Devolver un servidor DNS de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-701">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="0b1ae-702">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-702">Description</span></span>

<span data-ttu-id="0b1ae-703">Este servicio devuelve la dirección IP del servidor DNS de la lista de servidores en el índice especificado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="0b1ae-704">El índice es de base cero.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-704">The index is zero based.</span></span> <span data-ttu-id="0b1ae-705">Si el índice de entrada supera el tamaño de la lista de clientes DNS o se encuentra una dirección nula en el índice especificado, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="0b1ae-706">Se puede llamar al servicio *nx_dns_get_serverlist_size* primero para obtener el número de servidores DNS en la lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="0b1ae-707">Este servicio es compatible con las direcciones IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-708">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-708">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-709">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="0b1ae-710">**index**: índice de la lista de servidores del cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="0b1ae-711">**dns_server_address**: puntero a la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-712">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-712">Return Values</span></span>

- <span data-ttu-id="0b1ae-713">**NX_SUCCESS** (0x00): la dirección IP del servidor se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="0b1ae-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el índice apunta a una ranura vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="0b1ae-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): el índice apunta a una dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="0b1ae-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="0b1ae-717">**NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="0b1ae-718">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-719">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-720">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-720">Allowed From</span></span>

<span data-ttu-id="0b1ae-721">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-722">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="0b1ae-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="0b1ae-723">nx_dns_server_remove</span></span>

<span data-ttu-id="0b1ae-724">Quitar un servidor DNS IPv4 de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-725">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="0b1ae-726">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-726">Description</span></span>

<span data-ttu-id="0b1ae-727">Este servicio quita un servidor DNS IPv4 de la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="0b1ae-728">Es una función de contenedor para *nxd_dns_server_remove*.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-729">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-729">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-730">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="0b1ae-731">**server_address**: dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-732">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-732">Return Values</span></span>

- <span data-ttu-id="0b1ae-733">**NX_SUCCESS** (0x00): el servidor DNS se quitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="0b1ae-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el servidor no está en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="0b1ae-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="0b1ae-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-737">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-738">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-739">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-739">Allowed From</span></span>

<span data-ttu-id="0b1ae-740">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-741">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="0b1ae-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="0b1ae-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="0b1ae-743">Quitar un servidor DNS de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-744">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="0b1ae-745">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-745">Description</span></span>

<span data-ttu-id="0b1ae-746">Este servicio quita un servidor DNS de la dirección IP especificada de la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="0b1ae-747">La dirección IP de entrada acepta direcciones IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="0b1ae-748">Una vez quitado el servidor, el resto de los servidores baja un índice en la lista para ocupar la ranura vacía.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-749">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-749">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-750">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="0b1ae-751">**server_address**: puntero a los datos NXD_ADDRESS del servidor DNS que contienen la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-752">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-752">Return Values</span></span>

- <span data-ttu-id="0b1ae-753">**NX_SUCCESS** (0x00): el servidor DNS se quitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="0b1ae-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9): el servidor no está en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="0b1ae-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4): entrada de dirección de servidor nula.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="0b1ae-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="0b1ae-757">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-758">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0b1ae-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).</span><span class="sxs-lookup"><span data-stu-id="0b1ae-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-760">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-760">Allowed From</span></span>

<span data-ttu-id="0b1ae-761">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-762">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-762">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="0b1ae-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="0b1ae-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="0b1ae-764">Quitar todos los servidores DNS de la lista de clientes</span><span class="sxs-lookup"><span data-stu-id="0b1ae-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="0b1ae-765">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="0b1ae-766">Descripción</span><span class="sxs-lookup"><span data-stu-id="0b1ae-766">Description</span></span>

<span data-ttu-id="0b1ae-767">Este servicio quita todos los servidores DNS de la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0b1ae-768">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0b1ae-768">Input Parameters</span></span>

- <span data-ttu-id="0b1ae-769">**dns_ptr**: puntero al bloque de control DNS.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0b1ae-770">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-770">Return Values</span></span>

- <span data-ttu-id="0b1ae-771">**NX_SUCCESS** (0x00): los servidores DNS se quitaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="0b1ae-772">**NX_DNS_ERROR** (0XA0): no se puede obtener la exclusión mutua de protección.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="0b1ae-773">NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="0b1ae-774">NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0b1ae-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0b1ae-775">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0b1ae-775">Allowed From</span></span>

<span data-ttu-id="0b1ae-776">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0b1ae-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0b1ae-777">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0b1ae-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```