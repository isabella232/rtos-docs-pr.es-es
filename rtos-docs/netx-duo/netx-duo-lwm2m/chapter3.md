---
title: 'Capítulo 3: Descripción funcional del cliente LWM2M'
description: Este capítulo contiene una descripción funcional del cliente LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be6d9d854ce89140ce749fbeb0364678077337bf19ddc1055d286d0f624e8bd5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783465"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Capítulo 3: Descripción funcional del cliente LWM2M

> Este capítulo contiene una descripción funcional del cliente LWM2M.

## <a name="lwm2m-client-initialization"></a>Inicialización del cliente LWM2M

El cliente LWM2M se inicializa mediante una llamada al servicio ***nx_lwm2m_client_create***. El cliente LWM2M se ejecuta en su propio subproceso y puede notificar algunos eventos a la aplicación mediante devoluciones de llamada o bien llamando a los métodos de los objetos personalizados implementados por la aplicación.

Además, las sesiones del cliente LWM2M deben crearse mediante una llamada a ***nx_lwm2m_client_session_create*** para habilitar la comunicación con uno o más servidores. Una sesión puede comunicarse con dos tipos de servidores diferentes: un servidor de arranque o un servidor LWM2M (administración de dispositivos).

### <a name="bootstrap-server-session"></a>Sesión del servidor de arranque

Una sesión de comunicación con un servidor de arranque se usa para aprovisionar información esencial en el cliente LWM2M para permitir que dicho realice la operación de registro con uno o varios servidores LWM2M. Este tipo de servidor se usa durante los modos de arranque iniciados por el cliente y por el servidor.

La aplicación puede iniciar una sesión de arranque mediante una llamada a ***nx_lwm2m_client_session_bootstrap** _ o _*_nx_lwm2m_client_session_bootstrap_dtls_*_; debe proporcionar la dirección IP y el número de puerto del servidor, y un identificador de instancia de objeto de seguridad opcional. La función _*_nx_lwm2m_client_session_bootstrap_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_bootstrap_dtls_** establece una conexión DTLS segura con el servidor.

Si la operación de arranque se realiza correctamente, el servidor de arranque debe haber creado instancias de objeto de seguridad para los servidores de arranque y LWM2M, e instancias de objeto de servidor para los servidores LWM2M. La aplicación puede llamar a ***nx_lwm2m_client_session_register_info_get*** para obtener información de los servidores LWM2M y usar esta información para establecer una sesión con dichos servidores.

La aplicación debe guardar los datos de arranque en la memoria no volátil para configurar el cliente LWM2M en el siguiente reinicio del dispositivo.

### <a name="lwm2m-server-session"></a>Sesión del servidor LWM2M

Una sesión de comunicación con un servidor LWM2M se usa para el registro, la administración de dispositivos y la habilitación del servicio.

La aplicación puede registrar el cliente LWM2M en un servidor mediante una llamada a ***nx_lwm2m_client_session_register** _ o _*_nx_lwm2m_client_session_register_dtls_*_; debe proporcionar la dirección IP y el número de puerto del servidor, y el identificador de servidor corto que corresponde a una instancia de objeto de servidor existente. La función _*_nx_lwm2m_client_session_register_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_register_dtls_** establece una conexión DTLS segura con el servidor.

La aplicación puede anular el registro del cliente LWM2M mediante una llamada a ***nx_lwm2m_client_session_deregister** _ y pedir al cliente que envíe un mensaje de actualización mediante una llamada a _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Devolución de llamada de estado de sesión

La aplicación registra una devolución de llamada durante la creación de una sesión a la que se llama cuando se actualiza el estado de la sesión; la función de devolución de llamada **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** tiene el siguiente prototipo.

typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);

Los estados siguientes están definidos.

| Estado de&nbsp;la sesión | Descripción |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Estado inicial después de la creación de la sesión. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | El cliente está esperando la expiración del temporizador "Hold Off" o el arranque iniciado por el servidor. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | El cliente ha enviado un mensaje de solicitud al servidor de arranque (arranque iniciado por el cliente). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | El cliente recibe datos del servidor de arranque. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | El servidor de arranque ha enviado un mensaje de finalización. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Error en la sesión de arranque. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | El cliente ha enviado un mensaje de registro al servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | El cliente está registrado en el servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | El cliente ha enviado un mensaje de actualización al servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | El cliente ha enviado un mensaje de anulación de registro al servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Se anuló el registro del cliente en el servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | El servidor LWM2M está deshabilitado. Se enviará un mensaje de registro después de la expiración del temporizador de deshabilitación. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | No se pudo realizar la operación de registro o actualización en el servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Se eliminó la instancia de objeto de servidor correspondiente al servidor LWM2M. |

En caso de error, la aplicación puede recuperar la causa del error mediante una llamada a ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Administración de dispositivos locales

La aplicación puede acceder a los objetos del cliente LWM2M mediante las funciones de administración de dispositivos locales. Se proporciona las siguientes funciones.

| Nombre de&nbsp;la función | Descripción |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Permite leer recursos de una instancia de objeto. |
| ***nx_lwm2m_client_object_discover*** | Permite obtener la lista de los recursos de una instancia de objeto.
| ***nx_lwm2m_client_object_write*** | Permite escribir recursos en una instancia de objeto. |
| ***nx_lwm2m_client_object_execute*** | Permite realizar una operación de ejecución en un recurso de una instancia de objeto. |
| ***nx_lwm2m_client_object_create*** | Permite crear una instancia de objeto. |
| ***nx_lwm2m_client_object_delete*** | Permite eliminar una instancia de objeto existente. |
| ***nx_lwm2m_client_object_next_get*** | Permite obtener el id. de objeto siguiente mediante el cliente LWM2M. |
| ***nx_lwm2m_client_object_instance_next_get*** | Permite obtener la siguiente instancia de un objeto. |

## <a name="resource-information"></a>Información de recursos

Al leer y escribir en objetos, un recurso se representa mediante la estructura de NX_LWM2M_CLIENT_RESOURCE. Esta estructura contiene el identificador del recurso o la instancia y su valor.

Se proporcionan las siguientes funciones para establecer la información y el valor de los recursos.

| Nombre de&nbsp;la función | Descripción |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Permite establecer la información de los recursos. Id. de recurso y operación: READ, WRITE, EXECUTABLE. |
| ***nx_lwm2m_client_resource_string_set*** | Permite establecer el valor del recurso como una cadena. |
| ***nx_lwm2m_client_resource_integer32_set*** | Permite establecer el valor del recurso como un entero de 32 bits. |
| ***nx_lwm2m_client_resource_integer64_set*** | Permite establecer el valor del recurso como un entero de 64 bits. |
| ***nx_lwm2m_client_resource_float32_set*** | Permite establecer el recurso en un valor flotante de 32 bits. |
| ***nx_lwm2m_client_resource_float64_set*** | Permite establecer el recurso en un valor flotante de 64 bits. |
| ***nx_lwm2m_client_resource_boolean_set*** | Permite establecer el recurso en un valor booleano. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Permite establecer el valor del recurso como un vínculo de objeto. |
| ***nx_lwm2m_client_resource_opaque_set*** | Permite establecer el recurso en un valor opaco. |
| ***nx_lwm2m_client_resource_instance_set*** | Permite establecer el valor del recurso como una instancia para varios recursos. |
| ***nx_lwm2m_client_resource_dim_set*** | Permite establecer la dimensión del recurso para varios recursos con fines de detección. |

Se proporcionan las siguientes funciones para obtener la información y el valor de los recursos.

| Nombre de&nbsp;la función | Descripción |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Permite obtener la información de los recursos. Id. de recurso y operación: READ, WRITE, EXECUTABLE. |
| ***nx_lwm2m_client_resource_string_get*** | Permite obtener el valor de un recurso string. |
| ***nx_lwm2m_client_resource_integer32_get*** | Permite obtener el valor de un recurso integer de 32 bits. |
| ***nx_lwm2m_client_resource_integer64_get*** | Permite obtener el valor de un recurso integer de 64 bits. |
| ***nx_lwm2m_client_resource_float32_get*** | Permite obtener el valor de un recurso float de 32 bits. |
| ***nx_lwm2m_client_resource_float64_get*** | Permite obtener el valor de un recurso float de 64 bits. |
| ***nx_lwm2m_client_resource_boolean_get*** | Obtiene el valor de un recurso boolean. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Permite obtener el valor de un recurso de vínculo de objeto |
| ***nx_lwm2m_client_resource_opaque_get*** | Permite obtener el valor de un recurso opaque. |
| ***nx_lwm2m_client_resource_instance_get*** | Permite obtener la instancia de recurso para varios recursos. |
| ***nx_lwm2m_client_resource_dim_get*** | Permite obtener la dimensión de recurso para varios recursos. |

## <a name="object-implementation"></a>Implementación de objetos

El cliente LWM2M implementa los siguientes objetos OMA LWM2M obligatorios: Seguridad (0), Servidor (1), Control de acceso (2) y Dispositivo (3). La aplicación debe implementar otros objetos específicos del dispositivo.

Se usan dos estructuras de datos para definir un objeto: la estructura NX_LWM2M_CLIENT_OBJECT define la implementación del objeto (incluidos el id. de objeto y los métodos de objeto) y la estructura NX_LWM2M_CLIENT_OBJECT_INSTANCE contiene los datos de una instancia de objeto.

Se proporciona las siguientes funciones.

| Nombre de&nbsp;la función | Descripción |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Permite agregar la implementación de objeto al cliente LWM2M. |
| ***nx_lwm2m_client_object_remove*** | Permite quitar la implementación de objeto del cliente LWM2M. |
| ***nx_lwm2m_client_object_instance_add*** | Permite agregar una instancia de objeto al objeto. |
| ***nx_lwm2m_client_object_instance_remove*** | Permite quitar la instancia de objeto del objeto. |

La función de devolución de llamada del método de objeto tiene la firma que se muestra a continuación.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>Método "Read"

El método "Read" se usa para leer los valores de recursos de una instancia de objeto. Los parámetros se definen como se indica a continuación.

| Parámetro | Descripción |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Puntero a la instancia del objeto. |
| **resource** | Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes. |
| **resource_count** | Puntero al número de recursos que se van a leer. |
| **args_ptr** | Parámetro sin usar para la lectura. |
| **args_length** | Parámetro sin usar para la lectura. |

### <a name="the-discover-method"></a>Método "Discover"

El método "Discover" se usa para recuperar la lista de todos los recursos implementados por un objeto. Los parámetros se definen como se indica a continuación.

| Parámetro | Descripción |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Puntero a la instancia del objeto. |
| **resource** | Puntero a una matriz de NX_LWM2M_CLIENT_RESOURCE. En la devolución, la matriz se rellena con la información de recursos correspondiente. |
| **resource_count** | Puntero al número de recursos que se van a detectar. En la devolución, este parámetro debe actualizarse como el valor true. |
| **args_ptr** | Parámetro sin usar para la detección. |
| **args_length** | Parámetro sin usar para la detección. |

### <a name="the-write-method"></a>Método "Write"

El método "Write" se usa para actualizar o reemplazar los recursos de una instancia de objeto. Los parámetros se definen como se indica a continuación.

| Parámetro  | Descripción |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Puntero a la instancia del objeto. |
| **resource** | Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes. |
| **resource_count** | Puntero al número de recursos que se van a detectar. |
| **args_ptr** | Marcas de escritura. |
| **args_length** | Longitud de los argumentos. |

Se pueden especificar las siguientes operaciones de escritura en el parámetro *flag*.

| Operación | Acción | Descripción |
| --- | ---| --- |
| 0 | Actualización parcial | Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Reemplazo de instancia | Reemplaza la instancia de objeto por los nuevos valores de recursos proporcionados.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Reemplazo de recurso | Reemplaza los recursos por los nuevos valores de recursos proporcionados (usados para reemplazar varios recursos). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Create Instance | Inicializa la instancia del objeto recién creada con los valores de recursos proporcionados (llamados desde el método **_nx_lwm2m_object_create_**). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Escritura de arranque | Se llama durante la secuencia de arranque. |

### <a name="the-execute-method"></a>Método "Execute"

El método "Execute" implementa la ejecución de un recurso de objeto.

Los parámetros de entrada se definen de la manera siguiente.

| Parámetro  | Descripción |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Puntero a la instancia del objeto. |
| **resource** | Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes. |
| **resource_count** | Puntero al número de recursos que se van a detectar. |
| **args_ptr** | Puntero a los argumentos. |
| **args_length** | Longitud de los argumentos.  |

La función debe devolver **NX_LWM2M_CLIENT_NOT_FOUND** si el identificador de recurso no existe, o bien **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** si no admite la ejecución.

### <a name="the-create-method"></a>Método "Create"

El método "Create" implementa la creación de una instancia de objeto.

Los parámetros de entrada se definen de la manera siguiente.

| Parámetro  | Descripción |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Parámetro sin usar. |
| **resource** | Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes. |
| **resource_count** | Puntero al número de recursos que se van a detectar. |
| **args_ptr** | Id. de instancia de objeto. |
| **args_length** | Longitud de los argumentos. |

### <a name="the-delete-method"></a>Método "Delete"

El método "Delete" implementa la eliminación de una instancia de objeto. Los parámetros de entrada se definen como se indica a continuación.

| Parámetro  | Descripción |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Puntero a la implementación del objeto. |
| **instance_ptr** | Puntero a la instancia del objeto. |
| **resource** | Parámetro sin usar. |
| **resource_count** | Parámetro sin usar. |
| **args_ptr** | Parámetro sin usar. |
| **args_length** | Parámetro sin usar. |

Si se ejecuta correctamente, el objeto debe liberar los datos de la instancia de objeto y cualquier otro recurso asignado por la instancia.

## <a name="example-of-lwm2m-client-application"></a>Ejemplo de aplicación cliente LWM2M

El código siguiente es un ejemplo de una aplicación cliente LWM2M simple que implementa un dispositivo personalizado que consta de un sensor de temperatura y un interruptor de luz.

El dispositivo permite que un servidor lea el valor del sensor de temperatura y el estado booleano del interruptor de luz, así como encender y apagar dicho dispositivo.

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```