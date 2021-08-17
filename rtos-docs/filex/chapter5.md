---
title: 'Capítulo 5: Controladores de E/S para Azure RTOS FileX'
description: Este capítulo contiene una descripción de los controladores de E/S de Azure RTOS FileX y está diseñado para ayudar a los desarrolladores a escribir controladores específicos de la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 163893119837a46479b3f346c2bd47d200de2af75232f91a23bbc3f64e20ea50
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782921"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Capítulo 5: Controladores de E/S para Azure RTOS FileX

Este capítulo contiene una descripción de los controladores de E/S de Azure RTOS FileX y está diseñado para ayudar a los desarrolladores a escribir controladores específicos de la aplicación.

## <a name="io-driver-introduction"></a>Introducción a los controladores de E/S

FileX admite varios dispositivos multimedia. La estructura FX_MEDIA define todo lo necesario para administrar un dispositivo multimedia. Esta estructura contiene toda la información multimedia, incluido el controlador de E/S específico del elemento multimedia y los parámetros asociados para pasar información, y el estado entre el controlador y FileX. En la mayoría de los sistemas, hay un controlador de E/S único para cada instancia de elemento multimedia de FileX.

## <a name="io-driver-entry"></a>Entrada de controlador de E/S

Cada controlador de E/S de FileX tiene una sola función de entrada definida por la llamada de servicio ***fx_media_open***. La función de entrada del controlador tiene el formato siguiente:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX llama a la función de entrada del controlador de E/S para solicitar todo el acceso a los medios físicos, incluida la inicialización y la lectura del sector de arranque. Las solicitudes al controlador se realizan de forma secuencial, es decir, FileX espera a que se complete la solicitud actual antes de enviar una nueva.

## <a name="io-driver-requests"></a>Solicitudes de controlador de E/S

Dado que cada controlador de E/S tiene una sola función de entrada, FileX realiza solicitudes específicas a través del bloque de control del medio. Específicamente, el miembro **fx_media_driver_request** de **FX_MEDIA** se utiliza para especificar la solicitud de controlador exacta. El controlador de E/S comunica si la solicitud se ha realizado correctamente a través del miembro **fx_media_driver_status** de **FX_MEDIA**. Si la solicitud del controlador se ha realizado correctamente, **FX_SUCCESS** se coloca en este campo antes de que el controlador vuelva. De lo contrario, si se detecta un error, FX_IO_ERROR se coloca en este campo.

### <a name="driver-initialization"></a>Inicialización del controlador

Aunque el procesamiento real de inicialización del controlador es específico de la aplicación, normalmente se compone de la inicialización de la estructura de datos y, posiblemente, de una inicialización de hardware preliminar. Esta solicitud es la primera realizada por FileX y se realiza desde dentro del servicio fx_media_open.

Si se detecta protección contra escritura de medios, el miembro del controlador fx_media_driver_write_protect de FX_MEDIA debe establecerse en FX_TRUE.

Se usan los siguientes miembros de FX_MEDIA para la solicitud de inicialización del controlador de E/S:

|Miembro de FX_MEDIA|Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX proporciona un mecanismo para informar al controlador de la aplicación cuando los sectores ya no están en uso. Esto es especialmente útil para los administradores de memoria flash que deben administrar todos los sectores lógicos en uso asignados a la memoria flash.

Si se requiere esta notificación de sectores disponibles, el controlador de la aplicación simplemente establece en **FX_TRUE** el campo *fx_media_driver_free_sector_update* en la estructura **FX_MEDIA** asociada. Una vez establecido, FileX realiza una llamada de controlador de E/S **_FX_DRIVER_RELEASE_SECTORS_** que indica la disponibilidad de uno o más sectores consecutivos.

### <a name="boot-sector-read"></a>Lectura del sector de arranque

En lugar de usar una solicitud de lectura estándar, FileX realiza una solicitud específica para leer el sector de arranque del medio. Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de lectura del sector de arranque del controlador de E/S:

|Miembro de FX_MEDIA|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Dirección de destino del sector de arranque.|

### <a name="boot-sector-write"></a>Escritura del sector de arranque

En lugar de usar una solicitud de escritura estándar, FileX realiza una solicitud específica para escribir el sector de arranque del medio. Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de escritura del sector de arranque del controlador de E/S:

|Miembro de FX_MEDIA|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Dirección de origen del sector de arranque.|

### <a name="sector-read"></a>Lectura del sector

FileX lee uno o más sectores en la memoria emitiendo una solicitud de lectura al controlador de E/S. Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de lectura del controlador de E/S:

|Miembro de FX_MEDIA|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Sector lógico que se va a leer|
|fx_media_driver_sectors|Número de sectores que se van a leer|
|fx_media_driver_buffer|Búfer de destino para los sectores leídos|
|fx_media_driver_data_sector_read|Se establece en FX_TRUE si se solicita un sector de datos de archivo; de lo contrario, en FX_FALSE si se solicita un sector del sistema (FAT o sector de directorio).|
|fx_media_driver_sector_type|Define el tipo explícito de sector solicitado, como se indica a continuación:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Escritura de sectores

FileX escribe uno o más sectores en el medio físico emitiendo una solicitud de escritura en el controlador de E/S. Se usan los siguientes miembros de FX_MEDIA para la solicitud de escritura del controlador de E/S:

|Miembro de FX_MEDIA| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Sector lógico que se va a escribir|
|fx_media_driver_sectors|Número de sectores que se van a escribir|
|fx_media_driver_buffer|Búfer de origen de los sectores que se van a escribir|
|fx_media_driver_system_write| Se establece en FX_TRUE si se solicita un sector del sistema (FAT o sector del directorio); de lo contrario, en FX_FALSE si se solicita un sector de datos de archivo.|
|fx_media_driver_sector_type|Define el tipo explícito de sector solicitado, como se indica a continuación:<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4)|

### <a name="driver-flush"></a>Vaciado de controladores

FileX vacía todos los sectores que se encuentran actualmente en la memoria caché del sector del controlador en el medio físico emitiendo una solicitud de vaciado al controlador de E/S. Obviamente, si el controlador no almacena en caché los sectores, esta solicitud no requiere ningún procesamiento del controlador. Se usan los siguientes miembros de FX_MEDIA para la solicitud de vaciado del controlador de E/S:

|Miembro de FX_MEDIA| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Anulación del controlador

FileX informa al controlador de que debe anular toda la actividad física de E/S con el medio físico emitiendo una solicitud de anulación al controlador de E/S. El controlador no debe realizar ninguna E/S de nuevo hasta que se vuelva a inicializar. Se usan los siguientes miembros de FX_MEDIA para la solicitud de anulación del controlador de E/S:

|Miembro de FX_MEDIA| Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Disponibilidad de sectores

Si el controlador lo seleccionó anteriormente durante la inicialización, FileX informa al controlador cuando uno o más sectores consecutivos están disponibles. Si el controlador es en realidad un administrador de memoria flash, se puede usar esta información para indicarle que ya no se necesitan estos sectores. Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de disponibilidad de sectores de E/S:

|Miembro de FX_MEDIA| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Inicio del sector disponible|
|fx_media_driver_sectors|Número de sectores disponibles|

### <a name="driver-suspension"></a>Suspensión del controlador

Dado que la E/S con medios físicos puede tardar algún tiempo, suele ser recomendable suspender el subproceso de llamada. Con ello, se da por sentado que la finalización de la operación de E/S subyacente está controlada por interrupciones. Si es así, la suspensión de subprocesos se implementa fácilmente con un semáforo ThreadX. Después de iniciar la operación de entrada o de salida, el controlador de E/S se suspende en su propio semáforo de E/S interno (creado con un recuento inicial de cero durante la inicialización del controlador). Como parte del procesamiento de interrupciones de finalización de E/S del controlador, se establece el mismo semáforo de E/S, que a su vez activa el subproceso suspendido.

### <a name="sector-translation"></a>Traducción de sectores

Dado que FileX ve el medio como sectores lógicos lineales, las solicitudes de E/S realizadas al controlador de E/S se realizan con sectores lógicos. Es responsabilidad del controlador traducir entre sectores lógicos y la geometría física del medio, que puede incluir encabezados, pistas y sectores físicos. En el caso de los medios de disco RAM y Flash, los sectores lógicos suelen asignar el directorio a los sectores físicos. En cualquier caso, estas son las fórmulas típicas para realizar la asignación de sectores lógicos a físicos en el controlador de E/S:

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

Tenga en cuenta que los sectores físicos comienzan por uno, mientras que los sectores lógicos comienzan por cero.

### <a name="hidden-sectors"></a>Sectores ocultos

Los sectores ocultos residían antes del registro de arranque en el medio. Dado que realmente se encuentran fuera del ámbito del diseño del sistema de archivos FAT, se deben tener en cuenta en cada operación de sector lógico que realiza el controlador.

### <a name="media-write-protect"></a>Protección contra escritura de medios

El controlador FileX puede activar la protección contra escritura estableciendo el campo fx_media_driver_write_protect en el bloque de control multimedia. De esta manera se devolverá un error si se realizan llamadas a FileX en un intento de escribir en el medio.

## <a name="sample-ram-driver"></a>Controlador de RAM de ejemplo

El sistema de demostración de FileX se entrega con un pequeño controlador de disco RAM, que se define en el archivo fx_ram_driver.c. El controlador supone un espacio de memoria de 32 KB y crea un registro de arranque para los sectores de 256 y 128 bytes. Este archivo proporciona un buen ejemplo de cómo implementar controladores de E/S de FileX específicos de la aplicación.

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
