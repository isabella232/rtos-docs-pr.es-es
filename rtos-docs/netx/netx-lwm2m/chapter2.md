---
title: 'Capítulo 2: Instalación y uso de LWM2M de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente LWM2M de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791234"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Capítulo 2: Instalación y uso de LWM2M de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente LWM2M de Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

LWM2M de NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). El paquete incluye tres archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_lwm2m_client.h**: archivo de encabezado para el cliente NetX LWM2M

- **nx_lwm2m_*.c/h**: archivos de código fuente de C/H para NetX LWM2M

- **demo_netx_lwm2m_client.c**: archivo de código fuente C para la demostración de cliente NetX LWM2M

- **NetX_LWM2M_User_Guide.pdf**: descripción en PDF del producto NetX LWM2M

## <a name="netx-lwm2m-installation"></a>Instalación de NetX LWM2M

Para usar NetX LWM2M, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\\threadx\\arm7\\green*", los archivos *nx_lwm2m&#42;.&#42;* deben copiarse en ese mismo directorio.

## <a name="using-netx-lwm2m"></a>Uso de NetX LWM2M

El uso de NetX LWM2M es fácil. Básicamente, el código de la aplicación debe incluir *nx_lwm2m_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX. Después de incluir *nx_lwm2m_client.h*, el código de la aplicación puede realizar las llamadas de función NetX LWM2M que se especifican más adelante en este manual. La aplicación también debe importar los archivos *nx_lwm2m&#42;.&#42;* en la biblioteca de NetX.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca cliente LWM2M y la aplicación mediante el cliente LWM2M. Las opciones de configuración pueden definirse en el origen de la aplicación, en la línea de comandos, a menos que se especifique lo contrario.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Si se define, quita la API de comprobación de errores de cliente de LWM2M básica y mejora el rendimiento. Los códigos de retorno de API no afectados al deshabilitar la comprobación de errores se muestran en negrita en la definición de la API.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Si se define, quita la compatibilidad de los valores de números de punto flotante. Cuando está deshabilitado, el cliente de LWM2M no admite recursos con el tipo de datos float.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Si se define, quita la compatibilidad de los valores de números de punto flotante de 64 bits. El cliente de LWM2M todavía puede recibir mensajes TLV que contienen números flotantes de 64 bits, pero los valores se convierten en un número de punto flotante de 32 bits para su procesamiento.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Especifica la prioridad del subproceso del cliente LWM2M. De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Especifica el número máximo de códigos de error almacenados por el objeto de dispositivo. El valor predeterminado es 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Especifica el número máximo de instancias de objeto de seguridad. El valor predeterminado es 2 para admitir un servidor de arranque y un servidor estándar.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Especifica el número máximo de instancias de objeto de servidor. El valor predeterminado es 1 para admitir un solo servidor estándar.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Especifica la longitud máxima de un URI de servidor, incluido el carácter nulo de terminación. El valor predeterminado es 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Especifica el número máximo de instancias de Access Control. El valor predeterminado es 0, que deshabilita el control de acceso. Si la aplicación admite más de un servidor LWM2M, el número máximo de instancias de Access Control debe establecerse en el número máximo de instancias de objeto que admitirá el cliente LWM2M, ya que se debe crear una instancia de Access Control para cada instancia de objeto (excepto las instancias de objeto de seguridad).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Especifica el número máximo de recursos de ACL por instancia de Access Control. El valor predeterminado es 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Especifica el número máximo de notificaciones que el cliente de LWM2M admitirá. Un servidor LWM2M puede establecer notificaciones en objetos, instancias de objeto y recursos. El valor predeterminado es 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Especifica el número máximo de recursos por objeto. El valor predeterminado es 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Especifica el tiempo máximo de espera para las solicitudes del servidor de arranque cuando se inicia la sesión de arranque antes de anular la sesión. El valor predeterminado es de 60 segundos.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Especifica el tiempo máximo de espera para la finalización del protocolo de enlace de DTLS. El valor predeterminado es 30 segundos.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Especifica el tiempo máximo de espera para que se complete el apagado de DTLS. El valor predeterminado es de 5 segundos.
