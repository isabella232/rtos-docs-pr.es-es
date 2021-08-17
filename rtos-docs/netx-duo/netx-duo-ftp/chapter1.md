---
title: 'Capítulo 1: Introducción al FTP de Azure RTOS NetX Duo'
description: El protocolo de transferencia de archivos (FTP) es un protocolo diseñado para las transferencias de archivos.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a36357ce486d5ba8a68b23c829de6c4b821dfb3cc62f47b0958ff32deaa2f7a7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791302"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ftp"></a>Capítulo 1: Introducción al FTP de Azure RTOS NetX Duo

El protocolo de transferencia de archivos (FTP) es un protocolo diseñado para las transferencias de archivos. FTP emplea servicios del Protocolo de control de transmisión (TCP) de confianza para realizar su función de transferencia de archivos. Por este motivo, FTP es un protocolo de transferencia de archivos altamente fiable. FTP también es de alto rendimiento. La transferencia de archivos FTP real se realiza en una conexión FTP dedicada. El protocolo FTP de NetX Duo admite redes IPv4 e IPv6. IPv6 no cambia directamente el protocolo FTP, aunque es necesario realizar algunos cambios en la API de FTP de NetX original para adaptarse a IPv6 y se describirán en este documento.

## <a name="ftp-requirements"></a>Requisitos de FTP

Para que funcione correctamente, el paquete FTP de NetX requiere NetX Duo. La aplicación host debe crear una instancia de IP para ejecutar las tareas periódicas y los servicios de NetX. Si ejecuta la aplicación de host FTP en una red IPv6, IPv6 e ICMPv6 deben estar habilitados en la tarea IP. TCP también debe estar habilitado para redes IPv6 o IPv4. La aplicación host IPv6 debe establecer su dirección IPv6 local y global de vínculo mediante la API IPv6 o DHCPv6. Mediante un programa de demostración de la sección “Sistema de ejemplo pequeño” del **capítulo 2** se mostrará cómo se hace esto.

El servidor y el cliente FTP también están diseñados para funcionar con el sistema de archivos incrustado FileX. Si FileX no está disponible, el desarrollador del host puede implementar o sustituir su propio sistema de archivos a lo largo de las instrucciones que se sugieren en filex_stub.h definiendo cada uno de los servicios enumerados en ese archivo. Esto se describe en secciones posteriores de esta guía.

La parte del cliente FTP del paquete FTP de NetX no tiene ningún requisito adicional.

La parte del servidor FTP del paquete FTP de NetX tiene varios requisitos adicionales. En primer lugar, es necesario tener acceso completo al *conocido puerto 21* de TCP para controlar todas las solicitudes de comandos del FTP cliente y al *conocido puerto 20* para controlar todas las transferencias de datos del FTP cliente.

## <a name="ftp-constraints"></a>Restricciones de FTP

El estándar FTP tiene muchas opciones relacionadas con la representación de datos de archivos. FTP de NetX no implementa opciones de conmutador, por ejemplo, ls –al. El servidor FTP de NetX espera recibir solicitudes y sus argumentos en un solo paquete y no en paquetes consecutivos.

De forma similar a las implementaciones de UNIX, FTP de NetX supone las siguientes restricciones de formato de archivo:

- Tipo de archivo: **binario**
- Formato de archivo: **solo para no impresión**
- Estructura de archivo: **solo estructura de archivos**

## <a name="ftp-file-names"></a>Nombre de archivos FTP

Los nombres de archivo FTP deben tener el formato del sistema de archivos de destino (normalmente, FileX). Deben ser cadenas ASCII terminadas en NULL, con información de la ruta de acceso completa si es necesario. No hay ningún límite especificado para el tamaño de los nombres de archivo FTP en la implementación FTP de NetX. Sin embargo, el tamaño de carga del grupo de paquetes debe ser capaz de dar cabida a la ruta de acceso máxima o al nombre de archivo.

## <a name="ftp-client-commands"></a>Comandos de cliente FTP

FTP tiene un mecanismo sencillo para abrir conexiones y realizar operaciones de archivos y directorios. Básicamente, hay un conjunto de comandos FTP estándar que el cliente emite después de que una conexión se haya establecido correctamente en el *conocido puerto 21* de TCP. A continuación se muestran algunos de los comandos FTP básicos. Tenga en cuenta que la única diferencia cuando FTP se ejecuta a través de IPv6 es que el comando PORT se reemplaza por el comando EPRT:

- CWD ruta_de_acceso *Cambiar el directorio de trabajo*
- DELE nombre_de_archivo *Eliminar el nombre de archivo*
- EPRT dirección_ip, puerto *Proporcionar la dirección IPv6 y el puerto de datos de cliente*
- EPSV *Solicitar modo de transferencia pasiva IPv6*
- LIST directorio *Obtener lista de directorios*
- MKD directorio *Crear nuevo directorio*
- NLST directorio *Obtener lista de directorios*
- NOOP *Ninguna operación, vuelve correctamente*
- PASS contraseña *Proporcionar la contraseña para el inicio de sesión*
- PASV *Solicitar modo de transferencia pasiva IPv4*
- PORT dirección_ip,puerto *Proporcionar la dirección IP y el puerto de datos de cliente*
- PWD ruta_de_acceso *seleccionar la ruta de acceso del directorio actual*.
- QUIT *Finalizar la conexión de cliente*
- RETR nombre_de_archivo *Leer el archivo especificado*
- RMD directorio *Eliminar el directorio especificado*
- RNFR nombre_de_archivo_antiguo *Especificar el archivo que se va a cambiar de nombre*
- RNTO nombre_de_archivo_nuevo *Cambiar el nombre del archivo por el nombre de archivo proporcionado*
- STOR nombre_de_archivo *Escribir archivo especificado*
- TYPE I *Seleccionar imagen de archivo binario*
- USER nombre_de_usuario *Proporcionar el nombre de usuario para el inicio de sesión*

El software del cliente FTP de NetX usa internamente estos comandos ASCII para realizar operaciones FTP con el servidor FTP.

## <a name="ftp-server-responses"></a>Respuestas del servidor FTP

Una vez que el servidor FTP procesa la solicitud del cliente, devuelve una respuesta codificada de tres dígitos en ASCII seguida del texto ASCII opcional. El software del cliente FTP usa la respuesta numérica para determinar si la operación se ha realizado correctamente o no. A continuación, se muestran varias respuestas del servidor FTP a solicitudes de cliente:

**Significado del primer campo numérico**

- 1xx *Estado preliminar positivo: otra respuesta entrante*.
- 2xx *Estado de finalización positivo*.
- 3xx *Estado preliminar positivo: se debe enviar otro comando*.
- 4xx *Condición de error temporal*.
- 5xx *Condición de error*.

**Significado del segundo campo numérico**

- x0x *Error de sintaxis en el comando*.
- x1x *Mensaje informativo*.
- x2x *Conexión relacionada*.
- x3x *Autenticación relacionada*.
- x4x *Sin especificar*.
- x5x *Sistema de archivos relacionado*.

Por ejemplo, una solicitud de cliente para desconectar una conexión FTP con el comando QUIT normalmente responderá con un código “221” del servidor si la desconexión se realiza correctamente.

## <a name="ftp-passive-transfer-mode"></a>Modo de transferencia pasiva de FTP

De forma predeterminada, el cliente FTP de NetX Duo usa el modo de transporte activo para intercambiar datos a través del socket de datos con el servidor FTP. El problema de esta disposición es que requiere que el cliente FTP abra un socket de servidor TCP para que el servidor FTP se conecte. Esto representa un posible riesgo de seguridad y puede ser bloqueado por el firewall del cliente. El modo de transferencia pasiva difiere del modo de transporte activa al hacer que el servidor FTP cree el socket del servidor TCP en la conexión de datos. Esto elimina el riesgo de seguridad para el cliente FTP.

Para habilitar la transferencia de datos pasiva, la aplicación llama a *nx_ftp_client_passive_mode_set* en un cliente FTP creado previamente con el segundo argumento establecido en NX_TRUE. A partir de ese momento, todos los servicios de cliente FTP de NetX Duo posteriores para la transferencia de datos (NLST, RETR, STOR) se intentan en el modo de transporte pasivo.

El cliente FTP envía primero el comando pasivo (sin argumentos), el comando PASV para IPv4 o el comando EPSV para IPv6. Si el servidor FTP admite esta solicitud, devolverá la respuesta 227 “OK” para PASV y la respuesta 229 “OK” para EPSV. A continuación, el cliente envía la solicitud, por ejemplo, RETR. Si el servidor rechaza el modo de transferencia pasiva, el servicio de cliente FTP de NetX Duo devuelve un estado de error.

Para deshabilitar el modo de transporte pasivo y volver al modo de transporte activo, la aplicación llama a *nx_ftp_client_passive_mode_set* con el segundo argumento establecido en NX_FALSE.

## <a name="ftp-communication"></a>Comunicación FTP

El servidor FTP emplea el *conocido puerto TCP 21* para atender las solicitudes del cliente. Los clientes FTP pueden utilizar cualquier puerto TCP disponible. La secuencia general de eventos FTP es la siguiente:

**Solicitudes FTP de lectura de archivos**:

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta “220” para indicar que la operación es correcta.
1. El cliente envía el mensaje “USER” con el “nombre de usuario”.
1. El servidor envía la respuesta “331” para indicar que la operación es correcta.
1. El cliente envía el mensaje “PASS” con la “contraseña”.
1. El servidor envía la respuesta “230” para indicar que la operación es correcta.
1. El cliente envía el mensaje “TYPE I” para la transferencia binaria.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. *Aplicaciones IPv4*: el cliente envía el mensaje “PORT” con la dirección IP y el puerto.<br />*Aplicaciones IPv6*: el cliente envía el mensaje “EPRT” con la dirección IP y el puerto.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. El cliente envía el mensaje “RETR” con el nombre de archivo que se va a leer.
1. El servidor crea el socket de datos y se conecta con el puerto de datos de cliente especificado en el comando “PORT”.
1. El servidor envía la respuesta “125” para indicar que se ha comenzado a leer el archivo.
1. El servidor envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termina, el servidor desconecta la conexión de datos.
1. El servidor envía la respuesta “250” para indicar que el archivo se ha leído correctamente.
1. El cliente envía “QUIT” para finalizar la conexión FTP.
1. El servidor envía la respuesta “221” para indicar que la desconexión se ha realizado correctamente.
1. El servidor desconecta la conexión FTP.

Como se mencionó anteriormente, la única diferencia entre el FTP que se ejecuta a través de IPv4 e

IPv6 es el comando PORT que se sustituye por el comando EPRT para IPv6.

Si el cliente FTP realiza una solicitud de lectura en el modo de transferencia pasiva, la secuencia de comandos es la siguiente (las líneas en **negrita** indican un paso diferente del modo de transferencia activa):

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta “220” para indicar que la operación es correcta.
1. El cliente envía el mensaje “USER” con el “nombre de usuario”.
1. El servidor envía la respuesta “331” para indicar que la operación es correcta.
1. El cliente envía el mensaje “PASS” con la “contraseña”.
1. El servidor envía la respuesta “230” para indicar que la operación es correcta.
1. El cliente envía el mensaje “TYPE I” para la transferencia binaria.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. ***Aplicaciones IPv4:* el cliente envía el mensaje “PASV”.**<br />**_Aplicaciones IPv6:_ el cliente envía el mensaje “EPSV”.**
1. ***Aplicaciones IPv4:* el servidor envía la respuesta “227”, la dirección IP y el puerto para el cliente al que se va a conectar para indicar que la operación es correcta.**<br />**_Aplicaciones IPv6:_ el servidor envía la respuesta “229”, la dirección IP y el puerto para el cliente al que se va a conectar para indicar que la operación es correcta.**
1. El cliente envía el mensaje “RETR” con el nombre de archivo que se va a leer.
1. **El servidor crea un socket de servidor de datos y realiza escuchas para la solicitud de conexión de cliente en este socket utilizando el puerto especificado en la respuesta en el paso 10.**
1. **El servidor envía la respuesta “150” en el socket de control para indicar que la lectura en el archivo se ha iniciado.**
1. El servidor envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termina, el servidor desconecta la conexión de datos.
1. **El servidor envía la respuesta “226” en el socket de control para indicar que la lectura del archivo se ha completado**.
1. El cliente envía “QUIT” para finalizar la conexión FTP.
1. El servidor envía la respuesta “221” para indicar que la desconexión se ha realizado correctamente.
1. El servidor desconecta la conexión FTP.

**Solicitudes de escritura FTP**:

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta “220” para indicar que la operación es correcta.
1. El cliente envía el mensaje “USER” con el “nombre de usuario”.
1. El servidor envía la respuesta “331” para indicar que la operación es correcta.
1. El cliente envía el mensaje “PASS” con la “contraseña”.
1. El servidor envía la respuesta “230” para indicar que la operación es correcta.
1. El cliente envía el mensaje “TYPE I” para la transferencia binaria.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. *Aplicaciones IPv4*: el cliente envía el mensaje “PORT” con la dirección IP y el puerto.<br />*Aplicaciones IPv6*: el cliente envía el mensaje “EPRT” con la dirección IP y el puerto.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. El cliente envía el mensaje “STOR” con el nombre de archivo que se va a escribir.
1. El servidor crea el socket de datos y se conecta con el puerto de datos de cliente especificado en el comando “EPRT” o “PORT” anterior.
1. El servidor envía la respuesta “125” para indicar que se ha comenzado a escribir el archivo.
1. El cliente envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termina, el cliente desconecta la conexión de datos.
1. El servidor envía la respuesta “250” para indicar que se la escritura del archivo es correcta.
1. El cliente envía “QUIT” para finalizar la conexión FTP.
1. El servidor envía la respuesta “221” para indicar que la desconexión se ha realizado correctamente.
1. El servidor desconecta la conexión FTP.

Si el cliente FTP realiza una solicitud de escritura en el modo de transferencia pasiva, la secuencia de comandos es la siguiente (las líneas en **negrita** indican un paso diferente del modo de transferencia activa):

1. El cliente emite una conexión TCP al puerto 21 del servidor.
1. El servidor envía la respuesta “220” para indicar que la operación es correcta.
1. El cliente envía el mensaje “USER” con el “nombre de usuario”.
1. El servidor envía la respuesta “331” para indicar que la operación es correcta.
1. El cliente envía el mensaje “PASS” con la “contraseña”.
1. El servidor envía la respuesta “230” para indicar que la operación es correcta.
1. El cliente envía el mensaje “TYPE I” para la transferencia binaria.
1. El servidor envía la respuesta “200” para indicar que la operación es correcta.
1. ***Aplicaciones IPv4:* el cliente envía el mensaje “PASV”.**<br />**_Aplicaciones IPv6:_ el cliente envía el mensaje “EPSV”.**
1. ***Aplicaciones IPv4:* el servidor envía la respuesta “227”, la dirección IP y el puerto para el cliente al que se va a conectar para indicar que la operación es correcta.**<br />**_Aplicaciones IPv6:_ el servidor envía la respuesta “229”, la dirección IP y el puerto para el cliente al que se va a conectar para indicar que la operación es correcta.**
1. El cliente envía el mensaje “STOR” con el nombre de archivo que se va a escribir.
1. **El servidor crea un socket de servidor de datos y realiza escuchas para la solicitud de conexión de cliente en este socket utilizando el puerto especificado en la respuesta en el paso 10.**
1. **El servidor envía la respuesta “150” en el socket de control para indicar que la escritura en el archivo se ha iniciado.**
1. El cliente envía el contenido del archivo a través de la conexión de datos. Este proceso continúa hasta que el archivo se haya transferido por completo.
1. Cuando termina, el cliente desconecta la conexión de datos.
1. **El servidor envía la respuesta “226” en el socket de control para indicar que la escritura del archivo se ha completado**.
1. El cliente envía “QUIT” para finalizar la conexión FTP.
1. El servidor envía la respuesta “221” para indicar que la desconexión se ha realizado correctamente.
1. El servidor desconecta la conexión FTP.

## <a name="ftp-authentication"></a>FTP Authentication

Cada vez que se realiza una conexión FTP, el cliente debe proporcionar al servidor un *nombre de usuario* y una *contraseña*. Algunos sitios FTP permiten lo que se denomina *FTP anónimo*, que permite el acceso FTP sin un nombre de usuario ni una contraseña específicos. Para este tipo de conexión, se debe proporcionar “anonymous” para el nombre de usuario y la contraseña debe ser una dirección de correo electrónico completa.

El usuario es responsable de proporcionar al FTP de NetX las rutinas de autenticación de inicio y cierre de sesión. Estas se proporcionan durante los servicios ***nxd_ftp_server_create** _ y _*_nx_ftp_server_create_*_ y se las llama desde el procesamiento de contraseñas. La diferencia entre las dos es que los punteros de la función de entrada _*_nxd_ftp_server_create_*_ a las funciones de autenticación de inicio y cierre de sesión esperan el tipo de dirección de NetX Duo _*_NXD_ADDRESS_*_. Este tipo de datos contiene los formatos de dirección IPv4 o IPv6, lo que convierte a esta función en el servicio “dúo” que admite redes IPv4 e IPv6. Los punteros de función de entrada _ *_nx_ftp_server_create_** a las funciones de autenticación de inicio y cierre de sesión esperan el tipo de dirección IP ULONG. Esta función está limitada a las redes IPv4. Se recomienda al desarrollador que use el servicio “dúo” siempre que sea posible.

Si la función *inicio de sesión* devuelve NX_SUCCESS, la conexión se autentica y se permiten las operaciones FTP. De lo contrario, si la función de *inicio de sesión* devuelve un valor distinto de NX_SUCCESS, se rechazará el intento de conexión.

## <a name="ftp-multi-thread-support"></a>Compatibilidad con varios subprocesos FTP

Se puede llamar a los servicios de cliente FTP de NetX desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia de cliente FTP deben realizarse en secuencia desde el mismo subproceso.

## <a name="ftp-rfcs"></a>Publicaciones RFC para FTP

FTP de NetX Duo es compatible con RFC 959, RFC 2428 y publicaciones RFC relacionadas.
