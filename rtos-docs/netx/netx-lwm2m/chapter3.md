---
title: 'Capítulo 3: Descripción funcional de Azure RTOS NetX LWM2M'
description: Este capítulo contiene una descripción funcional de Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784944"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Capítulo 3: Descripción funcional de Azure RTOS NetX LWM2M

Este capítulo contiene una descripción funcional de Azure RTOS NetX LWM2M.

## <a name="lwm2m-client-initialization"></a>Inicialización del cliente LWM2M

El cliente LWM2M se inicializa mediante una llamada al servicio ***nx_lwm2m_client_create***. El cliente LWM2M se ejecuta en su propio subproceso y puede notificar algunos eventos a la aplicación mediante devoluciones de llamada o bien llamando a los métodos de los objetos personalizados implementados por la aplicación.

Además, las sesiones del cliente LWM2M deben crearse mediante una llamada a ***nx_lwm2m_client_session_create*** para habilitar la comunicación con uno o más servidores. Una sesión puede comunicarse con dos tipos de servidores diferentes: un servidor de arranque o un servidor LWM2M (administración de dispositivos).

### <a name="bootstrap-server-session"></a>Sesión del servidor de arranque

Una sesión de comunicación con un servidor de arranque se usa para aprovisionar información esencial en el cliente LWM2M para permitir que este realice la operación "Registro" con uno o varios servidores LWM2M. Este tipo de servidor se usa durante los modos de arranque iniciados por el cliente y por el servidor.

La aplicación puede iniciar una sesión de arranque mediante una llamada a ***nx_lwm2m_client_session_bootstrap** _ o _*_nx_lwm2m_client_session_bootstrap_dtls_*_; debe proporcionar la dirección IP y el número de puerto del servidor, y un identificador de instancia de objeto de seguridad opcional. La función _*_nx_lwm2m_client_session_bootstrap_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_bootstrap_dtls_** establece una conexión DTLS segura con el servidor.

Si la operación de arranque se realiza correctamente, el servidor de arranque debe haber creado instancias de objeto de seguridad para los servidores de arranque y LWM2M, e instancias de objeto de servidor para los servidores LWM2M. La aplicación debe utilizar esta información para establecer una sesión con los servidores LWM2M.

La aplicación debe guardar los datos de arranque en la memoria no volátil para configurar el cliente LWM2M en el siguiente reinicio del dispositivo.

### <a name="lwm2m-server-session"></a>Sesión del servidor LWM2M

Una sesión de comunicación con un servidor LWM2M se usa para el registro, la administración de dispositivos y la habilitación del servicio.

La aplicación puede registrar el cliente LWM2M en un servidor mediante una llamada a ***nx_lwm2m_client_session_register** _ o _*_nx_lwm2m_client_session_register_dtls_*_; debe proporcionar la dirección IP y el número de puerto del servidor, y el identificador de servidor corto que corresponde a una instancia de objeto de servidor existente. La función _*_nx_lwm2m_client_session_register_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_register_dtls_** establece una conexión DTLS segura con el servidor.

La aplicación puede anular el registro del cliente LWM2M mediante una llamada a ***nx_lwm2m_client_session_deregister** _ y pedir al cliente que envíe un mensaje de "actualización" mediante una llamada a _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Devolución de llamada de estado de sesión

La aplicación registra una devolución de llamada durante la creación de una sesión a la que se llama cuando se actualiza el estado de la sesión; la función de devolución de llamada NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK tiene el siguiente prototipo:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Los estados siguientes están definidos:

- **NX_LWM2M_CLIENT_SESSION_INIT**: el estado inicial después de la creación de la sesión.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: el cliente está esperando la expiración del temporizador "Hold Off" o el arranque iniciado por el servidor.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: el cliente envió un mensaje de "solicitud" al servidor de arranque (arranque iniciado por el cliente).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: el cliente recibe datos del servidor de arranque.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: el servidor de arranque envió un mensaje de "finalizado".

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: error en la sesión de arranque.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: el cliente envió un mensaje de "registro" al servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: el cliente está registrado en el servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: el cliente envió un mensaje de "actualización" al servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: el cliente envió un mensaje de "anulación de registro" al servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: se anuló el registro del cliente del servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: el servidor LWM2M está deshabilitado. Se enviará un mensaje de registro después de la expiración del temporizador de deshabilitación.

- **NX_LWM2M_CLIENT_SESSION_ERROR**: no se pudo realizar la operación de registro o actualización en el servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: se eliminó la instancia de objeto de servidor correspondiente al servidor LWM2M. En caso de error, la aplicación puede recuperar la causa del error mediante una llamada a **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Administración de dispositivos locales

La aplicación puede acceder a los objetos del cliente LWM2M mediante las funciones de administración de dispositivos locales. Se proporcionan las funciones siguientes:

- ***nx_lwm2m_client_object_read***: permite leer los recursos de una instancia de objeto.

- ***nx_lwm2m_client_object_discover***: permite obtener la lista de recursos de una instancia de objeto.

- ***nx_lwm2m_client_object_write***: permite escribir recursos en una instancia de objeto.

- ***nx_lwm2m_client_object_execute***: permite realizar la operación de ejecución en un recurso de una instancia de objeto.

- ***nx_lwm2m_client_object_create***: permite crear una instancia de objeto nueva.

- ***nx_lwm2m_client_object_delete***: permite eliminar una instancia de objeto existente.

- ***nx_lwm2m_client_object_get_next***: permite obtener el id. de objeto siguiente implementado por el cliente de LWM2M.

- ***nx_lwm2m_client_object_instance_get_next***: permite obtener la instancia siguiente de un objeto.

## <a name="resource-information"></a>Información de recursos

Al leer y escribir en objetos, un recurso se representa mediante la estructura de NX_LWM2M_RESOURCE. Esta estructura contiene el identificador del recurso o la instancia y su valor. La codificación del valor depende de su tipo y su origen (aplicación o red).

La estructura de NX_LWM2M_RESOURCE tiene la definición siguiente:

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: el id. del recurso o de la instancia.
- **nx_lwm2m_resource_type**: el tipo del valor (ver a continuación).
- **nx_lwm2m_resource_value**: el valor del recurso. Depende del tipo del valor.

Se definen los siguientes tipos de valores:

- **NX_LWM2M_RESOURCE_NONE**: recurso vacío.

- **NX_LWM2M_RESOURCE_STRING**: valor de cadena UTF-8 terminado en NULL almacenado en *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32**: valor entero de 32 bits almacenado en *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64**: valor entero de 64 bits almacenado en *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32**: valor de número de punto flotante de 32 bits almacenado en *nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64**: valor de número de punto flotante de 64 bits almacenado en *nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN**: valor booleano almacenado en *nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE**: valor opaco definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK**: valor de vínculo de objeto almacenado en *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV**: valor codificado TLV definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT**: valor codificado de texto sin formato definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE**: recurso múltiple definido por *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* es un puntero a una matriz de estructuras **NX_LWM2M_RESOURCE** que contienen información sobre cada instancia de recurso.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: recurso múltiple definido por *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* es un puntero a un búfer codificado TLV.

Se proporcionan funciones útiles para recuperar el valor y comprobar su tipo. La aplicación nunca debe acceder directamente al campo *nx_lwm2m_resource_value* al obtener un valor de una estructura NX_LWM2M_RESOURCE. Se definen las funciones siguientes:

- ***nx_lwm2m_resource_get_***: permite obtener un valor con el tipo determinado.
- ***nx_lwm2m_resource_multiple_get_***: permite obtener un valor con el tipo determinado a partir de un recurso múltiple.

La macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(tipo) se puede usar para comprobar si un tipo de recurso es un recurso múltiple.

## <a name="object-implementation"></a>Implementación de objetos

El cliente LWM2M implementa los siguientes objetos OMA LWM2M obligatorios: Seguridad (0), Servidor (1), Control de acceso (2) y Dispositivo (3). La aplicación debe implementar otros objetos específicos del dispositivo.

Se usan dos estructuras de datos para definir un objeto: la estructura NX_LWM2M_OBJECT define la implementación del objeto (incluidos el id. de objeto y los métodos de objeto) y la estructura NX_LWM2M_OBJECT_INSTANCE contiene los datos de una instancia de objeto.

La estructura de NX_LWM2M_OBJECT tiene la definición siguiente:

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next**: el objeto siguiente de la lista.
- **nx_lwm2m_object_id**: el id. del objeto.
- **nx_lwm2m_object_read**: el método "Read" (ver a continuación).
- **nx_lwm2m_object_discover**: el método "Discover" (ver a continuación).
- **nx_lwm2m_object_write**: el método "Write" (ver a continuación).
- **nx_lwm2m_object_execute**: el método "Execute" (ver a continuación).
- **nx_lwm2m_object_create**: el método "Create" (ver a continuación).
- **nx_lwm2m_object_delete**: el método "Delete" (ver a continuación).
- **nx_lwm2m_object_instances**: lista de instancias de objeto terminada en NULL.

La estructura NX_LWM2M_OBJECT_INSTANCE tiene la definición siguiente:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: la instancia siguiente de la lista.
- **nx_lwm2m_object_instance_id**: el id. de la instancia de objeto.

El objeto debe implementar los métodos que corresponden a las operaciones definidas por la interfaz de administración de dispositivos LWM2M: "Read", "Discover", "Write", "Execute", "Create" y "Delete". Los métodos "Create" y "Delete" se pueden establecer en NULL si el objeto no admite la creación dinámica de instancias.

### <a name="the-read-method"></a>Método "Read"

El método "Read" se usa para leer los valores de recursos de una instancia de objeto; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.

- **instance_ptr**: puntero a la instancia del objeto.

- **num_values**: número de recursos que se van a leer.

- **values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes.

### <a name="the-discover-method"></a>Método "Discover"

El método '"Discover" se usa para recuperar la lista de todos los recursos que un objeto implementa; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.

- **instance_ptr**: puntero a la instancia del objeto.

- **num_resources_ptr**: en la entrada, el tamaño del búfer de destino; en la salida, el número de elementos escritos en el búfer.

- **resources_ptr**: puntero al búfer de destino.

La información de los recursos se devuelve en una estructura NX_LWM2M_RESOURCE_INFO que se define como se indica a continuación:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: el id. del recurso.

- **nx_lwm2m_resource_info_flags**: ver a continuación.

- **nx_lwm2m_resource_info_dim**: la dimensión de un recurso múltiple si está establecida la marca NX_LWM2M_RESOURCE_INFO_MULTIPLE.

El campo *nx_lwm2m_resource_flags* puede tener los valores siguientes:

- 0: recurso legible único.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: recurso múltiple; se debe definir *nx_lwm2m_resource_info_dim*.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: recurso ejecutable o no legible.

### <a name="the-write-method"></a>Método "Write"

El método "Write" se usa para actualizar o reemplazar los recursos de una instancia de objeto; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.
- **instance_ptr**: puntero a la instancia del objeto.
- **num_values**: número de recursos que se van a escribir.
- **values_ptr**:puntero a los valores de los recursos.
- **write_op**: tipo de operaciones de escritura.

Se pueden especificar las operaciones de escritura siguientes en el parámetro *write_op*:

- 0 &mdash; Actualización parcial: agrega o actualiza los recursos proporcionados en el valor nuevo y deja sin modificar otros recursos existentes.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Reemplazo de instancia: reemplaza la instancia de objeto por los valores de recursos proporcionados nuevos.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Reemplazo de recurso: reemplaza los recursos por los valores de recursos proporcionados nuevos (se usa para reemplazar los recursos múltiples).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Creación de instancia: inicializa la instancia de objeto que recién se creó por los valores de recursos proporcionados (se llama desde el método *nx_lwm2m_object_create*).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Escritura de arranque: se llama durante la secuencia de arranque.

### <a name="the-execute-method"></a>Método "Execute"

El método "Execute" implementa la ejecución de un recurso de objeto; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.
- **instance_ptr**: puntero a la instancia del objeto.
- **resource_id**: id. del recurso.
- **arguments_ptr**: puntero a los argumentos de la operación de ejecución. Puede ser NULL si *arguments_length* es cero.
- **arguments_length**: longitud de los argumentos.

La función debe devolver NX_LWM2M_NOT_FOUND si el id. de recurso no existe, o bien NX_LWM2M_METHOD_NOT_ALLOWED si no admite la ejecución.

### <a name="the-create-method"></a>Método "Create"

El método "Create" implementa la creación de una instancia de objeto nueva; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.
- **instance_id**: id. de la instancia nueva.
- **num_values**: número de recursos que se van a inicializar.
- **values_ptr**:puntero a los valores de los recursos.
- **instance_ptr**: puntero al puntero de destino de la instancia creada.
- **bootstrap**: True si se llamada desde la secuencia de arranque.

El objeto debe asignar e inicializar una instancia de objeto nueva con la lista de valores de recursos proporcionada.

### <a name="the-delete-method"></a>Método "Delete"

El método "Delete" implementa la eliminación de una instancia de objeto; la función tiene la definición siguiente:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Los parámetros de entrada se definen de la manera siguiente:

- **object_ptr**: puntero a la implementación del objeto.
- **instance_ptr**: puntero a la instancia del objeto.

Si se ejecuta correctamente, el objeto debe liberar los datos de la instancia de objeto y cualquier otro recurso asignado por la instancia.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Incorporación de implementaciones e instancias de objeto al cliente LWM2M

La aplicación puede agregar una implementación de objeto nueva al cliente LWM2M mediante una llamada al servicio ***nx_lwm2m_client_object_add***.

Si el objeto no admite la creación dinámica de instancias (por ejemplo, si se trata de un objeto solo de instancia única), el campo *nx_lwm2m_object_instances* de la estructura del objeto debería apuntar a la lista de las estructuras de instancias estáticas.

Si el objeto admite la creación dinámica de instancias, *nx_lwm2m_object_instances* se debe establecer en NULL y, en su lugar, se debe usar el servicio ***nx_lwm2m_client_object_create*** para llamar al método "Create" del objeto.

## <a name="example-of-lwm2m-client-application"></a>Ejemplo de aplicación cliente LWM2M

El código siguiente es un ejemplo de una aplicación cliente LWM2M simple que implementa un dispositivo personalizado que consta de un sensor de temperatura y un interruptor de luz.

El dispositivo permite que un servidor lea el valor del sensor de temperatura y el estado booleano del interruptor de luz, así como encender y apagar dicho dispositivo.

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
