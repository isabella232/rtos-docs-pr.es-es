---
title: 'Capítulo 1: Introducción al cliente DNS de Azure RTOS NetX Duo'
description: El servicio DNS proporciona una base de datos distribuida que contiene la asignación entre los nombres de dominio y las direcciones IP físicas.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e878d32d6bcf514bb75a76b51e66c4d267b1a5b34f6c4b2df6ab231e5814ffc5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792065"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>Capítulo 1: Introducción al cliente DNS de Azure RTOS NetX Duo

El servicio DNS proporciona una base de datos distribuida que contiene la asignación entre los nombres de dominio y las direcciones IP físicas. La base de datos se denomina *distribuida* porque no hay ninguna entidad única en Internet que contenga la asignación completa. Una entidad que mantiene una parte de la asignación se denomina "servidor DNS". Internet se compone de numerosos servidores DNS, cada uno de los cuales contiene un subconjunto de la base de datos. Los servidores DNS también responden a las solicitudes de cliente DNS para la información de asignación de nombres de dominio, pero solo si el servidor en cuestión tiene la asignación solicitada.

El protocolo de cliente DNS para NetX Duo proporciona a la aplicación servicios para solicitar información de asignación de uno o más servidores DNS.

## <a name="dns-client-setup"></a>Configuración del cliente DNS

Para que funcione correctamente, el paquete del cliente DNS requiere que ya se haya creado una instancia de IP de NetX DUO.

Después de crear el cliente DNS, la aplicación debe agregar uno o más servidores DNS a la lista de servidores que mantiene el cliente DNS. Para agregar servidores DNS, la aplicación usa el servicio *nxd_dns_server_add*. También se puede usar el servicio de cliente DNS de NetX Duo *nx_dns_server_add* para agregar servidores. Sin embargo, solo acepta direcciones IPv4 y se recomienda que los desarrolladores usen el servicio de *nxd_dns_server_add* en su lugar.

Si la opción NX_DNS_IP_GATEWAY_SERVER está habilitada y la dirección de la puerta de enlace de la instancia IP es distinta de cero, la puerta de enlace de la instancia de IP se agrega automáticamente como servidor DNS principal. Si no se conoce la información del servidor DNS de forma estática, también se puede derivar a través del Protocolo de configuración dinámica de host (DHCP) para NetX Duo. Consulte la guía de usuario de DHCP de Next Duo para más información.

El cliente DNS requiere un grupo de paquetes para la transmisión de mensajes DNS. De forma predeterminada, el cliente DNS crea este grupo de paquetes cuando se llama al servicio *nx_dns_create*. Las opciones de configuración NX_DNS_PACKET_PAYLOAD_UNALIGNED y NX_DNS_PACKET_POOL_SIZE permiten que la aplicación determine la carga de paquetes y el tamaño del grupo de paquetes (por ejemplo, el número de paquetes) de este grupo de paquetes, respectivamente. Estas opciones se describen en la sección "Opciones de configuración" del segundo capítulo.

Una alternativa a que el cliente DNS cree su propio grupo de paquetes es que la aplicación cree el grupo de paquetes y lo establezca como el grupo de paquetes del cliente DNS mediante el servicio *nx_dns_packet_pool_set*. Para ello, se debe definir la opción NX_DNS_CLIENT_USER_CREATE_PACKET_POOL. Esta opción también requiere un grupo de paquetes creado anteriormente mediante *nx_packet_pool_create* como la entrada del puntero del grupo de paquetes para *nx_dns_packet_pool_set*. Cuando se elimina la instancia del cliente DNS, la aplicación es responsable de eliminar el grupo de paquetes del cliente DNS si se habilita NX_DNS_CLIENT_USER_CREATE_PACKET_POOL y ya no es necesario.

> [!NOTE] 
> En el caso de las aplicaciones que eligen proporcionar su propio grupo de paquetes mediante la opción de NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, el tamaño del paquete debe poder contener el tamaño de mensaje máximo de DNS (512 bytes) más espacios para el encabezado UDP, el encabezado IPv4 o IPv6 y el encabezado MAC.

## <a name="dns-messages"></a>Mensajes DNS

El servicio DNS tiene un mecanismo muy sencillo para obtener la asignación entre los nombres de host y las direcciones IP. Para obtener una asignación, el cliente DNS prepara un mensaje de consulta de DNS que contiene el nombre o la dirección IP que debe resolverse. A continuación, el mensaje se envía al primer servidor DNS de la lista de servidores. Si el servidor tiene este tipo de asignación, responde al cliente DNS con un mensaje de respuesta DNS que contiene la información de asignación solicitada. Si el servidor no responde, el cliente DNS consulta el servidor siguiente de la lista hasta haber consultado todos sus servidores DNS. Si no recibe ninguna respuesta de ninguno de sus servidores DNS, el cliente DNS tiene lógica de reintento para retransmitir el mensaje DNS. Al volver a enviar una consulta de DNS, se duplica el tiempo de espera de retransmisión. Este proceso continúa hasta que se alcanza el tiempo de espera de transmisión máximo (definido como NX_DNS_MAX_RETRANS_TIMEOUT en *nxd_dns.h*) o hasta que se obtiene una respuesta correcta de ese servidor.

El cliente DNS de NetX Duo puede realizar búsquedas de direcciones IPv6 (tipo AAAA) y búsquedas de direcciones IPv4 (tipo A). Para ello, debe especificar la versión de la dirección IP en la llamada *nxd_dns_host_by_name_get*. El cliente DNS puede realizar búsquedas inversas de direcciones IP (consultas de tipo PTR) para obtener los nombres de host web mediante *nxd_dns_host_by_address_get*. El cliente DNS de NetX Duo sigue siendo admitiendo *nx_dns_host_by_name_get* y *nx_dns_host_by_address_get*, que son los servicios equivalentes, pero están limitados a la comunicación de red IPv4. Sin embargo, se recomienda a los desarrolladores que porten las aplicaciones cliente DNS existentes a los servicios *nxd_dns_host_by_name_get* y *nxd_dns_host_by_address_get*.

La mensajería DNS emplea el protocolo UDP para enviar solicitudes y respuestas de campo. Un servidor DNS escucha en el número de puerto 53 las consultas de los clientes. Por lo tanto, los servicios UDP deben estar habilitados en NetX Duo mediante el servicio ***nx_udp_enable** _ en una instancia de IP creada anteriormente (_*_nx_ip_create_**).

En este momento, el cliente DNS está listo para aceptar solicitudes de la aplicación y enviar consultas de DNS.

## <a name="extended-dns-resource-record-types"></a>Tipos de registros de recursos DNS ampliados

Si la opción NX_DNS_ENABLE_EXTENDED_RR_TYPES está habilitada, el cliente DNS de NetX Duo también admite las siguientes consultas de tipo de registro:

- CNAME: contiene el nombre canónico de un alias.
- TXT: contiene una cadena de texto.
- NS: contiene un servidor de nombres autoritativo.
- SOA: contiene el inicio de una zona de autoridad.
- MX: se usa para intercambiar correo.
- SRV: contiene información sobre el servicio ofrecido por el dominio.

A excepción de los tipos de registro CNAME y TXT, la aplicación debe proporcionar un búfer alineado de 4 bytes para recibir el registro de datos DNS.

En el cliente DNS de NetX Duo, los datos de registro se almacenan para maximizar la eficiencia del uso del espacio del búfer.

A continuación se muestra un ejemplo de un búfer de registro de longitud fija (tipo de registro AAAA):

![Búfer de registro de longitud fija](media/image2.png)

En el caso de las consultas cuyos tipos de registro tienen una longitud de datos variable, como registros NS cuyos nombres de host son de longitud variable, el cliente DNS de NetX Duo guarda los datos como se indica a continuación. El búfer proporcionado en la consulta del cliente DNS se organiza en un área de datos de longitud fija y un área de memoria no estructurada. La parte superior del búfer de memoria se organiza en entradas de registro alineadas de 4 bytes. Cada entrada de registro contiene la dirección IP y un puntero a los datos de longitud variable de esa dirección IP. Los datos de longitud variable de cada dirección IP se almacenan en la memoria del área no estructurada a partir del final del búfer de memoria. Los datos de longitud variable de cada entrada de registro sucesiva se guardan en la siguiente memoria de área adyacente a los datos de variables de las entradas de registro anteriores. Por lo tanto, los datos de la variable "aumentan" hacia el área estructurada de la memoria que contiene las entradas del registro hasta que no hay memoria suficiente para almacenar otra entrada de registro ni datos variables.

Esto se puede observar en la siguiente ilustración:

![Figura 2](media/image3.png)

El ejemplo del almacenamiento de datos del nombre de dominio DNS (NS) se muestra arriba.

Las consultas de cliente DNS de NetX Duo que usan el formato de almacenamiento de registros devuelven el número de registros guardados en el búfer de registro. Esta información permite a la aplicación extraer registros NS del búfer de registro.

A continuación se muestra un ejemplo de una consulta de cliente DNS que almacena datos DNS de longitud variable mediante este formato de almacenamiento de registros:

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


Puede encontrar más detalles en el capítulo 3, "Descripción de los servicios del cliente DNS".

## <a name="dns-cache"></a>Caché de DNS

Si NX_DNS_CACHE_ENABLE está habilitado, el cliente DNS de NetX Duo es compatible con la característica de caché de DNS. Después de crear el cliente DNS, la aplicación puede llamar a la API *nx_dns_cache_initialize ()* para establecer la memoria caché de DNS especial. Si se habilita la característica de caché de DNS, el cliente DNS encontrará la respuesta disponible en la caché de DNS antes de que empiece a enviar la consulta de DNS. Si encuentra la respuesta disponible, devuélvala directamente a la aplicación; de lo contrario, el cliente DNS enviará un mensaje de consulta al servidor DNS y esperará la respuesta. Cuando el cliente DNS obtiene el mensaje de respuesta y hay disponible una memoria caché libre, el cliente DNS devuelve la respuesta a la aplicación y también la agrega como un registro de recursos a la caché de DNS.

Cada uno responde a una estructura de datos *NX_DNS_RR* (registro de recursos) en la caché. Las cadenas (nombre y datos del registro de recursos) de los registros son de longitud variable, por lo que no se almacenan en la estructura NX_DNS_RR. El registro contiene punteros a la ubicación de memoria real donde se almacenan las cadenas. La tabla de cadenas y los registros comparten la caché. Los registros se almacenan desde el principio de la caché y aumentan hacia el final de esta. La tabla de cadenas comienza desde el final de la caché y aumenta hacia el principio de esta. Cada cadena de la tabla de cadenas tiene un campo de longitud y un campo de contador. Cuando se agrega una cadena a la tabla de cadenas, si la misma cadena ya está presente en la tabla, el valor del contador se incrementa y no se asigna ninguna memoria para la cadena. La caché se considera llena si no se le pueden agregar más registros de recursos ni cadenas nuevas.

## <a name="dns-client-limitations"></a>Limitaciones del cliente DNS

El cliente DNS admite una solicitud de DNS a la vez. Los subprocesos que intentan realizar otra solicitud de DNS se bloquean temporalmente hasta que se completa la solicitud de DNS anterior.

El cliente DNS de NetX Duo no usa datos de respuestas autoritativas para reenviar consultas de DNS adicionales a otros servidores DNS.

## <a name="dns-rfcs"></a>Documentos RFC de DNS

El servicio DNS de NetX Duo es compatible con los siguientes documentos RFC:

- RFC1034 DOMAIN NAMES - CONCEPTS AND FACILITIES (RFC1034: NOMBRES DE DOMINIO. CONCEPTOS E INSTALACIONES)
- RFC1035 DOMAIN NAMES - IMPLEMENTATION AND SPECIFICATION (RFC1035: NOMBRES DE DOMINIO. IMPLEMENTACIÓN Y ESPECIFICACIÓN)
- RFC1480 The US Domain (RFC1480: El dominio de EE. UU.)
- RFC 2782 A DNS RR for specifying the location of services (DNS SRV) [RFC 2782: Registro de recursos DNS para especificar la ubicación de los servicios (DNS SRV)]
- RFC 3596 DNS Extensions to Support IP Version 6 [RFC 3596: Extensiones de DNS para admitir IP versión 6]