---
title: 'Capítulo 2: Instalación y uso de mDNS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del módulo mDSN de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b27671f82c100db4e6a70a568e8a68f14b3ab45e3a33f46dd1f2e1852010f500
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796436"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Capítulo 2: Instalación y uso de mDNS

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del módulo mDSN de NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

mDNS de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nxd_mdns.h** Archivo de encabezado del módulo mDNS de NetX Duo.
- **nxd_mdns.c** Archivo de código fuente de C del módulo mDNS de NetX Duo.
- **nxd_mdns.pdf** Descripción del archivo PDF de mDNS de NetX Duo.
- **demo_netxduo_mdns.c** Un sencillo programa de demostración que ilustra los servicios proporcionados por mDNS.

## <a name="netx-duo-mdns-installation"></a>Instalación de mDNS de NetX Duo

Para usar las API de mDNS de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio "*c:\netxduo*", se deben copiar *nxd_mdns.h* y *nxd_mdns.c* en este directorio.

## <a name="using-netx-duo-mdns"></a>Uso de mDNS de NetX Duo

Usar el módulo mDNS de NetX Duo es sencillo. Básicamente, el código de la aplicación debe incluir *nxd_dns.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX Duo, respectivamente. El proyecto de compilación debe incluir el código fuente y el archivo de aplicación de mDNS, y, por supuesto, los archivos de biblioteca ThreadX y NetX. Esto es todo lo que se necesita para usar mDNS de NetX Duo.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar el módulo mDNS de NetX Duo. Aunque se muestran los valores predeterminados, la aplicación puede establecer cada definición antes de incluir el archivo de encabezado de mDNS de NetX Duo especificado. En la lista siguiente se describe cada una de forma detallada:

- **NX_MDNS_DISABLE_SERVER** Deshabilita la funcionalidad de servidor de mDNS/DNS-SD. Sin esta funcionalidad, el módulo mDNS/DNS-SD no anuncia los servicios proporcionados por el host local ni responde a las preguntas de mDNS. De forma predeterminada, este símbolo no está definido.
- **NX_MDNS_DISABLE_CLIENT** Deshabilita la funcionalidad de cliente de mDNS/DNS-SD. Sin la funcionalidad de cliente, mDNS/DNS-SD no envía consultas ni mantiene las respuestas a las consultas de mDNS recibidas a través de la red.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** Cuando se define, el módulo mDNS realiza validaciones de direcciones (dirección de origen, dirección de destino y números de puerto) de los mensajes de mDNS recibidos. Este símbolo se define de forma predeterminada.
- **NX_MDNS_ENABLE_CLIENT_POOF** Cuando se define, el módulo mDNS realiza una observación pasiva de los errores y el cliente de mDNS/DNS_SD (solicitante) observa las consultas de multidifusión emitidas por los demás hosts de la red. Este símbolo se define de forma predeterminada.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Cuando se define, el servidor de mDNS/DNS-SD (respondedor) genera respuestas negativas a las consultas para las que tiene una propiedad legítima. Este símbolo se define de forma predeterminada.
- **NX_MDNS_ENABLE_IPV6** Cuando se define, mDNS/DNS-SD envía o procesa el mensaje de mDNS a través de la dirección IPv6. De forma predeterminada, este símbolo no está definido.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Número máximo de direcciones IPv6 del host. El valor predeterminado es 2.
- **NX_MDNS_HOST_NAME_MAX** Tamaño máximo de la cadena en el nombre de host. El valor predeterminado es 64. No incluye el terminador NULL.
- **NX_MDNS_SERVICE_NAME_MAX** Tamaño máximo de la cadena en el nombre del servicio. El valor predeterminado es 64. No incluye el terminador NULL.
- **NX_MDNS_DOMAIN_NAME_MAX** Tamaño máximo de la cadena en el nombre de dominio. El valor predeterminado es 16. No incluye el terminador NULL.
- **NX_MDNS_CONFLICT_COUNT** Número máximo de conflictos en el nombre de host o el nombre del servicio. El valor predeterminado es 8.
- **NX_MDNS_RR_TTL_HOST** Valor de TTL para registros de recursos con el nombre de host, en segundos. El valor predeterminado es 120 para 120 segundos.
- **NX_MDNS_RR_TTL_OTHER** Valor de TTL para otros registros de recursos, en segundos. El valor predeterminado es 4500 para 75 minutos.
- **NX_MDNS_PROBING_TIMER_COUNT** Intervalo de tiempo, en tics, entre los mensajes de sondeo de mDNS. El valor predeterminado es 25 tics para 250 ms.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** Intervalo de tiempo, en tics, entre los mensajes de anuncio de mDNS. El valor predeterminado es 25 tics para 250 ms.
- **NX_MDNS_GOODBYE_TIMER_COUNT** Intervalo de tiempo, en tics, entre mensajes de despedida repetidos. El valor predeterminado es 25 tics para 250 ms.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** Intervalo de tiempo mínimo, en tics, entre dos consultas. El valor predeterminado es 100 tics para 1 segundo.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** Intervalo de tiempo máximo, en tics, entre dos consultas. El valor predeterminado es 360 000 para 60 segundos.
- **NX_MDNS_QUERY_DELAY_MIN** Retraso mínimo para enviar la primera consulta, en tics. El valor predeterminado es 2 tics para 20 ms.
- **NX_MDNS_QUERY_DELAY_RANGE** Intervalo de retraso para enviar la primera consulta, en tics. El valor predeterminado es 10 tics para 100 ms.
- **NX_MDNS_RESPONSE_INTERVAL** Intervalo de tiempo, en tics, en responder a una consulta para garantizar un intervalo de al menos 1 s desde la última vez que el registro se transmitió por multidifusión. El valor predeterminado es 100 tics.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** Intervalo de tiempo, en tics, en responder a las consultas de sondeo para garantizar un intervalo de al menos 250 ms desde la última vez que el registro se transmitió por multidifusión. El valor predeterminado es 25 tics.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** Retraso, en tics, en responder a una consulta a un servicio que es único en la red local. El valor predeterminado es 1 tic para 10 ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** Retraso mínimo, en tics, en responder a una consulta a un recurso compartido. El valor predeterminado es 2 tics para 20 ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** Intervalo de retraso, en tics, en responder a una consulta a un recurso compartido. El valor predeterminado es 10 tics para 100 ms.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** Retraso mínimo, en tics, en responder a una consulta con el bit TC. El valor predeterminado es 40 tics para 400 ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** Intervalo de retraso, en tics, en responder a una consulta con el bit TC. El valor predeterminado es 10 tics para 100 ms.
- **NX_MDNS_TIMER_COUNT_RANGE** Al enviar respuestas de mDNS, el paquete contiene respuestas que, de lo contrario, se enviarían dentro de este intervalo de contador de tiempo. El intervalo de recuento de tiempo se expresa en tics. El valor predeterminado es 12 para 120 ms. Este valor permite que una respuesta incluya mensajes que se enviarán en el próximo intervalo de 120 ms si cada tic es de 10 ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** Número de mensajes de sondeo retransmitidos. El valor predeterminado es 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** Número de mensajes de despedida retransmitidos. El valor predeterminado es 1.
- **NX_MDNS_POOF_MIN_COUNT** Número de consultas sin respuesta de multidifusión; el host puede tomar este valor como una indicación de que es posible que el registro ya no sea válido. El valor predeterminado es 2.
- **NX_MDNS_POOF_TIME_COUNT** Intervalo de tiempo, en tics, en eliminar el registro de la caché después de ver dos o más de estas consultas y observar que no hay ninguna respuesta de multidifusión que contenga la respuesta esperada. El valor predeterminado es 1000 tics para 10 segundos.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** Retraso para eliminar un registro de recursos cuando el TTL de este registro es cero, en tics. El valor predeterminado es de 100 tics para 1 segundo.
