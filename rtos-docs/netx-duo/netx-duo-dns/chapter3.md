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
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>Capítulo 3: Descripción de los servicios del cliente DNS de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_dns_authority_zone_start_get** *permite buscar el inicio de una zona de autoridad asociada con el nombre de host especificado*.

- **nx_dns_cache_initialize** *permite inicializar una caché de DNS.*

- **nx_dns_cache_notify_clear** *permite borrar la función de notificación completa de la memoria caché.*

- **nx_dns_cache_notify_set** *permite establecer la función de notificación completa de la memoria caché.*

- **nx_dns_cname_get** *permite buscar el nombre de dominio canónico para el alias de nombre de dominio de entrada.*

- **nx_dns_create** *permite crear una instancia de cliente DNS.*

- **nx_dns_delete** *permite eliminar una instancia de cliente DNS.*

- **nx_dns_domain_name_server_get** *permite buscar los servidores de nombres autoritativos para la zona de dominio de entrada.*

- **nx_dns_domain_mail_exchange_get** *permite buscar el intercambio de correo asociado al nombre de host especificado.*

- **nx_dns_domain_service_get** *permite buscar los servicios asociados con el nombre de host especificado.*

- **nx_dns_get_serverlist_size** *permite devolver el tamaño de la lista de servidores del cliente DNS.*

- **nx_dns_info_by_name_get** *permite devolver la dirección IP y la consulta de puertos en el nombre de host de entrada.*

- **nx_dns_ipv4_address_by_name_get** *permite buscar la dirección IPv4 desde el nombre de host especificado.*

- **nxd_dns_ipv6_address_by_name_get** *permite buscar la dirección IPv6 desde el nombre de host especificado.*

- **nx_dns_host_by_address_get** *función de contenedor para que nxd_dns_host_by_address_get busque un nombre de host desde una dirección IP especificada (solo admite direcciones IPv4).*

- **nxd_dns_host_by_address_get** *permite buscar una dirección IP desde el nombre de host de entrada (admite direcciones IPv4 e IPv6).*

- **nx_dns_host_by_name_get** *función de contenedor para que nxd_dns_host_by_address_get busque un nombre de host desde la dirección especificada (solo admite direcciones IPv4).*

- **nxd_dns_host_by_name_get** *permite buscar una dirección IP desde el nombre de host de entrada (admite direcciones IPv4 e IPv6).*

- **nx_dns_host_text_get** *permite buscar los datos de texto para el nombre de dominio de entrada.*

- **nx_dhcp_packet_pool_set**: *permite establecer el grupo de paquetes del cliente DNS*.

- **nx_dns_server_add** *función de contenedor de* nxd_dns_server_add *para agregar un servidor DNS en la dirección especificada a la lista de clientes (solo admite IPv4).*

- **nxd_dns_server_add** *permite agregar un servidor DNS de la dirección IP especificada a la lista de servidores de cliente (admite direcciones IPv4 o IPv6).*

- **nx_dns_server_get** *permite devolver el servidor DNS en la lista de clientes (solo admite direcciones IPv4).*

- **nx_dns_server_get** *permite devolver el servidor DNS en la lista de clientes (admite direcciones IPv4 e IPv6).*

- **nx_dns_server_remove** *función de contenedor de nxd_dns_server_remove para quitar un servidor DNS de la lista de clientes.*

- **nxd_dns_server_remove** *permite quitar un servidor DNS de la dirección IP especificada de la lista de clientes (admite direcciones IPv4 e IPv6).*

- **nx_dns_server_remove_all** *permite quitar todos los servidores DNS de la lista de clientes.*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Buscar el inicio de la zona de autoridad del host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>Descripción

Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SOA con el nombre de dominio especificado para obtener el inicio de la zona de autoridad para el nombre de dominio de entrada. El cliente DNS copia los registros SOA devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

En el cliente DNS de NetX Duo, el tipo de registro SOA, NX_DNS_SOA_ENTRY, se guarda como siete parámetros de 4 bytes, que suman un total de 28 bytes:

- **nx_dns_soa_host_mname_ptr**: puntero al origen de datos principal para esta zona.
- **nx_dns_soa_host_rname_ptr**: puntero al responsable del buzón para esta zona.
- **nx_dns_soa_serial**: número de versión de zona.
- **nx_dns_soa_refresh**: intervalo de actualización.
- **nx_dns_soa_retry**: intervalo entre reintentos de consultas SOA.
- **nx_dns_soa_expire**: duración del tiempo de expiración de SOA.
- **nx_dns_soa_minmum**: campo TTL mínimo en los mensajes de respuesta DNS del nombre de host SOA.

A continuación se muestra el almacenamiento de dos registros SOA. Los registros SOA que contienen datos de longitud fija se introducen empezando por la parte superior del búfer. Los punteros MNAME y RNAME apuntan a los datos de longitud variable (nombres de host) que se almacenan en la parte inferior del búfer. Los registros SOA adicionales se escriben después del primer registro ("registros SOA adicionales...") y sus datos de longitud variable se almacenan encima de los datos de longitud variable de la última entrada ("datos de longitud variable de SOA adicionales"):

![Almacenamiento de dos registros SOA](media/image4.png)

Si la ubicación *record_buffer* de entrada no puede contener todos los datos SOA de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.

Con el número de registros SOA devueltos en **record_count,* la aplicación puede analizar los datos de *record_buffer* y extraer el inicio de las cadenas de nombre de host de la entidad de zona.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre de host para el que se van a obtener datos SOA.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos SOA.
- **buffer_size**: tamaño del búfer que contendrá datos SOA.
- **record_count**: puntero al número de registros SOA recuperados.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos SOA se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

Inicialización de la caché de DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a>Descripción

Este servicio crea e inicializa una caché de DNS.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.
- **cache_ptr**: puntero a la caché de DNS.
- **cache_size**: tamaño de la caché de DNS, en bytes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): la caché de DNS se inicializó correctamente.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_DNS_CACHE_ERROR (0xB7): puntero de caché no válido.
- NX_PTR_ERROR (0x07): puntero de DNS no válido. 
- NX_DNS_ERROR (0xA0): la memoria caché no es alineada de 4 bytes.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Borrar la función de notificación completa de la caché de DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra la función de notificación completa de la memoria caché.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0x07): puntero de DNS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Establecer la función de notificación completa de la caché de DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Descripción

Este servicio establece la función de notificación completa de la memoria caché.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.
- **cache_full_notify_cb**: función de devolución de llamada que se va a invocar cuando la memoria caché se llene.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): la notificación de caché de DNS se estableció correctamente.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0x07): puntero de DNS no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Buscar el nombre canónico del nombre de host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>Descripción

Si NX_DNS_ENABLE_EXTENDED_RR_TYPES se define en *nxd_dns.h*, este servicio envía una consulta de tipo CNAME con el nombre de dominio especificado para obtener el nombre de dominio canónico. El cliente DNS copia la cadena CNAME devuelta en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre de host para el que se van a obtener datos CNAME.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos CNAME.
- **buffer_size**: tamaño del búfer que contendrá datos CNAME.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos CNAME se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

##  <a name="nx_dns_create"></a>nx_dns_create

Crear una instancia de cliente DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente DNS para la instancia de IP creada anteriormente.

> [!IMPORTANT]
> La aplicación debe asegurarse de que la carga de paquetes del grupo de paquetes utilizada por el cliente DNS es lo suficientemente grande para el mensaje DNS máximo de 512 bytes, más los encabezados UDP, IP y Ethernet. Si el cliente DNS crea su propio grupo de paquetes, se define mediante NX_DNS_PACKET_PAYLOAD y NX_DNS_PACKET_POOL_SIZE.

Si la aplicación cliente DNS prefiere proporcionar un grupo de paquetes creado previamente, la carga para el cliente DNS IPv4 debe ser de 512 bytes para el DNS máximo más 20 bytes para el encabezado IP, 8 bytes para el encabezado UDP y 14 bytes para el encabezado Ethernet. En el caso de IPv6, la única diferencia es que el encabezado IP es de 40 bytes, por lo que el paquete debe contener el encabezado IPv6 de 40 bytes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **ip_ptr**: puntero a la instancia de IP creada anteriormente.  
- **domain_name**: puntero al nombre de dominio para la instancia DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): DNS creado correctamente.
- **NX_DNS_ERROR** (0xA0): error de creación de DNS.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

Eliminar una instancia de cliente DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente DNS creada anteriormente y libera sus recursos. 

> [!NOTE]
> Si se define NX_DNS_CLIENT_USER_CREATE_PACKET_POOL y se asignó al cliente DNS un grupo de paquetes definido por el usuario, depende de la aplicación que se elimine el grupo de paquetes del cliente DNS si ya no es necesario.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): cliente DNS eliminado correctamente.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Buscar los servidores de nombres autoritativos para la zona de dominio de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Descripción

Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo NS con el nombre de dominio especificado para obtener los servidores de nombres para el nombre de dominio de entrada. El cliente DNS copia los registros NS devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

En el cliente DNS de NetX Duo, el tipo de datos NS, NX_DNS_NS_ENTRY, se guarda como dos parámetros de 4 bytes:

- **nx_dns_ns_ipv4_address**: dirección IPv4 del servidor de nombres.
- **nx_dns_ns_hostname_ptr**: puntero al nombre de host del servidor de nombres.

El búfer que se muestra a continuación contiene cuatro registros NX_DNS_NS_ENTRY. El puntero a la cadena de nombre de host en cada entrada apunta a la cadena de nombre de host correspondiente en la mitad inferior del búfer:

![Contiene cuatro registros NX_DNS_NS_ENTRY](media/image5.png)

Si la ubicación *record_buffer* de entrada no puede contener todos los datos NS de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.

Con el número de registros NS devueltos en **record_count,* la aplicación puede analizar la dirección IP y el nombre de host de cada registro en la ubicación *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre de host para el que se van a obtener datos NS.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos NS.
- **buffer_size**: tamaño del búfer que contendrá datos NS.
- **record_count**: puntero al número de registros NS recuperados.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos NS se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

Buscar los intercambios de correo para el nombre de host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>Descripción

Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo MX con el nombre de dominio especificado para obtener el intercambio de correo para el nombre de dominio de entrada. El cliente DNS copia los registros MX devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*. 

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

En el cliente DNS de NetX Duo, el tipo de registro de intercambio de correo, NX_DNS_MAIL_EXCHANGE_ENTRY, se guarda como cuatro parámetros que suman un total de 12 bytes:

- **nx_dns_mx_ipv4_address**: dirección IPv4 de intercambio de correo de 4 bytes
- **nx_dns_mx_preference**: preferencia de 2 bytes
- **nx_dns_mx_reserved0**: 2 bytes reservados
- **nx_dns_mx_hostname_ptr**: puntero al nombre de host del servidor de intercambio de correo de 4 bytes

A continuación se muestra un búfer que contiene cuatro registros MX. Cada registro contiene los datos de longitud fija de la lista anterior. El puntero al nombre de host del servidor de intercambio de correo apunta al nombre de host correspondiente en la parte inferior del búfer.

![Un búfer que contiene cuatro registros MX](media/image6.png)

Si la ubicación *record_buffer* de entrada no puede contener todos los datos MX de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.

Con el número de registros MX devueltos en **record_count,* la aplicación puede analizar los parámetros MX, incluido el nombre de host de correo de cada registro en la ubicación *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre de host para el que se van a obtener datos SOA.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos MX.
- **buffer_size**: tamaño del búfer que contendrá datos MX.
- **record_count**: puntero al número de registros MX recuperados.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos MX se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

Buscar los servicios proporcionados por el nombre de host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Descripción

Si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES, este servicio envía una consulta de tipo SRV con el nombre de dominio especificado para buscar los servicios y su número de puerto asociado con el dominio especificado. El cliente DNS copia los registros SRV devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*. 

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

En el cliente DNS de NetX Duo, el tipo de registro del servicio, NX_DNS_SRV_ENTRY, se guarda como seis parámetros que suman un total de 16 bytes: Esto permite almacenar datos SRV de longitud variable de manera eficaz para la memoria:

- **Dirección IPv4 del servidor**: nx_dns_srv_ipv4_address de 4 bytes
- **Prioridad del servidor**: nx_dns_srv_priority de 2 bytes
- **Peso del servidor**: nx_dns_srv_weight de 2 bytes
- **Número de puerto de servicio**: nx_dns_srv_port_number de 2 bytes
- **Reservado para la alineación de 4 bytes**: nx_dns_srv_reserved0 de 2 bytes
- **Puntero al nombre de host del servidor**: *nx_dns_srv_hostname_ptr de 4 bytes

Se almacenan cuatro registros SRV en el búfer proporcionado. Cada registro de NX_DNS_SRV_ENTRY contiene un puntero, *nx_dns_srv_hostname_ptr*, que apunta a la cadena de nombre de host correspondiente en la parte inferior del búfer de registro:

![Cuatro registros SRV](media/image7.png)

Si la ubicación *record_buffer* de entrada no puede contener todos los datos SRV de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.

Con el número de registros SRV devueltos en **record_count,* la aplicación puede analizar los parámetros SRV, incluido el nombre de host del servidor de cada registro en la ubicación *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre de host para el que se van a obtener datos SRV.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos SRV.
- **buffer_size**: tamaño del búfer que contendrá datos SRV.
- **record_count**: puntero al número de registros SRV recuperados.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos SRV se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

Devolver el tamaño de la lista de servidores del cliente DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>Descripción

Este servicio devuelve el número de servidores DNS válidos (tanto IPv4 como IPv6) en la lista de clientes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.  
- **size**: devuelve el número de servidores de la lista.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): el tamaño de la lista de servidores DNS se devolvió correctamente.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Devolver la dirección IP y el puerto del servidor DNS por nombre de host

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio devuelve la dirección IP del servidor y el puerto (registro de servicio) basados en el nombre de host de entrada mediante la consulta de DNS. Si no se encuentra un registro de servicio, esta rutina devuelve una dirección IP cero en el puntero de la dirección de entrada y una devolución de estado de error distinto de cero para indicar un error.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.  
- **host_name**: puntero al búfer de nombre de host.
- **host_address_ptr**: puntero a la dirección que se va a devolver.
- **host_port_ptr**: puntero al puerto que se va a devolver.
- **wait_option**: opción de espera para la respuesta de DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): el registro del servidor DNS se devolvió correctamente.
- **NX_DNS_NO_SERVER** (0XA1): no hay ningún servidor DNS registrado en el cliente para enviar la consulta en el nombre de host.
- **NX_DNS_QUERY_FAILED** (0xA3): error de la consulta de DNS; no hay ninguna respuesta de ningún servidor DNS en la lista del cliente o no existe ningún registro de servicio disponible para el nombre de host de entrada.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Buscar la dirección IPv4 para el nombre de host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía una consulta de tipo A con el nombre de host especificado para obtener las direcciones IP para el nombre de host de entrada. El cliente DNS copia la dirección IPv4 de los registros A devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*.

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

Varias direcciones IPv4 se almacenan en el búfer alineado de 4 bytes, como se muestra a continuación:

![Búfer alineado de 4 bytes con varias direcciones](media/image8.png)

Si el búfer proporcionado no puede contener todos los datos de las direcciones IP, los registros A restantes no se almacenan en *record_buffer*. Esto permite que la aplicación recupere uno, algunos o todos los datos de direcciones IP disponibles en la respuesta del servidor.

Con el número de registros A devueltos en **record_count*, la aplicación puede analizar los datos de dirección IPv4 desde la ubicación *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name_ptr**: puntero al nombre de host para obtener la dirección IPv4.
- **buffer**: puntero a la ubicación en la que se van a extraer datos IPv4.
- **buffer_size**: tamaño del búfer que contendrá datos IPv4.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos IPv4 se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nxd_dns_ipv6_address_by_name_get"></a>nxd_dns_ipv6_address_by_name_get

Buscar la dirección IPv6 para el nombre de host de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía una consulta de tipo AAAA con el nombre de dominio especificado para obtener las direcciones IP para el nombre de dominio de entrada. El cliente DNS copia la dirección IPv6 de los registros AAAA devueltos en la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*. 

> [!NOTE]
> La ubicación *record_buffer* debe tener una alineación de 4 bytes para recibir los datos.

A continuación se muestra el formato de las direcciones IPv6 almacenadas en el búfer alineado de 4 bytes:

![Formato IPv6 del búfer alineado de 4 bytes](media/image9.png)

Si la ubicación *record_buffer* de entrada no puede contener todos los datos AAAA de la respuesta del servidor, dicha ubicación contendrá tantos registros como quepan y devolverá el número de registros del búfer.

Con el número de registros AAAA devueltos en **record_count,* la aplicación puede analizar las direcciones IPv6 de cada registro en la ubicación *record_buffer*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name_ptr**: puntero al nombre de host para obtener la dirección IPv6.
- **buffer**: puntero a la ubicación en la que se van a extraer datos IPv6.
- **buffer_size**: tamaño del búfer que contendrá datos IPv6.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los datos IPv6 se obtuvieron correctamente.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): parámetro que no es de puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Buscar un nombre de host desde una dirección IP

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio solicita la resolución de nombres de la dirección IP suministrada de uno o más servidores DNS especificados anteriormente por la aplicación. Si la operación se realiza correctamente, se devuelve el nombre de host terminado en NULL en la cadena especificada por *host_name_ptr*. Se trata de una función de contenedor para el servicio *nxd_dns_host_by_address_get* y no acepta direcciones IPv6.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de DNS creada anteriormente.
- **ip_address**: dirección IP que se va a resolver en un nombre.
- **host_name_ptr**: puntero al área de destino para el nombre de host.
- **max_host_name_size**: tamaño del área de destino para el nombre de host.
- **wait_option**: define cuánto tiempo esperará el servicio en tics de temporizador para una respuesta del servidor DNS después de cada consulta de DNS y reintento de consulta. Las opciones de espera se definen de la siguiente forma:

  valor de tiempo de espera (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): resolución de DNS correcta.  
- **NX_DNS_TIMEOUT** (0xA2): se agotó el tiempo de espera al obtener la exclusión mutua de DNS.
- **NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.
- **NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

**Ejemplo**
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a>nxd_dns_host_by_address_get

Buscar un nombre de host desde una dirección IP

### <a name="prototype"></a>Prototipo
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio solicita la resolución de nombres de la dirección IPv6 o IPv4 en el argumento de entrada *ip_address* de uno o más servidores DNS especificados anteriormente por la aplicación. Si la operación se realiza correctamente, se devuelve el nombre de host terminado en NULL en la cadena especificada por *host_name_ptr*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de DNS creada anteriormente.
- **ip_address**: dirección IP que se va a resolver en un nombre.
- **host_name_ptr**: puntero al área de destino para el nombre de host.
- **max_host_name_size**: tamaño del área de destino para el nombre de host.
- **wait_option**: define cuánto tiempo esperará el servicio en tics de temporizador para una respuesta del servidor DNS después de cada consulta de DNS y reintento de consulta. Las opciones de espera se definen de la siguiente forma:

  valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): resolución de DNS correcta.  
- **NX_DNS_TIMEOUT** (0xA2): se agotó el tiempo de espera al obtener la exclusión mutua de DNS.
- **NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.
- **NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

**Ejemplo**
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

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Buscar una dirección IP desde el nombre de host

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio solicita la resolución de nombres del nombre suministrado de uno o más servidores DNS especificados anteriormente por la aplicación. Si la operación se realiza correctamente, se devuelve la dirección IP asociada en el destino al que apunta host_address_ptr. Se trata de una función de contenedor para el servicio *nxd_dns_host_by_name_get* y se limita a la entrada de dirección IPv4.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de DNS creada anteriormente.
- **host_name**: puntero al nombre de host.
- **host_address_ptr**: dirección IP del servidor DNS devuelta.
- **wait_option**: define cuánto tiempo esperará el servicio para la resolución de DNS. Las opciones de espera se definen de la siguiente forma:

  valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): resolución de DNS correcta.
- **NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.
- **NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

**Ejemplo**
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

## <a name="nxd_dns_host_by_name_get"></a>nxd_dns_host_by_name_get

Buscar una dirección IP desde el nombre de host

### <a name="prototype"></a>Prototipo
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>Descripción

Este servicio solicita la resolución de nombres de la dirección IP suministrada de uno o más servidores DNS especificados anteriormente por la aplicación. Si la operación se realiza correctamente, se devuelve la dirección IP asociada en un servicio NXD_ADDRESS al que apunta *host_address_ptr*. Si el autor de la llamada establece específicamente la entrada lookup_type en NX_IP_VERSION_V6, este servicio enviará una consulta para una dirección IPv6 de host (registro AAAA). Si el autor de la llamada establece específicamente la entrada lookup_type en NX_IP_VERSION_V4, este servicio enviará una consulta para una dirección IPv4 de host (registro A).

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.
- **host_name**: puntero al nombre de host del que se buscará una dirección IP.
- **host_address_ptr**: puntero al destino de NXD_ADDRESS que contiene la dirección IP.
- **waig_option**: define cuánto tiempo esperará el servicio en tics de temporizador para la respuesta del servidor DNS para cada transmisión y retransmisión de consulta. Las opciones de espera se definen de la siguiente forma:

  valor de tiempo de espera (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor DNS responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecerá suspendido mientras se espera la resolución de DNS.

- **lookup_type**: indica el tipo de búsqueda (A frente a AAAA).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): resolución de DNS correcta.
- **NX_DNS_NO_SERVER** (0XA1): no se especificó ninguna dirección de servidor DNS.
- **NX_DNS_QUERY_FAILED** (0xA3): no se recibió ninguna respuesta a la consulta.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): dirección de entrada nula.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

**Ejemplo**
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

A continuación se muestra otro ejemplo del uso de este servicio de tiempo, esta vez con direcciones IPv4 y tipos de registro A:
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

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Buscar la cadena de texto para el nombre de dominio de entrada

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía una consulta de tipo TXT con el nombre de dominio y el búfer especificados para obtener los datos de cadena arbitrarios.

El cliente DNS copia la cadena de texto del registro TXT de la respuesta del servidor DNS en la ubicación de la memoria *record_buffer*. 

> [!NOTE]
> La ubicación record_buffer no necesita tener una alineación de 4 bytes para recibir los datos.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al cliente DNS.  
- **host_name**: puntero al nombre del host en el que se realizará la búsqueda.
- **record_buffer**: puntero a la ubicación en la que se van a extraer datos TXT.
- **buffer_size**: tamaño del búfer que contendrá datos TXT.
- **wait_option**: opción de espera que recibirá la respuesta del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): se obtuvo correctamente la cadena TXT.
- **NX_DNS_NO_SERVER** (0xA1): la lista de servidores del cliente está vacía.
- **NX_DNS_QUERY_FAILED** (0XA3): no se recibió ninguna respuesta DNS válida.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_PARAM_ERROR (0xA8): entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

######   
Ejemplo
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

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Establecer el grupo de paquetes del cliente DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Descripción

Este servicio establece un grupo de paquetes creado anteriormente como el grupo de paquetes del cliente DNS. El cliente DNS usará este grupo de paquetes para enviar consultas de DNS, por lo que la carga de paquetes no debe ser inferior al valor de NX_DNS_PACKET_PAYLOAD, que incluye los encabezados Ethernet, IP y UDP, y se define en *nxd_dns.h.* 

> [!NOTE]
> *C* uando se elimina el cliente DNS, el grupo de paquetes no se elimina con este y es responsabilidad de la aplicación eliminarlo cuando ya no es necesario.
>
> Este servicio solo está disponible si la opción de configuración NX_DNS_CLIENT_USER_CREATE_PACKET_POOL se define en *nxd_dns.h*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero a la instancia de cliente DNS creada anteriormente.
- **pool_ptr** Puntero a un grupo de paquetes creado previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): operación finalizada correctamente.
- **NX_NOT_ENABLED** (0x14): cliente no configurado para esta opción.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Agregar dirección IP del servidor DNS

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Descripción

Este servicio agrega un servidor DNS IPv4 a la lista de servidores.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.  
- **server_address**: dirección IP del servidor DNS

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): servidor agregado correctamente.
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0X17): no se permiten más servidores DNS (la lista está llena).
- **NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_BAD_ADDRESS_ERROR (0xA4): entrada de dirección de servidor nula.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

Agregar servidor DNS a la lista del cliente

### <a name="prototype"></a>Prototipo
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Descripción

Este servicio agrega la dirección IP de un servidor DNS a la lista de servidores del cliente DNS. El valor de server_address puede ser una dirección IPv4 o IPv6. Si el cliente desea poder acceder al mismo servidor mediante la dirección IPv4 o la dirección IPv6, debe agregar ambas direcciones IP como entradas a la lista de servidores.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.
- **server_address**: puntero al servicio NXD_ADDRESS que contiene la dirección IP del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): servidor agregado correctamente.
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0X17): no se permiten más servidores DNS (la lista está llena). 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- **NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0x07): entrada de puntero no válida.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_BAD_ADDRESS_ERROR (0xA4): entrada de dirección de servidor nula.
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Devolver un servidor DNS IPv4 de la lista de clientes

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>Descripción

Este servicio devuelve la dirección del servidor DNS IPv4 de la lista de servidores en el índice especificado. 

> [!NOTE]
> El índice es de base cero. Si el índice de entrada supera el tamaño de la lista de clientes DNS, se encuentra una dirección IPv6 en dicho índice o se encuentra una dirección nula en el índice especificado, se devuelve un error. Se puede llamar al servicio *nx_dns_get_serverlist_size* primero para obtener el número de servidores DNS en la lista de clientes.

Este servicio solo admite direcciones IPv4. Llama al servicio *nxd_dns_server_get* que admite tanto direcciones IPv4 como IPv6.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.  
- **index**: índice de la lista de servidores del cliente DNS.
- **dns_server_address**: puntero a la dirección IP del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): servidor devuelto correcto.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9): el índice apunta a una ranura vacía.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): el índice apunta a una dirección nula.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

Devolver un servidor DNS de la lista de clientes

### <a name="prototype"></a>Prototipo
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>Descripción

Este servicio devuelve la dirección IP del servidor DNS de la lista de servidores en el índice especificado. 

> [!NOTE]
> El índice es de base cero. Si el índice de entrada supera el tamaño de la lista de clientes DNS o se encuentra una dirección nula en el índice especificado, se devuelve un error. Se puede llamar al servicio *nx_dns_get_serverlist_size* primero para obtener el número de servidores DNS en la lista de servidores.

Este servicio es compatible con las direcciones IPv4 e IPv6.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.  
- **index**: índice de la lista de servidores del cliente DNS.
- **dns_server_address**: puntero a la dirección IP del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): la dirección IP del servidor se devolvió correctamente.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9): el índice apunta a una ranura vacía.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): el índice apunta a una dirección de servidor nula.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8): entrada que no es de puntero no válida.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Quitar un servidor DNS IPv4 de la lista de clientes

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Descripción

Este servicio quita un servidor DNS IPv4 de la lista de clientes. Es una función de contenedor para *nxd_dns_server_remove*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.
- **server_address**: dirección IP del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): el servidor DNS se quitó correctamente.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9): el servidor no está en la lista de clientes.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): entrada de dirección de servidor nula.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

Quitar un servidor DNS de la lista de clientes

### <a name="prototype"></a>Prototipo
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Descripción

Este servicio quita un servidor DNS de la dirección IP especificada de la lista de clientes. La dirección IP de entrada acepta direcciones IPv4 e IPv6. Una vez quitado el servidor, el resto de los servidores baja un índice en la lista para ocupar la ranura vacía.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.
- **server_address**: puntero a los datos NXD_ADDRESS del servidor DNS que contienen la dirección IP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): el servidor DNS se quitó correctamente.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9): el servidor no está en la lista de clientes.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4): entrada de dirección de servidor nula.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3): no se puede procesar el registro con IPv6 deshabilitado.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2): el índice apunta a un tipo de dirección no válido (p. ej., IPv6).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
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

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Quitar todos los servidores DNS de la lista de clientes

### <a name="prototype"></a>Prototipo
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>Descripción

Este servicio quita todos los servidores DNS de la lista de clientes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dns_ptr**: puntero al bloque de control DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00): los servidores DNS se quitaron correctamente.
- **NX_DNS_ERROR** (0XA0): no se puede obtener la exclusión mutua de protección.
- NX_PTR_ERROR (0X07): puntero de DNS o IP no válidos.
- NX_CALLER_ERROR (0x11): autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```