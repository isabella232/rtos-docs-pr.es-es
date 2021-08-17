---
title: 'Capítulo 1: Introducción a Telnet de Azure RTOS NetX Duo'
description: Telnet de Azure RTOS NetX Duo es un protocolo diseñado para transferir comandos y respuestas entre dos nodos en Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50a2c4d8726863f4e609debadd9ddf2455cfd540219a476970756d3d250ec562
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799037"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Capítulo 1: Introducción a Telnet de Azure RTOS NetX Duo

Telnet de Azure RTOS NetX Duo es un protocolo diseñado para transferir comandos y respuestas entre dos nodos en Internet. Telnet es un protocolo simple que emplea servicios de Protocolo de control de transmisión (TCP) confiables para realizar su función de transferencia. Por este motivo, Telnet es un protocolo de transferencia altamente fiable. Telnet también es uno de los protocolos de aplicación más usados.

## <a name="telnet-requirements"></a>Requisitos de Telnet

Para que funcione correctamente, el paquete Telnet de NetX Duo requiere que ya se haya creado una instancia de IP de NetX. Además, TCP debe estar habilitado en la misma instancia de IP. La parte del cliente Telnet del paquete Telnet de NetX Duo no tiene ningún requisito adicional.

La parte del servidor Telnet del paquete Telnet de NetX Duo tiene un requisito adicional. Se necesita acceso completo al *puerto 23* TCP conocido para controlar todas las solicitudes Telnet de cliente.

## <a name="telnet-constraints"></a>Restricciones de Telnet 

El protocolo Telnet de NetX Duo implementa el estándar de Telnet. Sin embargo, la interpretación y la respuesta de los comandos de Telnet, indicados por un byte con el valor 255, son responsabilidad de la aplicación. Los distintos parámetros de comando y comandos de Telnet se definen en los archivos *nxd_telnet_client.h y nxd_telnet_server.h*.

## <a name="telnet-communication"></a>Comunicación de Telnet

Como se ha mencionado anteriormente, el servidor Telnet emplea el *puerto 23 TCP conocido* para las solicitudes de cliente de campo. Los clientes de Telnet pueden utilizar cualquier puerto TCP disponible.

## <a name="telnet-authentication"></a>Autenticación de Telnet

La autenticación de Telnet es responsabilidad de la función de devolución de llamada del servidor Telnet de la aplicación. La devolución de llamada de "nueva conexión" del servidor Telnet de la aplicación normalmente solicita al cliente el nombre y la contraseña. A continuación, el cliente sería el responsable de proporcionar la información. Luego, el servidor procesaría la información en la devolución de llamada de "recepción de datos". En este punto, el código del servidor de aplicaciones tendría que autenticar la información y decidir si es válida o no.

## <a name="telnet-new-connection-callback"></a>Devolución de llamada de nueva conexión de Telnet

El servidor Telnet de NetX Duo llama a la función de devolución de llamada especificada de la aplicación cada vez que se recibe una nueva solicitud del cliente Telnet. La aplicación especifica la función de devolución de llamada cuando se crea el servidor Telnet mediante la función ***nx_telnet_server_create***. Las acciones típicas de la devolución de llamada de "nueva conexión" incluyen el envío de un banner o un aviso al cliente. También podrían incluir un mensaje de información de inicio de sesión.

### <a name="prototype"></a>Prototipo

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al servidor Telnet que realiza la llamada.
- **logical_connection**: conexión lógica interna con el servidor Telnet. La aplicación puede utilizarlo como índice en los búferes o estructuras de datos específicas para cada conexión de cliente. Su valor oscila entre 0 y NX_TELNET_MAX_CLIENTS - 1.

## <a name="telnet-receive-data-callback"></a>Devolución de llamada de datos de recepción de Telnet

El servidor Telnet de NetX Duo llama a la función de devolución de llamada especificada de la aplicación cada vez que se reciben nuevos datos del cliente Telnet. La aplicación especifica la función de devolución de llamada cuando se crea el servidor Telnet mediante la función ***nx_telnet_server_create***. Entre las acciones típicas de la devolución de llamada de "nueva conexión" se incluyen la devolución o análisis de los datos y la provisión de datos como resultado de interpretar un comando del cliente.

Tenga en cuenta que esta rutina de devolución de llamada también debe liberar el paquete proporcionado.

### <a name="prototype"></a>Prototipo

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al servidor Telnet que realiza la llamada.
- **logical_connection**: conexión lógica interna con el servidor Telnet. La aplicación puede utilizarlo como índice en los búferes o estructuras de datos específicas para cada conexión de cliente. Su valor oscila entre 0 y NX_TELNET_MAX_CLIENTS - 1.
- **packet_ptr**: puntero al paquete que contiene los datos del cliente.

## <a name="telnet-end-connection-callback"></a>Devolución de llamada de conexión final de Telnet

El servidor Telnet de NetX Duo llama a la función de devolución de llamada especificada de la aplicación cada vez que el cliente Telnet finaliza la conexión. La aplicación especifica la función de devolución de llamada cuando se crea el servidor Telnet mediante la función ***nx_telnet_server_create***. Las acciones típicas de la devolución de llamada de "finalización de la conexión" incluyen la limpieza de las estructuras de datos específicas del cliente asociadas con la conexión lógica.

### <a name="prototype"></a>Prototipo
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al servidor Telnet que realiza la llamada.
- **logical_connection**: conexión lógica interna para el servidor Telnet. La aplicación puede utilizarlo como índice en los búferes o estructuras de datos específicas para cada conexión de cliente. Su valor oscila entre 0 y NX_TELNET_MAX_CLIENTS - 1.

## <a name="telnet-option-negotiation"></a>Negociación de la opción de Telnet

El servidor Telnet de NetX Duo admite un conjunto limitado de opciones de Telnet: Echo (Eco) y Suppress Go Ahead (Eliminar avance).

Para habilitar esta característica, no se debe definir el elemento NX_TELNET_SERVER_OPTION_DISABLE. De forma predeterminada, no está definido. El servidor Telnet crea un grupo de paquetes en el servicio *nx_telnet_server_create* desde el que asigna paquetes para enviar las solicitudes de opciones de Telnet al cliente. Vea "Opciones de configuración" para establecer la carga de paquetes (NX_TELNET_SERVER_PACKET_PAYLOAD) y el tamaño del grupo de paquetes (NX_TELNET_SERVER_PACKET_POOL_SIZE) de este grupo de paquetes. Este grupo de paquetes se eliminará cuando se llame al servicio *nx_telnet_server_delete*.

Después de establecer una conexión con el cliente Telnet, enviará este conjunto de opciones de Telnet al cliente si no ha recibido solicitudes de opciones de este:

- will echo (se aplicará eco)
- dont echo (no se aplica eco)
- will sga (aplicará SGA)

Cuando recibe datos de Telnet del cliente, el servidor Telnet comprueba si el primer byte es el código "IAC". Si es así, procesará todas las opciones del paquete de cliente. Las opciones que no están en la lista anterior se ignoran.

De forma predeterminada, el servidor Telnet crea su propio grupo de paquetes interno si no se define la opción NX_TELNET_SERVER_OPTION_DISABLE y necesita transmitir los comandos de la opción de Telnet. El grupo de paquetes del servidor Telnet se define mediante NX_TELNET_SERVER_PACKET_PAYLOAD y NX_TELNET_SERVER_PACKET_POOLSIZE. Sin embargo, si se define NX_TELNET_SERVER_USER_CREATE_PACKET_POOL, la aplicación debe crear el grupo de paquetes del servidor Telnet y establecerlo como tal llamando a *_nx_telnet_server_packet_pool_set*. Consulte el capítulo 3 "Descripción de los servicios de Telnet" para obtener más información sobre esta función.

A diferencia del servidor Telnet de NetX Duo, el subproceso de la tarea del cliente Telnet de NetX Duo no envía ni responde automáticamente a las opciones recibidas del servidor Telnet. Esto debe realizarse mediante la aplicación cliente Telnet.

## <a name="telnet-multi-thread-support"></a>Compatibilidad con varios subprocesos de Telnet

Se puede llamar a los servicios del cliente Telnet de NetX Duo desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia del cliente Telnet deben realizarse consecutivamente desde el mismo subproceso.

## <a name="telnet-rfcs"></a>RFC de Telnet

Telnet de NetX Duo es compatible con RFC854 y otros protocolos RFC relacionados.
