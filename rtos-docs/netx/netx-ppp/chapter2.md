---
title: 'Capítulo 2: Instalación y uso del protocolo punto a punto (PPP) de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del protocolo punto a punto (PPP) de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b62ca837cadd5f7bee2686ab566ff133f1088ff7ba8b572e372e5051b7bbaab9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791098"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a>Capítulo 2: Instalación y uso del protocolo punto a punto (PPP) de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del protocolo punto a punto (PPP) de Azure RTOS NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

El paquete del protocolo punto a punto (PPP) de Azure RTOS NetX está disponible en <https://github.com/azure-rtos/netx>. El paquete incluye los siguientes archivos:

- **nx_ppp. h**: Archivo de encabezado para PPP para NetX
- **nx_ppp. c**: Archivo de origene de C para PPP para NetX
- **nx_ppp.pdf**: Descripción en PDF de PPP para NetX
- **demo_netx_ppp.c**: Demostración de PPP de NetX

## <a name="ppp-installation"></a>Instalación de PPP

Para usar PPP para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_ppp.h* y *nx_ppp.c* deben copiarse en este directorio.

## <a name="using-ppp"></a>Uso de PPP

El uso de PPP para NetX es sencillo. Básicamente, el código de la aplicación debe incluir *nx_ppp.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente. Después de incluir *nx_ppp.h*, el código de la aplicación puede realizar las llamadas de función PPP especificadas más adelante en esta guía. La aplicación también debe incluir *nx_ppp.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar el PPP de NetX.

## <a name="using-modems"></a>Uso de módems

Si se necesita un módem para la conexión a Internet, es necesario tener en cuenta algunas consideraciones especiales para poder usar el producto de PPP de NetX. Básicamente, el uso de un módem introduce lógica adicional de inicialización y lógica para la pérdida de comunicación. Además, la mayor parte de la lógica de módem adicional se realiza fuera del contexto de PPP de NetX. El flujo básico del uso de PPP de NetX con un módem es similar al siguiente:

1. Inicializar módem

1. Marcar al proveedor de servicios de Internet (ISP)

1. Esperar a la conexión

1. Esperar a la solicitud de UserID

1. Iniciar PPP de NetX [PPP en operación]

1. Pérdida de comunicación

1. Detener PPP de NetX (o reiniciar mediante nx_ppp_restart)

### <a name="initialize-modem"></a>Inicializar módem

Utilizando la rutina de salida en serie de bajo nivel de la aplicación, el módem se inicializa a través de una serie de comandos de caracteres ASCII (consulte la documentación del módem para obtener más detalles).

### <a name="dial-internet-service-provider"></a>Marcar al proveedor de servicios de Internet

Con la rutina de salida en serie de bajo nivel de la aplicación, se indica al módem que marque al ISP. Por ejemplo, lo siguiente es típico de una cadena ASCII que se usa para marcar a un ISP en el número 123-4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Esperar a la conexión

En este momento, la aplicación espera a recibir la indicación del módem de que se ha establecido una conexión. Esto se consigue buscando los caracteres de la rutina de entrada en serie de bajo nivel de la aplicación. Normalmente, los módems devuelven una cadena ASCII "CONNECT" cuando se ha establecido una conexión.

### <a name="wait-for-user-id-prompt"></a>Esperar a la solicitud de UserID

Una vez establecida la conexión, la aplicación debe esperar una solicitud de inicio de sesión inicial del ISP. Normalmente, suele tomar la forma de una cadena ASCII como "Inicio de sesión".

### <a name="start-netx-ppp"></a>Iniciar PPP de NetX

En este punto, se puede iniciar el PPP de NetX. Esto se logra mediante una llamada al servicio *nx_ppp_create* seguido del servicio *nx_ip_create*. También es posible que se requieran servicios adicionales para habilitar PAP y configurar las direcciones IP del PPP. Consulte las siguientes secciones de esta guía para obtener más información.

### <a name="loss-of-communication"></a>Pérdida de comunicación

Una vez que se inicia PPP, cualquier información que no sea de PPP se pasa a la rutina de "control de paquetes no válidos" que la aplicación especificó para el servicio *nx_ppp_create*. Normalmente, los módems envían una cadena ASCII, como "SIN OPERADOR", cuando se pierde la comunicación con el ISP. Cuando la aplicación recibe un paquete que no es PPP con dicha información, debe continuar para detener la instancia de PPP de NetX o reiniciar la máquina de estados de PPP a través de la API de *nx_ppp_restart*.

### <a name="stop-netx-ppp"></a>Detener PPP de NetX

Detener el PPP de NetX es bastante sencillo. Básicamente, todos los sockets creados deben desenlazarse y eliminarse. A continuación, elimine la instancia de IP a través del servicio *nx_ip_delete*. Una vez eliminada la instancia de IP, se debe llamar al servicio *nx_ppp_delete* para finalizar el proceso de detención de PPP. En este momento, la aplicación puede intentar restablecer la comunicación con el ISP.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En la figura 1.1 a continuación se describe un ejemplo que muestra lo fácil que es usar el PPP de NetX. En este ejemplo, el archivo de inclusión de PPP *nx_ppp. h* se incluye en la línea 3. A continuación, se crea el PPP en *"tx_application_define*" en la línea 56. El bloque de control de PPP "*my_ppp*" se definió anteriormente como una variable global en la línea 9. 

>[!NOTE]
>El PPP debe crearse antes de crear la instancia de IP. Después de la creación correcta de PPP e IP, el subproceso "*my_thread*" espera a que el vínculo del PPP esté activo en la línea 98. En la línea 104, tanto PPP como NetX están totalmente operativos.

El único elemento que no se muestra en este ejemplo es el ISR de recepción de bytes en serie de la aplicación. Deberá llamar a *nx_ppp_byte_receive* con "*my_ppp*" y el byte recibido como parámetros de entrada.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para crear el PPP para NetX. En la lista siguiente se describe cada una de forma detallada:

- **NX_DISABLE_ERROR_CHECKING** Si está definida, esta opción quita la comprobación de errores básica de PPP. Normalmente se utiliza después de depurar la aplicación.
- **NX_PPP_PPPOE_ENABLE** Si está definida, PPP puede transmitir paquetes a través de Ethernet.
- **NX_PPP_BASE_TIMEOUT** Define la frecuencia del periodo (en tics del temporizador) con el que se reactiva la tarea del subproceso de PPP para comprobar los eventos de PPP. El valor predeterminado es 1*NX_IP_PERIODIC_RATE (100 tics).
- **NX_PPP_DISABLE_INFO** Si está definida, la recopilación de información interna de PPP está deshabilitada.
- **NX_PPP_DEBUG_LOG_ENABLE** Si está definida, se habilita el registro de depuración interno de PPP.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**: si está definida, se habilita el registro de depuración de PPP interno *printf* en *stdio*. Esto solo es válido si el registro de depuración también está habilitado.
- **NX_PPP_DEBUG_LOG_SIZE** Tamaño del registro de depuración (número de entradas del registro de depuración). Al llegar a la última entrada, la captura de depuración vuelve a la primera entrada y sobrescribe cualquier dato capturado previamente. El valor predeterminado es 50.
- **NX_PPP_DEBUG_FRAME_SIZE**: cantidad máxima de datos capturados de una carga de paquetes recibida y guardados en la salida de depuración. El valor predeterminado es 50.
- **NX_PPP_DISABLE_CHAP** Si está definida, se quita la lógica interna de CHAP de PPP, incluida la lógica de síntesis de MD5.
- **NX_PPP_DISABLE_PAP**: si está definida, se quita la lógica interna de PAP de PPP.
- **NX_PPP_DNS_OPTION_DISABLE**: si está definida, la opción DNS se deshabilita en la respuesta IPCP.  De forma predeterminada, esta opción no está definida (la opción de DNS está establecida).
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: especifica el número de veces que el host de PPP solicitará una dirección de servidor DNS del homólogo en el estado de IPCP. Esto no tiene ningún efecto si se define NX_PPP_DNS_OPTION_DISABLE. El valor predeterminado es 2.
- **NX_PPP_HASHED_VALUE_SIZE** Especifica el tamaño de las cadenas "hashed value" que se usan en la autenticación de CHAP. El valor predeterminado se establece en 16 bytes, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES** Define el número máximo de reintentos si el PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de configuración de LCP. Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva. El valor predeterminado es 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES** Define el número máximo de reintentos si el PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de autenticación de PAP. Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva. El valor predeterminado es 20.
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES** Define el número máximo de reintentos si el PPP agota el tiempo de espera antes de enviar otro mensaje de desafío de CHAP. Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva. El valor predeterminado es 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES** Define el número máximo de reintentos si el PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de configuración de IPCP. Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva. El valor predeterminado es 20.
- **NX_PPP_MRU** Especifica la unidad de recepción máxima (MRU) para PPP. De forma predeterminada, este valor es 1500 bytes (el valor mínimo). La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.
- **NX_PPP_MINIMUM_MRU** Especifica el número mínimo de MRU recibido en un mensaje de solicitud de configuración de LCP. De forma predeterminada, este valor es 1500 bytes (el valor mínimo). La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.
- **NX_PPP_NAME_SIZE** Especifica el tamaño de las cadenas "name" usadas en la autenticación. El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de incluir *nx_ppp.h.
- **NX_PPP_PASSWORD_SIZE**: especifica el tamaño de las cadenas "password" usadas en la autenticación. El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de la inclusión de *nx_ppp. h.*
- **NX_PPP_PROTOCOL_TIMEOUT** Define la opción de espera (en segundos) para que la tarea PPP reciba una respuesta a un mensaje de solicitud de protocolo PPP. El valor predeterminado es 4 segundos.
- **NX_PPP_RECEIVE_TIMEOUTS** Define el número de veces que la tarea de subprocesos PPP agota el tiempo de espera para recibir el siguiente carácter de una secuencia de mensajes de PPP. Después, PPP libera el paquete y comienza a esperar para recibir el siguiente mensaje de PPP. El valor predeterminado es 4.
- **NX_PPP_SERIAL_BUFFER_SIZE** Especifica el tamaño del búfer de serie de caracteres de recepción. De forma predeterminada, este valor es 3000 bytes. La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.
- **NX_PPP_TIMEOUT** Define la opción de espera (en tics de temporizador) para asignar paquetes para transmitir datos, así como almacenar en búfer los datos de serie de PPP en paquetes para enviarlos a la capa de IP. El valor predeterminado es 4*NX_IP_PERIODIC_RATE (400 tics).
- **NX_PPP_THREAD_TIME_SLICE** Opción de segmento de tiempo para los subprocesos de PPP. Este valor es TX_NO_TIME_SLICE de forma predeterminada. La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.
- **NX_PPP_VALUE_SIZE** Especifica el tamaño de las cadenas "value" que se usan en la autenticación de CHAP. El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de la inclusión de nx_ppp. h.
