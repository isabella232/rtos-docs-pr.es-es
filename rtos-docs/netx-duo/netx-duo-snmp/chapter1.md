---
title: 'Capítulo 1: Introducción a SNMP de Azure RTOS NetX Duo'
description: La implementación de SNMP de NetX Duo es la de un agente de SNMP. Un agente es responsable de responder a los comandos del administrador de SNMP y enviar las capturas controladas por eventos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814574"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Capítulo 1: Introducción a SNMP de Azure RTOS NetX Duo

El Protocolo simple de administración de redes (SNMP) es un protocolo diseñado para administrar dispositivos en Internet. SNMP es un protocolo que emplea los servicios del Protocolo de datagramas de usuario (UDP) sin conexión para realizar su función de administración. La implementación de SNMP de Azure RTOS NetX Duo es la de un agente de SNMP. Un agente es responsable de responder a los comandos del administrador de SNMP y enviar las capturas controladas por eventos. 

SNMP de NetX Duo admite la comunicación IPv4 e IPv6 con los administradores de SNMP. Las aplicaciones SNMP de NetX deben compilarse y ejecutarse en el protocolo SNMP de NetX Duo. Sin embargo, se recomienda que el desarrollador porte las aplicaciones SNMP existentes para usar los servicios equivalentes "Duo". Por ejemplo, al enviar mensajes de captura de SNMP, los siguientes servicios "Duo" deben reemplazar su equivalente de NetX:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Para obtener más información, consulte el capítulo **Descripción de los servicios del agente SNMP** de este manual del usuario.

## <a name="netx-duo-snmp-agent-requirements"></a>Requisitos del agente de SNMP de NetX Duo

El paquete de SNMP de NetX Duo requiere que ya se haya creado una instancia de IP. Además, UDP debe estar habilitado en la misma instancia de IP.

El agente de SNMP de NetX Duo tiene varios requisitos adicionales. En primer lugar, requiere acceso al puerto 161 para controlar todas las solicitudes del administrador de SNMP. También requiere acceso al puerto 162 para enviar mensajes de captura al administrador.

Para usar el agente de SNMP de NetX Duo a través de IPv6 y obtener objetos IPv6, IPv6 debe estar habilitado en NetX Duo. Consulte la ***guía del usuario de NetX Duo*** para obtener más detalles sobre cómo habilitar la instancia de IP para servicios IPv6.

## <a name="netx-duo-snmp-constraints"></a>Restricciones de SNMP de NetX Duo

El protocolo SNMP de NetX Duo implementa las versiones 1, 2 y 3 de SNMP. La implementación de SNMPv3 admite la autenticación MD5 y SHA y el cifrado DES. Esta versión del agente de SNMP de NetX Duo tiene las siguientes restricciones:

1. Debe haber un agente de SNMP por instancia de IP de NetX.
2. No se admite RMON.
3. No se admiten los mensajes informativos de SNMP v3.
4. No se admiten los tipos de datos OPAQUE y NSAP.
5. Las direcciones IPv6 se definen como cadenas de octetos, y la aplicación se encarga de la comprobación de formato.

## <a name="snmp-object-names"></a>Nombres de objeto de SNMP

El protocolo SNMP está diseñado para administrar dispositivos en Internet. Para ello, cada dispositivo administrado de SNMP tiene un conjunto de objetos definidos por la estructura de información de administración (SMI), tal y como se especifica en el protocolo RFC 1155. La estructura es un tipo de árbol jerárquico con una estructura similar a la siguiente:

![Diagrama de la estructura de la información de administración.](media/image3.png)

Cada nodo del árbol es un objeto. El objeto "dod" del árbol se identifica mediante la notación 1.3.6, mientras que el objeto "Internet" del árbol se identifica mediante la notación 1.3.6.1. Todos los nombres de objeto de SNMP comienzan con la notación 1.3.6.

Un administrador de SNMP usa esta notación de objeto para especificar qué objeto del dispositivo quiere obtener o establecer. El agente de SNMP de NetX Duo interpreta dichas solicitudes del administrador y proporciona mecanismos para que la aplicación realice la operación solicitada.

## <a name="snmp-manager-requests"></a>Solicitudes del administrador del SNMP

SNMP tiene un mecanismo sencillo para administrar dispositivos. Existe un conjunto de comandos de SNMP estándar que emite el administrador de SNMP para el dispositivo de SNMP en el *puerto 161*. A continuación, se muestran algunos de los comandos básicos del administrador de SNMP:

| Comando de SNMP | Significado                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Obtiene el objeto especificado.*                                       |
| GETNEXT      | *Obtiene el siguiente objeto lógico después del identificador de objeto especificado.*      |
| GETBULK      | *Obtiene varios objetos lógicos después del identificador de objeto especificado.* |
| SET          | *Establece el objeto especificado.*                                       |

Estos comandos se codifican en el formato de notación de sintaxis abstracta uno (ASN.1) y residen en la carga del paquete UDP enviado por el administrador de SNMP. El agente de SNMP de NetX Duo procesa la solicitud y, a continuación, llama a la rutina de control correspondiente especificada en la llamada ***nx_snmp_agent_create***.

## <a name="netx-duo-snmp-agent-traps"></a>Capturas del agente de SNMP de NetX Duo

El agente de SNMP de NetX Duo proporciona la capacidad de alertar también a un administrador de SNMP de eventos de forma asincrónica. Esto se hace a través de un comando de captura de SNMP. Existe una API única para cada versión de SNMP para enviar capturas a un administrador de SNMP. De forma predeterminada, las capturas se envían al administrador de SNMP en el puerto 162.

El agente de SNMP de NetX Duo proporciona claves de seguridad independientes para los mensajes de captura de SNMPv3. Para ello, la aplicación SNMP debe crear un conjunto de claves distinto de las que se aplican a las respuestas a las solicitudes del administrador. La seguridad de captura permite al agente de SNMP utilizar contraseñas iguales o distintas para la autenticación y la privacidad. Para obtener más información acerca de la creación de claves de seguridad, consulte el apartado **Cifrado y autenticación de SNMP de NetX Duo** en la sección siguiente.

En la parte superior del archivo *nxd_snmp.h* se enumera una lista de variables de captura de SNMP estándar:

| Variables                                 | Value  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

Para incluir estas variables en el mensaje de captura, el argumento de entrada trap_type en *nx_snmp_agent_trapv2_send* (SNMPv2) o *nx_snmp_agent_trapv3_send* (SNMPv3) se establece en el valor enumerado de estas variables. A continuación, se muestra un ejemplo para que SNMPv2 notifique al administrador de SNMP un evento de inicio en frío:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Para incluir variables de propiedad en el mensaje de captura, el argumento de entrada trap_type se establece en NX_SNMP_TRAP_CUSTOM y el argumento de entrada de la lista de capturas contiene los datos de propiedad. Tenga en cuenta que el mensaje de captura contendrá el tiempo de actividad del sistema (1.3.6.1.6.3.1.1.4.1.0). A continuación se muestra un ejemplo para SNMPv2:

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>Autenticación y cifrado de SNMP de NetX Duo

Existen dos tipos de autenticación: *básica* e *implícita*. La autenticación básica equivale al *nombre de usuario* simple de texto sin formato que se encuentra en muchos protocolos. En la autenticación SNMP básica, el usuario simplemente verifica que el nombre de usuario proporcionado es válido para realizar operaciones SNMP. La autenticación básica es la única opción para las versiones 1 y 2 de SNMP.

La principal desventaja de la autenticación básica es que el nombre de usuario se transmite en texto sin formato. La autenticación implícita SNMPv3 soluciona este problema, ya que no transmite nunca el nombre de usuario en texto sin formato. En su lugar, se utiliza un algoritmo para derivar un hash de 96 bits del nombre de usuario, el motor de contexto y otra información. El agente de SNMP de NetX Duo admite los algoritmos hash MD5 y SHA.

Para habilitar la autenticación, el agente de SNMP debe establecer su identificador de motor de contexto mediante el servicio *nx_snmp_agent_context_engine_set*. El identificador del motor de contexto se usa en la creación de la clave de autenticación.

El cifrado de datos SNMPv3 está disponible mediante el algoritmo DES. El cifrado requiere que se habilite la autenticación (no se pueden cifrar los datos sin establecer los parámetros de autenticación).

Para crear claves de privacidad y autenticación, se usa la siguiente API:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

A continuación, el agente de SNMP se debe configurar para usar estas claves. Para registrar una clave con el agente de SNMP, se usa la siguiente API:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Se pueden crear claves independientes para los mensajes de captura. Para aplicar claves para mensajes de captura, hay disponibles las siguientes API:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Para deshabilitar la autenticación o el cifrado de los mensajes de respuesta y enviar capturas, use estos servicios con la entrada de puntero de clave establecida en NULL.

## <a name="netx-duo-snmp-community-strings"></a>Cadenas de comunidad de SNMP de NetX Duo

El agente de SNMP de NetX Duo admite cadenas de comunidad públicas y privadas. La cadena pública se establece con el servicio *nx_snmp_agent _public_string_set*. La cadena privada del agente de SNMP de NetX Duo se establece mediante el servicio *nx_snmp_agent_private_string_set*.

## <a name="netx-duo-snmp-username-callback"></a>Devolución de llamada de nombre de usuario SNMP de NetX Duo

El paquete del agente de SNMP de NetX Duo permite que la aplicación especifique (a través de la llamada ***nx_snmp_agent_create***) una devolución de llamada de nombre de usuario a la que se llama cuando se empieza a administrar cada solicitud de cliente SNMP.

La rutina de devolución de llamada proporciona el nombre de usuario al agente de SNMP de NetX Duo. Si el nombre de usuario proporcionado es válido o si no se necesita ninguna comprobación de nombre de usuario para responder a la solicitud, la devolución de llamada del nombre de usuario debe devolver el valor **NX_SUCCESS**. De lo contrario, la rutina debe devolver **NX_SNMP_ERROR** para indicar que el nombre de usuario especificado no es válido.

El formato de la rutina de devolución de llamada del nombre de usuario de la aplicación se define a continuación:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Los parámetros de entrada se definen de la manera siguiente:

| Parámetro | Significado                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Puntero al agente de SNMP que realiza la llamada                        |
| username  | Destino del puntero al nombre de usuario solicitado |

En el caso de las sesiones SNMPv1 y SNMPv2/v2C, la aplicación deberá examinar la cadena de comunidad en una solicitud de SNMP entrante para determinar si la solicitud de SNMP tiene una cadena de comunidad válida. Hay varios servicios que puede usar la aplicación SNMP para hacerlo.

La aplicación SNMP puede consultar si la solicitud actual del administrador de SNMP es de tipo GET (por ejemplo, GET, GETNEXT o GETBULK) o SET en la solicitud mediante este servicio:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Si la solicitud es de tipo GET, la aplicación comparará la cadena de la comunidad de entrada con la cadena pública del agente de SNMP:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

De igual manera, si la solicitud es de tipo SET, la aplicación querrá comparar la cadena de comunidad de entrada con la cadena privada del agente de SNMP:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Los valores devueltos is_public e is_private indican respectivamente si la cadena de comunidad de entrada es una cadena de comunidad privada o pública válida.

El valor devuelto de la rutina de devolución de llamada de nombre de usuario indica si el nombre de usuario es válido. Se devuelve el valor **NX_SUCCESS** si el nombre de usuario es válido o **NX_SNMP_ERROR** si no lo es.

## <a name="netx-duo-snmp-agent-get-callback"></a>Devolución de llamada GET del agente de SNMP de NetX Duo

La aplicación debe establecer una rutina de devolución de llamada para controlar las solicitudes del objeto GET del administrador de SNMP. La devolución de llamada recupera el valor del objeto especificado en la solicitud.

La rutina de devolución de llamada de la solicitud GET de la aplicación se define a continuación:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Los parámetros de entrada se definen de la manera siguiente:

| Parámetro        | Significado |
|------------------|----------------------------------|
| *agent_ptr*        | Puntero al agente de SNMP que realiza la llamada |
| object_requested | Cadena ASCII que representa el identificador de objeto para el que se realiza la operación GET. |
| object_data      | Estructura de datos que contiene el valor recuperado por la devolución de llamada. Se puede establecer con una serie de API SNMP de NetX Duo que se describen a continuación. |

> [!NOTE]
> *En el caso de las cadenas de octeto, el objeto debe tener asignada la longitud para que la función interna la conozca, ya que la devolución de llamada no tiene ningún argumento de longitud:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Dado que la devolución de llamada GET no conoce el tipo de datos, no es necesario comprobarlo. La longitud no tendrá ningún efecto en las cadenas o tipos numéricos que estén delimitados con valores NULL.

A continuación, llame a la función interna:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**. Si se detecta algún otro error, se debe devolver el código **NX_SNMP_ERROR**.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>Devolución de llamada GETNEXT del agente de SNMP de NetX Duo

La aplicación también debe establecer la rutina de devolución de llamada para las solicitudes del objeto GETNEXT desde el administrador de SNMP. La devolución de llamada GETNEXT recupera el valor del siguiente objeto especificado por la solicitud.

La rutina de devolución de llamada de la solicitud GETNEXT de la aplicación se define a continuación:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Los parámetros de entrada se definen de la manera siguiente:

| Parámetro        | Significado |
|------------------|-------------------------------------------|
| *agent_ptr*        | Puntero al agente de SNMP que realiza la llamada |
| object_requested | Cadena ASCII que representa el identificador de objeto para el que es la operación GETNEXT. |
| object_data      | Estructura de datos que contiene el valor recuperado por la devolución de llamada. Se puede establecer con una serie de API SNMP de NetX Duo que se describen a continuación. |

Al igual que sucede con las devoluciones de llamada GET, los objetos con datos de cadenas de octeto deben tener asignada la longitud para que la función interna la conozca, ya que la devolución de llamada no tiene ningún argumento de longitud:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Dado que la devolución de llamada GET no conoce el tipo de datos, no es necesario comprobarlo. La longitud no tendrá ningún efecto en las cadenas o tipos numéricos que estén delimitados con valores NULL.

A continuación, llame a la función interna:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**. Si se detecta algún otro error, se debe devolver el código **NX_SNMP_ERROR**.

## <a name="netx-duo-snmp-agent-set-callback"></a>Devolución de llamada SET del agente de SNMP de NetX Duo

La aplicación debe establecer la rutina de devolución de llamada para controlar las solicitudes del objeto SET del administrador de SNMP. La devolución de llamada SET establece el valor del objeto especificado por la solicitud.

La rutina de devolución de llamada de la solicitud SET de la aplicación se define a continuación:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Los parámetros de entrada se definen de la manera siguiente:

| Parámetro        | Significado |
|------------------|-------- |
| *agent_ptr*      | Puntero al agente de SNMP que realiza la llamada |
| object_requested | Cadena ASCII que representa el identificador de objeto para el que es la operación SET. |
| object_data      | Estructura de datos que contiene el nuevo valor para el objeto especificado. La operación real se puede realizar con la API de SNMP de NetX Duo que se describe a continuación. |

Tenga en cuenta que, para las cadenas de octetos, la devolución de llamada SET debe actualizar la tabla MIB con la longitud de los datos, ya que el agente de SNMP ha analizado los datos y conoce el tipo y la longitud:

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**.

Si el host de SNMP de NetX Duo ha creado cadenas de comunidad privadas y el emisor de SNMP de la solicitud SET no tiene la cadena privada coincidente, es posible que se devuelva el error **NX_SNMP_ERROR_NOACCESS**. Si se detecta algún otro error, se devolverá el código **NX_SNMP_ERROR**.

> [!NOTE]
> *Aunque el agente de SNMP de NetX Duo proporciona una base de datos MIB de SNMP con la distribución, esta es principalmente para fines de prueba y desarrollo. Probablemente, el desarrollador necesitará una base de datos MIB de propiedad para una aplicación SNMP profesional.*

## <a name="changing-snmp-version-at-run-time"></a>Cambio de la versión de SNMP en tiempo de ejecución

El host de agente de SNMP puede cambiar la versión de SNMP para cada una de las tres versiones en tiempo de ejecución mediante el servicio *nx_snmp_agent_set_version*. El agente de SNMP se habilita de forma predeterminada para las tres versiones cuando se crea el agente de SNMP en *nx_snmp_agent_create*. Sin embargo, la aplicación puede limitarlo a un subconjunto de todas las versiones.

> [!NOTE]
> *Si las opciones de configuración NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 o NX_SNMP_DISABLE_V3 están definidas, esta función no tendrá ningún efecto cuando se habiliten las versiones afectadas.*

El agente de SNMP puede recuperar la versión de SNMP del paquete de SNMP más reciente recibido mediante el servicio *nx_snmp_agent_get_current_version*.

## <a name="snmpv3-discovery"></a>Detección de SNMPv3

Si el agente de SNMP está habilitado para SNMPv3, este responderá a las solicitudes de detección del administrador de SNMP. Esta solicitud contiene datos de parámetros de seguridad con valores NULL para el identificador del motor autoritativo, el nombre de usuario, el recuento de arranques y el tiempo de arranque. Los parámetros de autenticación no se aplican al mensaje DISCOVERY. La lista de enlaces de variables de la solicitud está vacía (no contiene ningún elemento). El agente de SNMP responde con un recuento y un tiempo de arranque de cero y la lista de enlaces de variables que contiene un elemento, *usmStatsUnknownEngineIDs*, que es el recuento de solicitudes recibidas con un identificador de motor desconocido (NULL). En la solicitud GETNEXT subsiguiente del explorador/administrador, los datos de arranque y los parámetros de seguridad se rellenan solo si está habilitada la seguridad. Si es así, también se enviará una actualización de datos NotInTime en la PDU. Los parámetros de seguridad, como la autenticación, demuestran la identidad del agente para el administrador.

Puede encontrar información más detallada sobre la autenticación SNMPv3 en el protocolo RFC 3414 "Modelo de seguridad basado en el usuario (USM) para la versión 3 del Protocolo simple de administración de redes (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>RFC de SNMP de NetX Duo

SNMP de NetX Duo es compatible con RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 y otros protocolos RFC relacionados.
