---
title: 'Capítulo 1: Introducción a Azure RTOS NetX FTP'
description: El protocolo de transferencia de archivos (FTP) es un protocolo diseñado para las transferencias de archivos. FTP emplea servicios de protocolo de control de transmisión (TCP) de confianza para realizar su función de transferencia de archivos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86e132daf96f9039631234f10c8e239b61ad5126
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815209"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Capítulo 1: Introducción a Azure RTOS NetX FTP

El protocolo de transferencia de archivos (FTP) es un protocolo diseñado para las transferencias de archivos. FTP emplea servicios de protocolo de control de transmisión (TCP) de confianza para realizar su función de transferencia de archivos. Por este motivo, FTP es un protocolo de transferencia de archivos altamente fiable. FTP también es de alto rendimiento. La transferencia de archivos FTP real se realiza en una conexión FTP dedicada.

## <a name="ftp-requirements"></a>Requisitos de FTP

Para que funcione correctamente, el paquete Azure RTOS NetX FTP requiere que ya se haya creado una instancia de IP NetX. Además, TCP debe estar habilitado en la misma instancia de IP. La parte del cliente FTP del paquete NetX FTP no tiene ningún requisito adicional.

La parte del servidor FTP del paquete NetX FTP tiene varios requisitos adicionales. En primer lugar, es necesario tener acceso completo al *conocido puerto 21* de TCP para controlar todas las solicitudes de comandos FTP del cliente y al *conocido puerto 20* para controlar todas las transferencias de datos FTP del cliente. El servidor FTP también está diseñado para su uso con el sistema de archivos incrustados FileX. Si FileX no está disponible, el usuario puede migrar las partes de FileX usadas a su propio entorno. Esto se describe en secciones posteriores de esta guía.

## <a name="ftp-constraints"></a>Restricciones de FTP

El estándar FTP tiene muchas opciones relacionadas con la representación de datos de archivos. De forma similar a las implementaciones de UNIX, FTP de NetX supone las siguientes restricciones de formato de archivo:

- Tipo de archivo: **binario**
- Formato de archivo: **solo para no impresión**
- Estructura de archivo: **solo estructura de archivos**
- Modo de transmisión: **solo en modo de secuencia**

## <a name="ftp-file-names"></a>Nombre de archivos FTP

Los nombres de archivo FTP deben tener el formato del sistema de archivos de destino (normalmente, FileX). Deben ser cadenas ASCII terminadas en NULL, con información de ruta de acceso completa si es necesario. No hay ningún límite especificado para el tamaño de los nombres de archivo FTP en la implementación FTP de NetX. Sin embargo, el tamaño de carga del grupo de paquetes debe ser capaz de dar cabida a la ruta de acceso máxima y/o al nombre de archivo.

## <a name="ftp-client-commands"></a>Comandos de cliente FTP

El FTP tiene un mecanismo sencillo para abrir conexiones y realizar operaciones de archivos y directorios. Básicamente, hay un conjunto de comandos FTP estándar que emite el cliente después de que una conexión se haya establecido correctamente en el *conocido puerto 21* de TCP. A continuación se muestran algunos de los comandos FTP básicos:

### <a name="ftp-command-and-meaning"></a>Comandos FTP y significado

- **CWD ruta**: *cambiar el directorio de trabajo*.
- **DELE nombre de archivo**: *eliminar el nombre de archivo especificado*.
- **LIST directorio**: *obtener lista de directorios*.
- **MKD directorio**: *crear nuevo directorio*.
- **NLIST directorio**: *obtener lista de directorios*.
- **NOOP**: *ninguna operación, vuelve correctamente*.
- **PASS contraseña**: *proporcionar la contraseña para el inicio de sesión*.
- **PASV**: *solicitar modo de transferencia pasiva*.
- **PWD ruta**: *seleccionar la ruta de acceso del directorio actual*.
- **QUIT**: *finalizar la conexión de cliente*.
- **RETR nombre de archivo**: *leer archivo especificado*.
- **RMD directorio**: *eliminar el directorio especificado*.
- **RNFR nombre de archivo antiguo**: *especificar el archivo que se va a cambiar de nombre*.
- **RNTO nombre de archivo nuevo**: *cambiar el nombre del archivo por el nombre de archivo proporcionado*.
- **STOR nombre de archivo**: *escribir archivo especificado*.
- **TYPE I**: *seleccionar imagen de archivo binario*.
- **USER nombre de usuario**: *proporcionar el nombre de usuario para el inicio de sesión*.
- **PORT ip_address,port**: *proporcionar la dirección IP y el puerto de datos de cliente*.

El software cliente FTP de NetX usa internamente estos comandos ASCII para realizar operaciones FTP con el servidor FTP.

## <a name="ftp-server-responses"></a>Respuestas del servidor FTP

El servidor FTP emplea el *conocido puerto TCP 21* para el campo solicitudes de comando de cliente. Una vez que el servidor FTP procesa el comando de cliente, devuelve una respuesta numérica de 3 dígitos en ASCII seguida de una cadena ASCII opcional. El software cliente FTP usa la respuesta numérica para determinar si la operación se ha realizado correctamente o no. A continuación, se enumeran varias respuestas del servidor FTP a comandos de cliente:

### <a name="first-numeric-field-and-meaning"></a>Primer campo numérico y significado

- **1xx**: *Estado preliminar positivo: otra respuesta entrante*.
- **2xx**: *Estado de finalización positivo*.
- **3xx**: *Estado preliminar positivo: se debe enviar otro comando*.
- **4xx**: *Condición de error temporal*.
- **5xx:** *Condición de error*.

### <a name="second-numeric-field-and-meaning"></a>Segundo campo numérico y significado

- **x0x**: Error de sintaxis en el comando.
- **x1x**: Mensaje informativo.
- **x2x**: Conexión relacionada.
- **x3x**: Autenticación relacionada.
- **x4x**: Sin especificar.
- **x5x**: Sistema de archivos relacionado.

Por ejemplo, una solicitud de cliente para desconectar una conexión FTP con el comando QUIT normalmente responderá con un código "221" del servidor si la desconexión se realiza correctamente.

## <a name="ftp-passive-transfer-mode"></a>Modo de transferencia pasiva de FTP

De forma predeterminada, el cliente FTP de NetX usa el modo de transporte activo para intercambiar datos a través del socket de datos con el servidor FTP. El problema de esta disposición es que requiere que el cliente FTP abra un socket de servidor TCP para que el servidor FTP se conecte. Esto representa un posible riesgo de seguridad y puede ser bloqueado por el firewall del cliente. El modo de transferencia pasiva difiere del modo de transporte activa al hacer que el servidor FTP cree el socket del servidor TCP en la conexión de datos. Esto elimina el riesgo de seguridad para el cliente FTP.

Para habilitar la transferencia de datos pasiva, la aplicación llama a *nx_ftp_client_passive_mode_set* en un cliente FTP creado previamente con el segundo argumento establecido en NX_TRUE. A partir de ese momento, todos los servicios de cliente FTP de NetX posteriores para la transferencia de datos (NLST, RETR, STOR) se intentan en el modo de transporte pasivo.

El cliente FTP envía primero el comando PASV sin argumentos. Si el servidor FTP admite esta solicitud, devolverá la respuesta 227 "OK". A continuación, el cliente envía la solicitud; por ejemplo, RETR. Si el servidor rechaza el modo de transferencia pasiva, el servicio de cliente FTP de NetX devuelve un estado de error.

Para deshabilitar el modo de transporte pasivo y volver al modo de transporte activo, la aplicación llama a *nx_ftp_client_passive_mode_set* con el segundo argumento establecido en NX_FALSE.

## <a name="ftp-communication"></a>Comunicación FTP

El servidor FTP emplea el *conocido puerto TCP 21* para el campo solicitudes de cliente. Los clientes FTP pueden utilizar cualquier puerto TCP disponible. La secuencia general de eventos FTP es la siguiente:

### <a name="ftp-read-file-requests"></a>Solicitudes FTP de lectura de archivos

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta "220" a la señal correcta.
1. El cliente envía el mensaje "USER" con el "nombre de usuario".
1. El servidor envía la respuesta "331" a la señal correcta.
1. El cliente envía el mensaje "PASS" con la "contraseña".
1. El servidor envía la respuesta "230" a la señal correcta.
1. El cliente envía el mensaje "TYPE I" para la transferencia binaria.
1. El servidor envía la respuesta "200" a la señal correcta.
1. El cliente envía el mensaje "PORT" con la dirección IP y el puerto.
1. El servidor envía la respuesta "200" a la señal correcta.
1. El cliente envía el mensaje "RETR" con el nombre de archivo que se va a leer.
1. El servidor crea el socket de datos y se conecta con el puerto de datos de cliente especificado en el comando "PORT".
1. El servidor envía la respuesta "125" para indicar que se ha comenzado a leer el archivo.
1. El servidor envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termine, el servidor desconecta la conexión de datos.
1. El servidor envía la respuesta "250" para indicar que se ha leído el archivo con éxito.
1. Los clientes envían "QUIT" para finalizar la conexión FTP.
1. El servidor envía la respuesta "221" para indicar que se ha desconectado con éxito.
1. El servidor desconecta la conexión FTP.

Como se mencionó anteriormente, la única diferencia entre el FTP que se ejecuta a través de IPv4 e IPv6 es el comando de puerto que se sustituye por el comando EPRT para IPv6

Si el cliente FTP realiza una solicitud de lectura en el modo de transferencia pasiva, la secuencia de comandos es la siguiente (las líneas en **negrita** indican un paso diferente del modo de transferencia activa):

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta "220" a la señal correcta.
1. El cliente envía el mensaje "USER" con el "nombre de usuario".
1. El servidor envía la respuesta "331" a la señal correcta.
1. El cliente envía el mensaje "PASS" con la "contraseña".
1. El servidor envía la respuesta "230" a la señal correcta.
1. El cliente envía el mensaje "TYPE I" para la transferencia binaria.
1. El servidor envía la respuesta "200" a la señal correcta.
1. **El cliente envía el mensaje "PASV".**
1. **El servidor envía la respuesta "227", la dirección IP y el puerto para el cliente al que se va a conectar, para indicar el éxito.**
1. El cliente envía el mensaje "RETR" con el nombre de archivo que se va a leer.
1. **El servidor crea un socket de servidor de datos y realiza escuchas para la solicitud de conexión de cliente en este socket utilizando el puerto especificado en la respuesta "227".**
1. **El servidor envía la respuesta "150" en el socket de control para indicar que la lectura en el archivo se ha iniciado.**
1. El servidor envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termine, el servidor desconecta la conexión de datos.
1. **El servidor envía la respuesta "226" en el socket de control para indicar que la lectura en el archivo se ha completado**.
1. El cliente envía "QUIT" para finalizar la conexión FTP.
1. El servidor envía la respuesta "221" para indicar que se ha desconectado con éxito.
1. El servidor desconecta la conexión FTP.

### <a name="ftp-write-requests"></a>Solicitudes de escritura FTP

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta "220" a la señal correcta.
1. El cliente envía el mensaje "USER" con el "nombre de usuario".
1. El servidor envía la respuesta "331" a la señal correcta.
1. El cliente envía el mensaje "PASS" con la "contraseña".
1. El servidor envía la respuesta "230" a la señal correcta.
1. El cliente envía el mensaje "TYPE I" para la transferencia binaria.
1. El servidor envía la respuesta "200" a la señal correcta.
1. El cliente envía el mensaje "PORT" con la dirección IP y el puerto.
1. El servidor envía la respuesta "200" a la señal correcta.
1. El cliente envía el mensaje "STOR" con el nombre de archivo que se va a escribir.
1. El servidor crea el socket de datos y se conecta con el puerto de datos de cliente especificado en el comando "PORT".
1. El servidor envía la respuesta "125" para indicar que se ha comenzado a escribir el archivo.
1. El cliente envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termine, el cliente desconecta la conexión de datos.
1. El servidor envía la respuesta "250" para indicar que se ha escrito el archivo con éxito.
1. Los clientes envían "QUIT" para finalizar la conexión FTP.
1. El servidor envía la respuesta "221" para indicar que se ha desconectado con éxito.
1. El servidor desconecta la conexión FTP.

Si el cliente FTP realiza una solicitud de escritura en el modo de transferencia pasiva, la secuencia de comandos es la siguiente (las líneas en **negrita** indican un paso diferente del modo de transferencia activa):

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta "220" a la señal correcta.
1. El cliente envía el mensaje "USER" con el "nombre de usuario".
1. El servidor envía la respuesta "331" a la señal correcta.
1. El cliente envía el mensaje "PASS" con la "contraseña".
1. El servidor envía la respuesta "230" a la señal correcta.
1. El cliente envía el mensaje "TYPE I" para la transferencia binaria.
1. El servidor envía la respuesta "200" a la señal correcta.
1. **El cliente envía el mensaje "PASV".**
1. **El servidor envía la respuesta "227", la dirección IP y el puerto para el cliente al que se va a conectar, para indicar el éxito.**
1. El cliente envía el mensaje "STOR" con el nombre de archivo que se va a escribir.
1. **El servidor crea un socket de servidor de datos y realiza escuchas para la solicitud de conexión de cliente en este socket utilizando el puerto especificado en la respuesta "227".**
1. **El servidor envía la respuesta "150" en el socket de control para indicar que la escritura en el archivo se ha iniciado.**
1. El cliente envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termine, el cliente desconecta la conexión de datos.
1. **El servidor envía la respuesta "226" en el socket de control para indicar que la escritura en el archivo se ha completado**.
1. El cliente envía "QUIT" para finalizar la conexión FTP.
1. El servidor envía la respuesta "221" para indicar que se ha desconectado con éxito.
1. El servidor desconecta la conexión FTP.

## <a name="ftp-authentication"></a>FTP Authentication

Cada vez que se realiza una conexión FTP, el cliente debe proporcionar al servidor un *nombre de usuario* y una *contraseña*. Algunos sitios FTP permiten lo que se denomina *FTP anónimo*, que permite el acceso FTP sin un nombre de usuario y una contraseña específicos. Para este tipo de conexión, se debe proporcionar "Anonymous" para el nombre de usuario y la contraseña debe ser una dirección de correo electrónico completa.

El usuario es responsable de proporcionar las rutinas de autenticación de FTP de NetX con inicio de sesión y cierre de sesión. Se proporcionan durante la función **nx_ftp_server_create** y se les llama desde el procesamiento de contraseñas. Si la función _login * devuelve NX_SUCCESS, la conexión se autentica y se permiten las operaciones FTP. De lo contrario, si la función de *Inicio de sesión* devuelve un valor distinto de NX_SUCCESS, se rechazará el intento de conexión.

## <a name="ftp-multi-thread-support"></a>Compatibilidad con varios subprocesos FTP

Se puede llamar a los servicios de cliente FTP de NetX desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia de cliente FTP deben realizarse en secuencia desde el mismo subproceso.

## <a name="ftp-rfcs"></a>RFC de FTP

FTP de NetX es compatible con RFC959 y RFC relacionados.