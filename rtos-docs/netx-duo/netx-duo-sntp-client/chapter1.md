---
title: 'Capítulo 1: Introducción a SNTP de Azure RTOS NetX Duo'
description: El protocolo simple de tiempo de redes (SNTP) de Azure RTOS NetX es un protocolo diseñado para sincronizar relojes a través de Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3e1170197c6c4981060459104da80e354fac5db
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814554"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Capítulo 1: Introducción a SNTP de Azure RTOS NetX Duo 

El protocolo simple de tiempo de redes (SNTP) de Azure RTOS NetX es un protocolo diseñado para sincronizar relojes a través de Internet. La versión 4 de SNTP es un protocolo simplificado basado en el protocolo de tiempo de redes (NTP). Emplea servicios de protocolo de datagramas de usuario (UDP) para realizar actualizaciones de hora con un protocolo simple sin estado. Aunque no es tan complejo como NTP, SNTP es muy confiable y preciso. En la mayoría de los lugares de Internet de hoy en día, SNTP proporciona una precisión de entre 1 y 50 milisegundos, en función de las características del origen de la sincronización y de las rutas de acceso de la red. SNTP tiene muchas opciones para proporcionar confiabilidad a la hora de recibir las actualizaciones de hora. La posibilidad de cambiar a servidores alternativos, la aplicación de interrupciones en los algoritmos de sondeo y la detección automática de servidores horarios son solo algunos de los medios de los que dispone un cliente SNTP para administrar un entorno variable de servicio horario de Internet. Lo que le falta en precisión lo compensa con la simplicidad y la facilidad de implementación que ofrece. SNTP está pensado principalmente para ofrecer mecanismos completos de acceso a los servicios nacionales de difusión de tiempo y frecuencia (por ejemplo, el servidor NTP).

## <a name="netx-duo-sntp-client-requirements"></a>Requisitos del cliente SNTP de NetX Duo

El cliente SNTP de NetX Duo requiere que ya se haya creado una instancia de IP. Además, debe estar habilitado el protocolo UDP en la misma instancia de IP y debe tener acceso al puerto *conocido* 123 para enviar datos de hora a un servidor SNTP, aunque también puede utilizar puertos alternativos. Los clientes de difusión deben enlazar al puerto UDP por el que está enviando su servidor de difusión, normalmente 123. La aplicación de cliente SNTP de NetX Duo debe tener una o varias direcciones IP de servidor SNTP.

## <a name="netx-duo-sntp-client-limitations"></a>Limitaciones del cliente SNTP de NetX Duo 

La precisión en la representación de la hora local en las actualizaciones de hora de NTP administradas por la API del cliente SNTP está limitada a una resolución de milisegundos.

El cliente SNTP incluye una única dirección de servidor SNTP a la vez. Si parece que ese servidor ya no es válido, la aplicación debe detener la tarea del cliente SNTP y reinicializarla con otra dirección de servidor SNTP, mediante la comunicación de difusión o de unidifusión SNTP.

El cliente SNTP no es compatible con la difusión manycast a varios receptores.

El cliente SNTP de NetX Duo no es compatible con mecanismos de autenticación para comprobar los datos de los paquetes recibidos.

## <a name="netx-duo-sntp-client-operation"></a>Funcionamiento del cliente SNTP de NetX Duo

En la RFC 4330 se recomienda que los clientes SNTP solo funcionen en la capa más alta de la red local y preferiblemente con configuraciones en las que ningún cliente NTP o SNTP dependa de ellos para la sincronización. El nivel de capa refleja la posición del host en la jerarquía de tiempo de NTP, donde la capa 1 es el nivel más alto (un servidor horario raíz) y la capa 15 es el nivel mínimo permitido (por ejemplo, el cliente). La capa mínima predeterminada del cliente SNTP es 2.

El cliente SNTP de NetX Duo puede funcionar en uno de dos modos básicos, unidifusión o difusión, para obtener la hora a través de Internet. En el modo de unidifusión, el cliente sondea su servidor SNTP a intervalos regulares y espera a recibir una respuesta del servidor. Cuando la recibe, comprueba que la respuesta contiene una actualización de hora válida mediante la aplicación de un conjunto de "comprobaciones de integridad" recomendado en la RFC 4330. A continuación, aplica la diferencia de tiempo, si existe, con el reloj del servidor a su reloj local. En el modo de difusión, el cliente simplemente escucha las difusiones de actualización de hora y mantiene su reloj local después de aplicar un conjunto similar de comprobaciones de integridad para verificar los datos de hora de la actualización. Las comprobaciones de integridad se describen en detalle en la sección **Comprobaciones de integridad de SNTP**, más abajo.

Para que el cliente pueda ejecutarse en cualquier modo, debe establecer sus parámetros operativos. Esto se hace llamando a *nx_sntp_client_initialize_unicast* o a *nx_sntp_client_initialize_broadcast* para los modos de unidifusión o difusión, respectivamente. Estos servicios establecen los tiempos de espera para el intervalo máximo de tiempo sin una actualización válida, el límite de actualizaciones no válidas consecutivas recibidas, un intervalo de sondeo para el modo de unidifusión, el modo de operación (es decir, unidifusión o difusión) y el servidor SNTP.

Si se supera el intervalo máximo de tiempo o el número máximo de actualizaciones no válidas recibidas, el cliente SNTP continúa ejecutándose, pero establece el estado del servidor SNTP actual en no válido. La aplicación puede sondear el cliente SNTP mediante el servicio *nx_sntp_client_receiving_updates* para comprobar que el servidor SNTP todavía está enviando actualizaciones válidas. Si no es así, debe detener el subproceso del cliente SNTP mediante el servicio *nx_sntp_client_stop* y llamar a cualquiera de los dos servicios de inicialización para establecer otra dirección de servidor SNTP. Para reiniciar el cliente SNTP, la aplicación llama a *nx_sntp_client_run_broadcast* o a *nx_sntp_client_run_unicast*. Tenga en cuenta que la aplicación puede cambiar el modo de funcionamiento del cliente SNTP en la llamada de inicialización para pasar a unidifusión o difusión, según interese.

### <a name="local-clock-operation"></a>Funcionamiento del reloj local

La hora de SNTP se basa en el número de segundos del reloj NTP maestro, o lo que es lo mismo, en el número de segundos transcurridos en la primera época de NTP, desde el 1 de enero de **1900 a las 00:00:00 hasta** el 1 de enero de **1999 a las 00:00:00**. El 01-01-1999 fue cuando se produjo el último segundo intercalar. Este valor se define de la manera siguiente:

\#define NTP_SECONDS_AT_01011999 0xBA368E80

Antes de que se ejecute el cliente SNTP, la aplicación puede inicializar la hora local del cliente SNTP para que el cliente la use como hora base de referencia. Para ello, debe usar el servicio *nx_sntp_client_set_local_time*. Este servicio recibe la hora en formato de NTP de segundos y fracción, donde la fracción son los milisegundos en el tiempo condensado de NTP. Idealmente, la aplicación puede obtener una hora de SNTP de un origen independiente. No hay ninguna API para convertir el año, el mes, el día y la hora a una hora de NTP en el cliente SNTP de NetX Duo. Para obtener una descripción del formato de hora de NTP, consulte la *RFC4330 de protocolo simple de tiempo de redes (SNTP) versión 4 para IPv4, IPv6 y OSI*.

Si no se proporciona ninguna hora local base cuando se inicia el cliente SNTP, este aceptará las actualizaciones de SNTP sin compararlas con su hora local en la primera actualización. A partir de ese momento, aplicará los valores máximo y mínimo de actualización de hora para determinar si va a modificar su hora local.

Para obtener la hora local del cliente SNTP, la aplicación puede utilizar el servicio *nx_sntp_client_get_local_time_extended*.

### <a name="sntp-sanity-checks"></a>Comprobaciones de integridad de SNTP 

El cliente examina el paquete entrante con los siguientes criterios:

  - La dirección IP de origen debe coincidir con la dirección IP del servidor actual.

  - El puerto de origen del emisor debe coincidir con el puerto de origen del servidor actual.

  - El paquete debe tener la longitud mínima necesaria para incluir un mensaje de hora de SNTP.

A continuación, se extraen los datos de hora del búfer del paquete y el cliente aplica un conjunto de "comprobaciones de integridad" específicas:

  - El indicador de segundo intercalar establecido en 3 indica que el servidor no está sincronizado. El cliente debe intentar buscar un servidor alternativo.

  - Un campo de capa establecido en cero se conoce como paquete de beso de la muerte (KOD). El controlador de KOD del cliente SMTP en esta situación es una devolución de llamada definida por el usuario. El pequeño archivo de demostración de ejemplo contiene un controlador de KOD simple para esta situación. El campo de identificador de referencia contiene opcionalmente un código que indica el motivo de la respuesta de KOD. En cualquier momento, el controlador de KOD debe indicar cómo administrar la recepción de un beso de la muerte del servidor SNTP. Normalmente, querrá reinicializar el cliente SNTP con otro servidor SNTP.

  - La versión del servidor SNTP, la capa y el modo de funcionamiento deben coincidir con el servicio del cliente.

  - Si el cliente se configura con el máximo de dispersión del reloj del servidor, el cliente solo comprueba la dispersión del reloj del servidor en la primera actualización que recibe y, si supera el máximo del cliente, rechaza el servidor.

  - Los campos de marca de tiempo del servidor también deben superar comprobaciones específicas. En el caso del servidor de unidifusión, todos los campos de hora deben incluir contenido y no pueden ser NULL. La marca de tiempo de origen debe ser igual a la marca de tiempo de transmisión de la solicitud de mensaje de hora SNTP del cliente. Esto protege al cliente ante intrusos malintencionados y un comportamiento de servidor no autorizado. El servidor de difusión solo necesita rellenar la marca de tiempo de transmisión. Dado que no recibe nada del cliente, no tiene ningún campo de recepción ni de origen que rellenar.

    Una comprobación de integridad con errores marca una actualización de hora como una actualización de hora no válida. El servicio de comprobación de integridad del cliente SNTP realiza un seguimiento del número de actualizaciones de hora no válidas consecutivas recibidas del mismo servidor.

Cuando la tarea de subproceso del cliente SNTP comprueba la validez de un paquete SNTP para aplicarlo a la hora local del cliente SNTP, incrementa el recuento del servicio `nx_sntp_client_invalid_time_updates.` del cliente SNTP. También devuelve un estado de error al autor de la llamada, pero se trata de un procesamiento interno, por lo que no es inmediatamente visible para la aplicación. Para detectar actualizaciones de hora con errores se consulta el valor del servicio `nx_sntp_client_invalid_time_updates` del cliente SNTP después de recibir las actualizaciones de hora del servidor SNTP.

Si la actualización de hora del servidor supera las comprobaciones de integridad, el cliente intenta procesar los datos de hora a su hora local. Si el cliente está configurado para el cálculo del recorrido de ida y vuelta (por ejemplo, el tiempo desde que se envía una solicitud de actualización hasta que se recibe), se calcula este tiempo. El valor se reduce a la mitad y se agrega a la hora del servidor.

Después, si se trata de la primera actualización que se recibe del servidor SNTP actual, el cliente SNTP determina si debe pasar por alto la diferencia entre la hora local del servidor y la del cliente. A partir de ese momento, se evalúan todas las actualizaciones del servidor SNTP para detectar la diferencia con la hora local del cliente.

La diferencia entre la hora del cliente y del servidor se compara con el valor de `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT`. Si supera este valor, los datos se descartan. Si la diferencia es menor que el valor de `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT`, se considera demasiado pequeña para necesitar ajuste.

Tras superar todas estas comprobaciones, la actualización de hora se aplica al cliente SNTP con algunas correcciones por los retrasos en el procesamiento interno del cliente SNTP.

### <a name="sntp-asynchronous-unicast-requests"></a>Solicitudes asincrónicas de unidifusión SNTP 

El cliente SNTP permite que la aplicación host envíe de forma asincrónica una solicitud de unidifusión de la hora actual desde el servidor NTP.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

La opción de espera indica cuándo se deja de esperar una respuesta.

Si el servidor NTP responde, el paquete está sujeto al mismo procesamiento y las mismas comprobaciones de integridad que se han descrito en la sección anterior antes de actualizar la hora local del cliente SNTP.

Si la llamada devuelve una finalización correcta, la aplicación puede llamar a *nx_sntp_client_utility_display_date_time* o a *nx_sntp_client_get_local_time_extended* para obtener la hora local actualizada.

Estas solicitudes de unidifusión no interfieren con la programación normal del cliente SNTP para enviar la siguiente solicitud de unidifusión ni, en el modo de difusión, con el momento en el que se espera la siguiente difusión NTP.

### <a name="periodic-local-time-updates"></a>Actualizaciones periódicas de la hora local

El ajuste máximo de la hora local se establece en la opción NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (en milisegundos). El intervalo de actualización de sondeo para las operaciones de unidifusión del cliente SNTP se establece en la opción NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (en segundos). Si el intervalo de sondeo es mayor que el ajuste máximo, se rechazarán las actualizaciones del servidor siguientes a la primera actualización. Para evitar que esto suceda, el cliente SNTP actualizará la hora local que se define periódicamente como NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

Si hay una diferencia en la hora entre el RTC incorporado y el servidor (la hora en la que se debe establecer la hora local del cliente SNTP), el RTC se debe sincronizar con la hora del cliente SNTP (esta operación no se muestra en este manual del usuario).

Puesto que las actualizaciones del servidor SNTP no deben producirse más de una vez por hora, no resulta útil sondear el cliente SNTP para ver si hay actualizaciones del servidor o para conocer el estado del servidor con más frecuencia. Sin embargo, el cliente SNTP debe actualizar su reloj local con la frecuencia suficiente como para no superar el parámetro de ajuste de tiempo máximo NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Como alternativa, se puede establecer el ajuste máximo NX_SNTP_CLIENT_MAX_TIME_LAPSE en un valor mayor que la actualización de sondeo de unidifusión (o intervalos de difusión anticipados). En este último caso se elimina la necesidad de un reloj en tiempo real independiente. Sin embargo, la intención del protocolo SNTP es evitar la dependencia total de las actualizaciones de hora de la red o del RTC local. Además, las actualizaciones del servidor SNTP están diseñadas para evitar el desfase en el reloj de hora local.

## <a name="multiple-network-interfaces"></a>Varias interfaces de red

El cliente SNTP de NetX Duo se puede configurar para ejecutarse en redes secundarias, siempre y cuando esas redes estén registradas con la instancia de IP. Consulte el manual del usuario de NetX Duo o NetX para obtener más información sobre cómo registrar redes secundarias.

En la llamada a *nx_sntp_client_create*, establezca la tercera entrada, iface_index, en el índice de la red donde el cliente SNTP recibirá las actualizaciones de hora. La interfaz principal siempre está en el índice 0. El cliente SNTP de NetX Duo no admite actualizaciones de hora simultáneamente en varias interfaces de red.

## <a name="sntp-and-ntp-rfcs"></a>Publicaciones RFC para SNTP y NTP

El cliente SNTP de NetX Duo es compatible con la RFC4330 de protocolo simple de tiempo de redes (SNTP) versión 4 para IPv4, IPv6 y OSI y otras RFC relacionadas.