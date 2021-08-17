---
title: 'Capítulo 2: Instalación de la compatibilidad de ThreadX con ARMv8-M'
description: En este capítulo se explica cómo instalar y usar el código fuente de ThreadX para la arquitectura ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 085310acd5262226e9ff3af440a5f05268c7799e78eda81334a13b736222b95c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801961"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Capítulo 2: Instalación de la compatibilidad de ThreadX con ARMv8-M

Hay archivos de código fuente de ThreadX adicionales que admiten la arquitectura ARMv8-M.

Si ThreadX se va a ejecutar en modo seguro, no se necesitan estos archivos y API adicionales. Para ejecutar ThreadX en modo seguro, defina el símbolo **TX_SECURE_EXECUTION** en la parte superior de **_tx_port.h_ *_ o en la línea de comandos o la configuración del proyecto. Asegúrese de definir* _TX_SECURE_EXECUTION** para todos los archivos de ensamblado y de c. ThreadX y la aplicación de usuario se ejecutarán en modo seguro.

Para ejecutar ThreadX y la aplicación de usuario en modo no seguro y admitir funciones seguras invocables no seguras, haga lo siguiente:

Se debe agregar el archivo ***tx_thread_secure_stack.c*** a la aplicación segura.

Se deben agregar los siguientes archivos a la biblioteca ThreadX.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

Los dos archivos siguientes reemplazan a los archivos genéricos de la biblioteca ThreadX.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Orígenes de ThreadX adicionales para ARMv8-M

A continuación se describen los archivos de ThreadX adicionales para la arquitectura TrustZone para ARMv8-M.

  | **Nombre de archivo**                            | **Contents**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | Archivo de inclusión que define las funciones ThreadX invocables no seguras. |
  | ***txe_thread_secure_stack_allocate.c*** |  Archivo de comprobación de errores de la API de asignación de pila segura. |
  | ***txe_thread_secure_stack_free.c***     |  Archivo de comprobación de errores de la API gratuita de pila segura. |
  | ***tx_thread_secure_stack_allocate.s***  |  Capa no segura para el servicio de asignación de pila segura. |
  | ***tx_thread_secure_stack_free.s***      |  Capa no segura para el servicio gratuito de pila segura. |
  | ***tx_thread_stack_error_handler.c***    |  Controlador de errores de pila de subprocesos. |
  | ***tx_thread_stack_error_notify.c***     |  Registra la devolución de llamada de notificación para controlar los errores de pila de subprocesos. |
