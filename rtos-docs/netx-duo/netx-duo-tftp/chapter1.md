---
title: 'Capítulo 1: Introducción a TFTP de Azure RTOS NetX Duo'
description: El protocolo trivial de transferencia de archivos trivial (TFTP) es un protocolo ligero diseñado para las transferencias de archivos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4854f96d8f230d7c1f21700ac731d6430854a950009d3ed51fbf90d37885f255
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791982"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Capítulo 1: Introducción a TFTP de Azure RTOS NetX Duo 

El protocolo trivial de transferencia de archivos trivial (TFTP) es un protocolo ligero diseñado para las transferencias de archivos. A diferencia de otros protocolos más sólidos, TFTP no realiza una comprobación exhaustiva de errores y puede ofrecer un rendimiento limitado, ya que es un protocolo de detención y espera. Después de enviar un paquete de datos TFTP, el remitente espera a que el destinatario devuelva una confirmación. Aunque es sencillo, limita el rendimiento general de TFTP. El paquete TFTP permite que los hosts usen este protocolo a través de las redes IP.

## <a name="tftp-requirements"></a>Requisitos de TFTP

Para que funcione correctamente, la parte de cliente TFTP del paquete TFTP de NetX Duo requiere que ya se haya creado una instancia de IP. Además, UDP debe estar habilitado en la misma instancia de IP. La parte del cliente del paquete TFTP de NetX Duo no tiene ningún otro requisito.

La parte del servidor TFTP del paquete TFTP de NetX Duo tiene varios requisitos adicionales. En primer lugar, se necesita acceso completo al *puerto 69 conocido* de UDP para controlar todas las solicitudes TFTP del cliente. El servidor TFTP también está diseñado para su uso con el sistema de archivos incrustados FileX. Si FileX no está disponible, el usuario puede distribuir las partes de FileX usadas a su propio entorno. Esto se describe en secciones posteriores de esta guía.

## <a name="tftp-file-names"></a>Nombres de archivos TFTP 

Los nombres de archivos TFTP deben tener el formato del sistema de archivos de destino. Deben ser cadenas ASCII terminadas en NULL, con información de ruta de acceso completa si es necesario. No hay ningún límite especificado para el tamaño de los nombres de archivos TFTP en la implementación de TFTP de NetX Duo.

## <a name="tftp-messages"></a>Mensajes TFTP

El protocolo TFTP sigue un mecanismo muy sencillo para abrir, leer, escribir y cerrar archivos. Básicamente, hay de 2 a 4 bytes de encabezado TFTP bajo el encabezado UDP. La definición de los mensajes para abrir archivos TFTP tiene el siguiente formato:

**oooof…f0OCTET0**

Donde:

- **oooo**: campo de código de operación de 2 bytes  
0x0001 -> Apertura para lectura  
0x0002 -> Apertura para escritura

- **f…f**: campo de nombre de archivo de n bytes

- 0: carácter de terminación NULL de 1 byte

- **OCTET**: "octeto" ASCII para especificar la transferencia binaria

- 0: carácter de terminación NULL de 1 byte

La definición de los mensajes de escritura, confirmación y error de TFTP es ligeramente diferente y se define de la siguiente manera:

**oooobbbbd…d**

Donde:

- **oooo**: campo de código de operación de 2 bytes  
0x0003 -> Paquete de datos  
0x0004 -> Confirmación de última lectura  
0x0005 -> Condición de error  

- **bbbb**: campo de número de bloque de 2 bytes (1-n)

- **d…d**: campo de datos de n bytes


- 0x0001 (lectura): nombre de archivo 0 octeto 0

- 0x0002 (escritura): nombre de archivo 0 octeto 0

## <a name="tftp-communication"></a>Comunicación TFTP

Los servidores TFTP usan el puerto UDP 69 conocido para escuchar las solicitudes de cliente. Los sockets del cliente TFTP se pueden enlazar a cualquier puerto UDP disponible. La carga del paquete de datos que contiene el archivo que se va a cargar o descargar se envía en fragmentos de 512 bytes, hasta el último paquete que contiene menos de 512 bytes. Por lo tanto, un paquete que contenga menos de 512 bytes señala el final del archivo. La secuencia general de eventos es la siguiente:

Solicitudes TFTP de lectura de archivos:

1.  El cliente emite una solicitud de apertura para lectura con el nombre de archivo y espera una respuesta del servidor.

2.  El servidor envía los primeros 512 bytes del archivo, o menos si el tamaño del archivo es inferior a 512 bytes.

3.  El cliente recibe los datos, envía una confirmación y espera el siguiente paquete del servidor en el caso de los archivos que contienen más de 512 bytes.

4.  La secuencia finaliza cuando el cliente recibe un paquete que contiene menos de 512 bytes.

Solicitudes TFTP de escritura:

1.  El cliente emite una solicitud de apertura para escritura con el nombre de archivo y espera una confirmación con un número de bloque 0 del servidor.

2.  Cuando el servidor está listo para escribir el archivo, envía una confirmación con un número de bloque cero.

3.  El cliente envía los primeros 512 bytes del archivo (o menos en el caso de los archivos con un tamaño inferior a 512 bytes) al servidor y espera una confirmación.

4.  El servidor envía una confirmación después de escribir los bytes.

5.  La secuencia finaliza cuando el cliente completa la escritura de un paquete que contiene menos de 512 bytes.
 

## <a name="tftp-server-session-timer"></a>Temporizador de sesiones del servidor TFTP

El servidor TFTP tiene un número limitado de espacios para las solicitudes de cliente. Si se anula una sesión de cliente, ese espacio no se podrá reutilizar. Sin embargo, si se habilita la opción NX_TFTP_SERVER_RETRANSMIT_ENABLE, el servidor TFTP de NetX Duo crea un temporizador de sesión que supervisa el tiempo de espera de cada una de sus sesiones de cliente. Cuando expira el tiempo de espera de una sesión, se termina y se cierran los archivos abiertos. De este modo, el espacio pasa a estar disponible para otra solicitud del cliente TFTP.

Para establecer el tiempo de espera, ajuste la opción de configuración NX_TFTP_SERVER_RETRANSMIT_TIMEOUT que, de forma predeterminada, se establece en 200 tics del temporizador. El intervalo con el que se comprueban los tiempos de espera de la sesión se establece mediante la opción NX_TFTP_SERVER_TIMEOUT_PERIOD; su valor predeterminado es de 20 tics del temporizador.

Cuando el cliente TFTP ha cargado (escrito) archivos en el soporte FileX de TFTP, es necesario vaciar el soporte para que los datos se puedan escribir desde el disco RAM del servidor TFTP en el soporte subyacente (memoria del disco del cliente TFTP). Esto puede hacerse mediante el servicio fx_media_flush si la aplicación no desea cerrar el servidor TFTP.

Sin embargo, después de cerrar el servidor TFTP, la aplicación debe cerrar el soporte FileX con el servicio fx_media_close si ya no va a usarlo. Esto hará que los datos de los archivos se vacíen en el disco del cliente TFTP, se cierren los archivos abiertos y se actualice la información del directorio en el soporte.

Se puede ver una demostración en la sección "Sistema de ejemplo pequeño" de esta guía.

Una tercera opción para actualizar el soporte FileX es compilar la biblioteca de FileX con las opciones FX_FAULT_TOLERANT o FX_FAULT_TOLERANT_DATA en lugar de usar los servicios de FileX explícitamente. En este caso, FileX pasa automáticamente las solicitudes de escritura al controlador del soporte. Estas opciones pueden limitar el rendimiento pero ofrecen una mayor protección ante la pérdida de datos de archivo o de clústeres. Para obtener más información sobre esta cuestión y sobre FileX en general, consulte el manual del usuario de FileX de Express Logic.

## <a name="tftp-multi-thread-support"></a>Compatibilidad con varios subprocesos TFTP

Se puede llamar a los servicios del cliente TFTP de NetX Duo desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia del cliente TFTP deben realizarse consecutivamente desde el mismo subproceso.

## <a name="tftp-rfcs"></a>Publicaciones RFC para TFTP

TFTP de NetX Duo es compatible con la RFC1350 y las RFC relacionadas.

