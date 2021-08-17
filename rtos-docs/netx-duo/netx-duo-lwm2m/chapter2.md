---
title: 'Capítulo 2: Instalación y uso del cliente LWM2M de NetX Duo para RTOS'
description: En este capítulo se explica cómo instalar y usar el cliente LWM2M de NetX Duo para RTOS.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f804ae59dd639ca05d1b8f5251cf8b878e78bb9ad2575e08c21d43b14e727a19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796521"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Capítulo 2: Instalación y uso del cliente LWM2M

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente cliente LWM2M.

## <a name="product-distribution"></a>Distribución del producto

El cliente LWM2M para Azure RTOS se puede obtener de nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/). El paquete incluye tres archivos de origen, uno de los archivos de inclusión, como se indica a continuación.

* **nx\_lwm2m\_client.h** Archivo de encabezado del cliente LWM2M

* **nx\_lwm2m\_client.c** Archivos de origen de C para el cliente LWM2M

* **demo\_netx\_lwm2m\_client.c** Archivo de origen de C de la demostración de cliente LWM2M

## <a name="lwm2m-client-installation"></a>Instalación de cliente LWM2M

El cliente LWM2M forma parte de NetX Duo. Por lo tanto, después de clonar NetX Duo desde el repositorio de GitHub, se puede encontrar el origen del cliente LWM2M en ***netxduo/addons/LWM2M***.

## <a name="using-lwm2m_client"></a>Uso del cliente LWM2M

El uso del cliente LWM2M es sencillo. Básicamente, el código de la aplicación debe incluir ***nx\_lwm2m\_client.h**después de incluir*_tx\_api.h_*y*_nx\_api.h_ *, con el fin de usar ThreadX y NetX. Una vez que se incluye* _nx\_lwm2m\_client.h_ *, el código de aplicación puede realizar las llamadas de función del cliente LWM2M especificadas más adelante en esta guía. La aplicación también debe importar los archivos* nx\_lwm2m\_client\_.\**** en la biblioteca NetX.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca cliente LWM2M y la aplicación mediante el cliente LWM2M. Las opciones de configuración pueden definirse en el origen de la aplicación, en la línea de comandos, a menos que se especifique lo contrario.

| Opción de configuración | Descripción |
| --- | --- |
| **NX\_LWM2M\_CLIENT\_MTU** | Especifica el tamaño máximo de un mensaje CoAP, incluidos los encabezados IP y UDP. El valor predeterminado es 1280. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TOS** | Tipo de servicio necesario para el UDP de LwM2M. De forma predeterminada, este valor se define como NX\_IP\_NORMAL para indicar el servicio de paquetes IP normal. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TTL** | Especifica el número de enrutadores que este paquete puede pasar antes de que se descarte. El valor predeterminado se define en 0x80. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_QUEUE\_MAX** | Especifica el número máximo de profundidades de la cola de recepción. El valor predeterminado se establece en 4. |
| **NX\_LWM2M\_CLIENT\_MAX\_COAP\_URI\_PATH** | Especifica el número máximo de longitudes de la opción CoAP Uri-Path. El valor predeterminado se establece en 32. |
| **NX\_LWM2M\_CLIENT\_MAX\_DEVICE\_ERRORS** | Especifica el número máximo de códigos de error almacenados por el objeto de dispositivo. El valor predeterminado es 8. |
| **NX\_LWM2M\_CLIENT\_MAX\_SECURITY\_INSTANCES** | Especifica el número máximo de instancias de objeto de seguridad. El valor predeterminado es 2 para admitir un servidor de arranque y un servidor estándar. |
| **NX\_LWM2M\_CLIENT\_MAX\_SERVER\_INSTANCES** | Especifica el número máximo de instancias de objeto de servidor. El valor predeterminado es 1 para admitir un solo servidor estándar. |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_INSTANCES** | Especifica el número máximo de instancias de Access Control. El valor predeterminado es 0, que deshabilita el control de acceso. Si la aplicación admite más de un servidor LWM2M, el número máximo de instancias de Access Control debe establecerse en el número máximo de instancias de objeto que admitirá el cliente LWM2M, ya que se debe crear una instancia de Access Control para cada instancia de objeto (excepto las instancias de objeto de seguridad). |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_ACLS** | Especifica el número máximo de recursos de ACL por instancia de Access Control. El valor predeterminado es 4. |
| **NX\_LWM2M\_CLIENT\_MAX\_NOTIFICATIONS** | Especifica el número máximo de notificaciones que admitirá el cliente LWM2M. Un servidor LWM2M puede establecer notificaciones en objetos, instancias de objeto y recursos. El valor predeterminado es 8. |
| **NX\_LWM2M\_CLIENT\_MAX\_RESOURCES** | Especifica el número máximo de recursos por objeto. El valor predeterminado es 32. |
| **NX\_LWM2M\_CLIENT\_MAX\_MULTIPLE\_RESOURCES** | Especifica el número máximo de instancias de recursos para varios recursos. El valor predeterminado es 8. |
| **NX\_LWM2M\_CLIENT\_BOOTSTRAP\_IDLE\_TIMER** | Especifica el tiempo máximo de espera para las solicitudes del servidor de arranque cuando se inicia la sesión de arranque antes de anular la sesión. El valor predeterminado es de 60 segundos. |
| **NX\_LWM2M\_CLIENT\_DTLS\_START\_TIMEOUT** | Especifica el tiempo máximo de espera para la finalización del protocolo de enlace de DTLS. El valor predeterminado es 30 segundos. |
| **NX\_LWM2M\_CLIENT\_DTLS\_END\_TIMEOUT** | Especifica el tiempo máximo de espera para que se complete el apagado de DTLS. El valor predeterminado es de 5 segundos. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_URI** | Especifica la longitud máxima de un URI de servidor, incluido el carácter nulo de terminación. El valor predeterminado es 128. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_PUBLIC\_KEY\_OR\_IDENTITY** | Especifica la longitud máxima de la clave pública o la identidad de DTLS. El valor predeterminado es 128. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_PUBLIC\_KEY** | Especifica la longitud máxima de la clave pública del servidor de DTLS. El valor predeterminado es 128. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SECRET\_KEY** | Especifica la longitud máxima de la clave secreta de DTLS. El valor predeterminado es 128. |
| **NX\_LWM2M\_CLIENT\_HOLD\_OFF** | Especifica el número de segundos que se espera antes de que se inicie el arranque. El valor predeterminado es 1 segundo. |
| **NX\_LWM2M\_CLIENT\_LIFE\_TIME** | Especifica el número de segundos para la duración del registro. El valor predeterminado es 600 segundos. |
