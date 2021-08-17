---
title: 'Capítulo 2: Instalación y uso del cliente DHCP para NetX de Azure RTOS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente DHCP para NetX de Azure RTOS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: da27039694c90f74a8b13dc556a367802f66c0ba7dd337f3e31ebab05641a9b1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788786"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Capítulo 2: Instalación y uso del cliente DHCP para NetX de Azure RTOS

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente DHCP para NetX de Azure RTOS.

## <a name="product-distribution"></a>Distribución del producto

DHCP para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_dhcp.h** Archivo de encabezado de DHCP para NetX

- **nx_dhcp.c** Archivo de código fuente C de DHCP para NetX

- **nx_dhcp.pdf** Descripción en PDF de DHCP para NetX

- **demo_netx_dhcp.c** Demostración de DHCP para NetX

- **demo_netx_multihome_dhcp_client.c** Demostración del cliente DHCP de NetX en varias interfaces

## <a name="dhcp-installation"></a>Instalación de DHCP

Para usar DHCP para NetX, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_dhcp.h* y *nx_dhcp.c* deben copiarse en este directorio.

## <a name="using-dhcp"></a>Uso de DHCP

DHCP para NetX es fácil de utilizar. Básicamente, el código de la aplicación debe incluir *nx_dhcp.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente. Después de incluir *nx_dhcp.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía. La aplicación también debe incluir *nx_dhcp.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar DHCP para NetX.

Tenga en cuenta que, como DHCP usa los servicios de UDP de NetX, debe habilitarse UDP con la llamada a *nx_udp_enable* antes de utilizar DHCP.

Para obtener una dirección IP asignada previamente, el cliente DHCP puede iniciar el proceso de DHCP con el mensaje Request y la opción 50 "Requested IP Address" (Dirección IP solicitada) en el servidor DHCP. El servidor DHCP responderá con un mensaje ACK si concede la dirección IP al cliente o un mensaje NACK si la rechaza. En el último caso, el cliente DHCP reinicia el proceso de DHCP en el estado Init con un mensaje Discover y ninguna dirección IP solicitada. La aplicación host crea primero el cliente DHCP y, a continuación, llama al servicio de API *nx_dhcp_request_client_ip* para establecer la dirección IP solicitada antes de iniciar el proceso de DHCP con *nx_dhcp_start*. Se proporciona una aplicación DHCP de ejemplo en este documento para ofrecer más detalles.

## <a name="in-the-bound-state"></a>En estado enlazado

Mientras el cliente DHCP se encuentra en estado enlazado, el subproceso de cliente DHCP procesa el estado del cliente una vez por intervalo (según se especifica en NX_DHCP_TIME_INTERVAL) y reduce el tiempo restante de la concesión de IP asignada al cliente. Cuando el tiempo de renovación ha transcurrido, el estado del cliente DHCP se actualiza al estado RENEW, en el que el cliente solicitará una renovación del servidor DHCP.


## <a name="sending-dhcp-messages-to-the-server"></a>Envío de mensajes DHCP al servidor

El cliente DHCP dispone de servicios de API que permiten que la aplicación host envíe un mensaje al servidor DHCP. Tenga en cuenta que estos servicios no están diseñados para que la aplicación host ejecute manualmente el protocolo de cliente DHCP ya que envían el mensaje, sin actualizar necesariamente el estado interno del cliente DHCP.

  - *nx_dhcp_release*: envía un mensaje RELEASE al servidor cuando la aplicación host abandona la red o necesita ceder su dirección IP.

  - *nx_dhcp_decline*: envía un mensaje DECLINE al servidor si la aplicación host determina independientemente del cliente DHCP que su dirección IP ya está en uso.

  - *nx_dhcp_forcerenew*: envía un mensaje FORCERENEW al servidor.

  - *nx_dhcp_send_request*: toma como argumento un tipo de mensaje de DHCP, como se especifica en *nx_dhcp.h*, y envía el mensaje al servidor. Está pensado principalmente para enviar el mensaje DHCP INFORM.

Vea la sección "*Descripción de los servicios DHCP*" en este documento para más información sobre estos servicios.

## <a name="starting-and-stopping-the-dhcp-client"></a>Inicio y detención del cliente DHCP

Para detener el cliente DHCP, independientemente de si ha logrado un estado enlazado, la aplicación host llama a *nx_dhcp_stop*.

Para reiniciar un cliente DHCP, la aplicación host debe detener primero el cliente DHCP mediante el servicio *nx_dhcp_stop* descrito anteriormente. A continuación, el host puede llamar a *nx_dhcp_start* para reanudar el cliente DHCP. Si la aplicación host desea borrar un perfil de cliente DHCP anterior, por ejemplo, uno obtenido de un servidor DHCP anterior de otra red, la aplicación host debe llamar a *nx_dhcp_reinitialize* para realizar esta tarea internamente antes de llamar a nx_dhcp_start.

Una secuencia típica podría ser:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

En el caso de las aplicaciones DHCP que se ejecutan en una sola interfaz DHCP, la detención del cliente DHCP también desactiva el temporizador del cliente DHCP. Por lo tanto, ya no realiza un seguimiento del tiempo restante de la concesión de IP. Al detener el cliente DHCP en una interfaz determinada, no se desactivará el temporizador del cliente DHCP, pero se detendrán las actualizaciones del temporizador del tiempo restante de la concesión de IP en esa interfaz.

Por lo tanto, no se recomienda detener el cliente DHCP a menos que la aplicación host requiera un reinicio o conmutación de redes.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Uso del cliente DHCP con IP automática

El cliente DHCP para NetX funciona simultáneamente con el protocolo de IP automática en las aplicaciones en las que DHCP y la IP automática garantizan una dirección cuando no se garantiza que un servidor DHCP esté disponible o responda. Sin embargo, si el host no puede detectar un servidor u obtener una dirección IP asignada, puede cambiar al protocolo de IP automática para una dirección IP local. Aunque, antes de hacerlo, es aconsejable detener temporalmente el cliente DHCP mientras la IP automática pasa por las fases de "sondeo" y "defensa". Una vez asignada una dirección IP automática al host, se puede reiniciar el cliente DHCP y, si está disponible un servidor DHCP, la dirección IP del host puede aceptar la dirección IP que ofrece el servidor DHCP mientras la aplicación se está ejecutando.

La IP automática de NetX dispone de una notificación de cambio de dirección para que el host supervise sus actividades en caso de un cambio de dirección IP.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En la figura 1.1 siguiente, se describe un ejemplo de cómo usar NetX. El cliente DHCP "*my_thread_entry*" se crea en la línea 101. Después de que se cree correctamente, el proceso DHCP se inicia en la llamada a *nx_dhcp_start* en la línea 108. En este momento, se inician los intentos del cliente DHCP para ponerse en contacto con el servidor DHCP. Durante este proceso, el código de aplicación espera a que se registre una dirección IP válida en la instancia de IP mediante el servicio de *nx_ip_status_check* (o *nx_ip_interface_status_check* para una interfaz secundaria) a partir de la línea 95. Esto se hace más habitualmente en un bucle con una opción de espera más corta.

Después de la línea 127, DHCP ha recibido una dirección IP válida y la aplicación puede continuar usando los servicios TCP/IP de NetX como se desee.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figura 1.1 Ejemplo de uso de DHCP con NetX

## <a name="multi-server-environments"></a>Entornos de varios servidores

En las redes en las que hay más de un servidor DHCP, el cliente DHCP acepta el primer mensaje Offer recibido del servidor DHCP, avanza hasta el estado Request y omite cualquier otra oferta recibida.

## <a name="arp-probes"></a>Sondeos ARP

El cliente DHCP puede configurarse para enviar uno o más sondeos ARP después de la asignación de direcciones IP del servidor DHCP para comprobar que la dirección IP aún no está en uso. En el RFC 2131 se recomienda el paso de sondeo ARP y es especialmente importante en entornos con más de un servidor DHCP. Si la aplicación host habilita la opción NX_DHCP_CLIENT_SEND_ARP_PROBE (consulte **Opciones de configuración** en el capítulo dos de las opciones adicionales de sondeo ARP), el cliente DHCP enviará un sondeo ARP "autodireccionado" y esperará durante el tiempo especificado para recibir una respuesta. Si no se recibe ninguna, el cliente DHCP avanza al estado Bound. Si se recibe una respuesta, el cliente DHCP supone que la dirección ya está en uso. Envía automáticamente un mensaje DECLINE al servidor y reinicializa el cliente para reiniciar los sondeos DHCP de nuevo desde el estado INIT. Así se reinicia la máquina de estado DHCP y el cliente envía otro mensaje DISCOVER al servidor.

## <a name="bootp-protocol"></a>Protocolo BOOTP

El cliente DHCP también admite el protocolo BOOTP además del protocolo DHCP. Para habilitar esta opción y usar BOOTP en lugar de DHCP, la aplicación host debe establecer la opción de configuración NX_DHCP_BOOTP_ENABLE. La aplicación host también puede solicitar direcciones IP específicas en el protocolo BOOTP. Sin embargo, el cliente DHCP no admite la carga del sistema operativo host, ya que a veces se usa BOOTP para hacerlo.

## <a name="dhcp-on-a-secondary-interface"></a>DHCP en una interfaz secundaria

El cliente DHCP de NetX puede ejecutarse en interfaces secundarias en lugar de en la interfaz principal predeterminada.

Para ejecutar el cliente DHCP de NetX en una interfaz de red secundaria, la aplicación host debe establecer el índice de interfaz del cliente DHCP en la interfaz secundaria mediante el servicio de API *nx_dhcp_set_interface_index*. La interfaz ya debe estar conectada a la interfaz de red principal mediante el servicio *nx_ip_interface_attach*. Consulte la guía del usuario de NetX para obtener más detalles sobre cómo conectar interfaces secundarias.

En la figura 1.2 siguiente, se muestra un sistema de ejemplo en el que la aplicación host se conecta al servidor DHCP en su interfaz secundaria. En la línea 65, la interfaz secundaria se conecta a la tarea de IP con una dirección IP nula. En la línea 104, una vez creada la instancia de cliente DHCP, el índice de la interfaz de cliente DHCP se establece en 1 (por ejemplo, el desplazamiento desde la interfaz principal que es el índice 0) mediante una llamada a *nx_dhcp_set_interface_index*. Después, el cliente DHCP está listo para iniciarse en la línea 108.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figura 1.2 Ejemplo de DHCP para NetX con compatibilidad de varios orígenes

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>Cliente DHCP en varias interfaces simultáneamente

Para ejecutar el cliente DHCP en varias interfaces, se debe establecer NX_MAX_PHYSICAL_INTERFACES de *nx_api.h* en el número de interfaces físicas conectadas al dispositivo. De forma predeterminada, este valor es 1 (es decir, la interfaz principal). Para registrar una interfaz adicional en la instancia de IP, use el servicio *nx_ip_interface_attach*. Consulte la guía del usuario de NetX para obtener más detalles sobre cómo conectar interfaces secundarias.

El siguiente paso consiste en establecer NX_DHCP_CLIENT_MAX_RECORDS de *nx_dhcp.h* en el número máximo de interfaces que se espera que ejecuten DHCP simultáneamente. Tenga en cuenta que NX_DHCP_CLIENT_MAX_RECORDS no tiene que ser igual a NX_MAX_PHYSICAL_INTERFACES. Por ejemplo, NX_MAX_PHYSICAL_INTERFACES puede ser 3 y NX_DHCP_CLIENT_MAX_RECORDS puede ser 2. En esta configuración, solo dos interfaces (pueden ser cualquiera de las tres interfaces físicas en cualquier momento) de las tres interfaces físicas pueden ejecutar DHCP al mismo tiempo. Los registros de cliente DHCP no tienen una asignación de uno a uno con las interfaces de red, por ejemplo, el registro del cliente 1 no se correlaciona automáticamente con el índice de interfaz física 1.

NX_DHCP_CLIENT_MAX_RECORDS también se puede establecer en un valor mayor que NX_MAX_PHYSICAL_INTERFACES, pero esto crearía registros de cliente no usados y sería un uso ineficaz de la memoria.

Antes de poder iniciar DHCP en cualquier interfaz, la aplicación debe habilitar las interfaces mediante una llamada a *nx_dhcp_interface_enable*. Tenga en cuenta que la excepción es la interfaz principal que se habilita automáticamente en la llamada a *nx_dhcp_create* (y que se puede deshabilitar mediante el servicio *nx_dhcp_interface_disable* que se describe a continuación).

En cualquier momento, se puede deshabilitar una interfaz para DHCP o se puede detener DHCP en esa interfaz independientemente de otras interfaces que ejecuten DHCP.

Como se mencionó anteriormente, para habilitar una interfaz específica para DHCP, use el servicio *nx_dhcp_interface_enable* y especifique el índice de interfaz física en el argumento de entrada. El número máximo de interfaces que se pueden habilitar es el valor de NX_DHCP_CLIENT_MAX_RECORDS con la única limitación de que el argumento de entrada del índice de interfaz sea menor que NX_MAX_PHYSICAL_INTERFACES.

Para iniciar DHCP en una interfaz específica, utilice el servicio *nx_dhcp_interface_start*. Para iniciar DHCP en todas las interfaces habilitadas, use el servicio *nx_dhcp_start*. (Las interfaces que ya han iniciado DHCP no se verán afectadas por *nx_dhcp_start*).

Para detener DHCP en una interfaz, use el servicio *nx_dhcp_interface_stop*. DHCP debe haberse iniciado ya en esa interfaz o se devolverá un estado de error. Para detener DHCP en todas las interfaces habilitadas, use el servicio *nx_dhcp_stop*. DHCP se puede detener independientemente de otras interfaces en cualquier momento.

La mayoría de los servicios de cliente DHCP existentes tienen un equivalente de "interfaz"; por ejemplo, *nx_dhcp_interface_release* es el equivalente específico de la interfaz de *nx_dhcp_release.* Si el cliente DHCP está configurado para una sola interfaz, realizan la misma acción.

Tenga en cuenta que los servicios de cliente DHCP que no son específicos de interfaz suelen aplicarse a todas las interfaces, pero no a todas. En el último caso, el servicio que no es específico de interfaz se aplica a la primera interfaz habilitada para DHCP que se encuentra en la búsqueda en la lista de registros de interfaz del cliente DHCP. Vea **Descripción de los servicios** en el capítulo tres sobre cómo funciona un servicio que no es específico de interfaz cuando se habilitan varias interfaces para DHCP.

En la secuencia de ejemplo siguiente, la instancia de IP tiene dos interfaces de red y primero se ejecuta DHCP en la interfaz secundaria. En algún momento posterior, inicia DHCP en la interfaz principal. A continuación, libera la dirección IP en la interfaz principal y reinicia DHCP en la interfaz principal:

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

Para obtener una lista completa de los servicios específicos de interfaz, vea **Descripción de los servicios** en el capítulo tres.

## <a name="configuration-options"></a>Opciones de configuración

Las opciones DHCP configurables por el usuario en *nx_dhcp.h* permiten a la aplicación host ajustar correctamente el cliente DHCP para sus requisitos particulares. A continuación, se muestra una lista de estos parámetros:  
  
- **NX_DHCP_ENABLE_BOOTP** Si se define, esta opción habilita el protocolo BOOTP en lugar de DHCP. Esta opción está deshabilitada de manera predeterminada.

- **NX_DHCP_CLIENT_RESTORE_STATE** Si se define, permite que el cliente DHCP guarde el "estado" actual de la licencia de cliente DHCP, incluido el tiempo restante de la concesión, y restaure este estado entre los reinicios de la aplicación de cliente DHCP. El valor predeterminado está deshabilitado.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Si se establece, el cliente DHCP no creará su propio grupo de paquetes. La aplicación host debe usar el servicio nx_dhcp_packet_pool_set para establecer el grupo de paquetes del cliente DHCP. El valor predeterminado está deshabilitado.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE** Si se define, permite que el cliente DHCP envíe un sondeo ARP después de la asignación de la dirección IP para comprobar que la dirección DHCP asignada no pertenece a otro host. Esta opción está deshabilitada de forma predeterminada.

- **NX_DHCP_ARP_PROBE_WAIT** Define el período de tiempo que el cliente DHCP espera una respuesta después de enviar un sondeo ARP. El valor predeterminado es un segundo (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCP_ARP_PROBE_MIN** Define la variación mínima en el intervalo entre el envío de sondeos ARP. El valor predeterminado es 1 segundo.

- **NX_DHCP_ARP_PROBE_MAX** Define la variación máxima en el intervalo entre el envío de sondeos ARP. El valor predeterminado es 2 segundos.

- **NX_DHCP_ARP_PROBE_NUM** Define el número de sondeos ARP enviados para determinar si la dirección IP asignada por el servidor DHCP ya está en uso. El valor predeterminado es 3 sondeos.

- **NX_DHCP_RESTART_WAIT** Define el período de tiempo que el cliente DHCP espera para reiniciar DHCP si la dirección IP asignada al cliente DHCP ya está en uso. El valor predeterminado es 10 segundos.

- **NX_DHCP_CLIENT_MAX_RECORDS** Especifica el número máximo de registros de interfaz que se guardarán en la instancia del cliente DHCP. Un registro de la interfaz de cliente DHCP es un registro del cliente DHCP que se ejecuta en una interfaz específica. El valor predeterminado se establece en el recuento de interfaces físicas (NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Si se define, permite que el cliente DHCP envíe la opción de tamaño máximo de mensaje DHCP. Esta opción está deshabilitada de forma predeterminada.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Si se define, permite que el cliente DHCP compruebe si los caracteres o la longitud son válidos en el nombre de host de entrada en la llamada a nx_dhcp_create. Esta opción está deshabilitada de forma predeterminada.

- **NX_DHCP_THREAD_PRIORITY** Prioridad del subproceso DHCP. De forma predeterminada, este valor especifica que el subproceso DHCP se ejecuta con la prioridad 3.

- **NX_DHCP_THREAD_STACK_SIZE** Tamaño de la pila de subprocesos DHCP. De forma predeterminada, el tamaño es 2048 bytes.

- **NX_DHCP_TIME_INTERVAL** Intervalo en segundos en el que se ejecuta la función de expiración del temporizador del cliente DHCP. Esta función actualiza todos los tiempos de espera del proceso DHCP, por ejemplo, si se deben retransmitir los mensajes o se debe cambiar el estado del cliente DHCP. De manera predeterminada, este valor es 1 segundo.

- **NX_DHCP_OPTIONS_BUFFER_SIZE** Tamaño del búfer de opciones DHCP. De manera predeterminada, este valor es 312.

- **NX_DHCP_PACKET_PAYLOAD** Especifica el tamaño en bytes de la carga del paquete de cliente DHCP. El valor predeterminado es NX_DHCP_MINIMUM_IP_DATAGRAM más el tamaño del encabezado físico. Normalmente, el tamaño del encabezado físico en una red de conexión por cable es el tamaño del marco de Ethernet.

- **NX_DHCP_PACKET_POOL_SIZE** Especifica el tamaño del grupo de paquetes del cliente DHCP. El valor predeterminado es (5 * NX_DHCP_PACKET_PAYLOAD) que proporcionará cuatro paquetes más espacio para la sobrecarga interna del grupo de paquetes.

- **NX_DHCP_MIN_RETRANS_TIMEOUT** Especifica la opción de espera mínima para recibir una respuesta del servidor DHCP al mensaje del cliente antes de retransmitir el mensaje. El valor predeterminado son los 4 segundos recomendados por el RFC 2131.

- **NX_DHCP_MAX_RETRANS_TIMEOUT** Especifica la opción de espera máxima para recibir una respuesta del servidor DHCP al mensaje del cliente antes de retransmitir el mensaje. El valor predeterminado son los 64 segundos recomendados por el RFC 2131.

- **NX_DHCP_MIN_RENEW_TIMEOUT** Especifica la opción de espera mínima para recibir un mensaje del servidor DHCP y enviar una solicitud de renovación una vez que el cliente DHCP esté enlazado a una dirección IP. El valor predeterminado es de 60 segundos. Sin embargo, el cliente DHCP utiliza los tiempos de expiración de renovación y reenlace del mensaje del servidor DHCP antes de tomar de manera predeterminada el tiempo de espera mínimo de renovación.

- **NX_DNS_TYPE_OF_SERVICE** Tipo de servicio necesario para las solicitudes UDP de DHCP. De forma predeterminada, este valor se define como NX_IP_NORMAL para el servicio de paquetes IP normal.

- **NX_DHCP_FRAGMENT_OPTION** Habilitación de la fragmentación de solicitudes UDP de DHCP. De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP de DHCP.

- **NX_DNS_TIME_TO_LIVE** Especifica el número de enrutadores que un paquete puede pasar antes de que se descarte. El valor predeterminado se define en 0x80.

- **NX_DHCP_QUEUE_DEPTH** Especifica el número máximo de profundidad de la cola de recepción. El valor predeterminado se establece en 4.
