---
title: 'Capítulo 1: Introducción'
author: philmea
description: Este artículo ofrece información general sobre Azure RTOS ThreadX Modules.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9018c10e6fe92b2237ec94b633f2f0030ad1cef4bcbcb7afa5ace20548f012ed
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799442"
---
# <a name="chapter-1-overview"></a>Capítulo 1: Introducción

El componente ThreadX Modules proporciona una infraestructura para que las aplicaciones carguen dinámicamente los módulos que se compilan de forma independiente desde la parte residente de la aplicación. Esto es especialmente útil en situaciones en las que el tamaño del código de aplicación supera la memoria disponible. También puede ayudar cuando es necesario agregar nuevas características después de implementar la imagen principal. Además, se pueden usar módulos de carga dinámica cuando se requieren actualizaciones de firmware parciales.

La protección de memoria para el módulo cargado es opcional, en función de las propiedades especificadas en el preámbulo del propio módulo. Cuando se especifica la protección de memoria, el hardware de administración de memoria del procesador se configura de modo que los subprocesos del módulo solo pueden acceder al código y la memoria de datos del módulo. Cualquier ejecución o acceso a la memoria extraños provocará un error de memoria y que se finalice el subproceso de módulo infractor. Si en la aplicación se ha registrado la devolución de llamada de notificación de error de memoria, también se usará para avisar a la aplicación del error de memoria.

El componente ThreadX Modules se basa en la aplicación para proporcionar un área de memoria en la que se puedan cargar los módulos. El área de instrucciones de cada módulo puede ejecutarse in situ o copiarse en el área de memoria del módulo RAM para su ejecución. En cualquier caso, los requisitos de memoria de datos del módulo se asignan desde el área de memoria del módulo.

No hay ningún límite en el número de módulos que se pueden cargar a la vez (más allá de la cantidad de memoria disponible), en tanto que solo hay una copia del código del administrador de módulos residente. En la figura 1 se muestra la relación entre el administrador de módulos y los propios módulos.

![Relación entre los módulos y el administrador de módulos](media/image2.png)

**Figura 1** Módulos y administrador de módulos

Cada módulo debe tener su propia área de memoria; está área viene definida por la aplicación. El módulo y el administrador de módulos interactúan a través de una función de distribución de software por medio de identificadores de solicitud predefinidos que corresponden a los servicios de ThreadX solicitados por el módulo. Además, el módulo debe proporcionar un punto de entrada de un solo subproceso, así como el tamaño de pila necesario, la prioridad, el identificador de módulo, el tamaño y la prioridad de la pila de subprocesos de devolución de llamada, etc. Esta información se define en el preámbulo de cada módulo.

El administrador de módulos es responsable de crear el subproceso inicial del módulo e iniciar su ejecución. Una vez que se está ejecutando el subproceso inicial del módulo, el administrador de módulos es responsable de recibir todas las solicitudes de API de ThreadX realizadas por el módulo. Un módulo tiene acceso completo a la API de ThreadX, incluida la capacidad de crear subprocesos adicionales en el módulo.  
  
Las convenciones de nomenclatura del código fuente del módulo son sencillas: todos los archivos de código fuente del administrador de módulos se denominan ***txm_module_manager_\****  y todos los archivos asociados exclusivamente al módulo omiten la parte "**_manager_ *_" del nombre. El código fuente del módulo y del administrador comparten el archivo de inclusión principal _* _txm_module.h_**.
