---
title: ¿Qué es Microsoft Azure RTOS?
description: Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos IoT y perimetrales con tecnología de microcontroladores (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: d9bd7cfda454e73e9bd270b86616780ab7ceab1a76160a66cf49a9ef82efae05
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792407"
---
# <a name="what-is-microsoft-azure-rtos"></a>¿Qué es Microsoft Azure RTOS?

Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos de Internet de las cosas (IoT) y perimetrales con tecnología de microcontroladores (MCU). Azure RTOS está diseñado para admitir la mayoría de los dispositivos altamente restringidos (con batería y con menos de 64 kB de memoria flash).

Azure RTOS está certificado previamente para una amplia variedad de estándares de seguridad. Entre ellas se incluyen las certificaciones IEC 61508 SIL 4, IEC 62304 clase C e ISO 26262 ASIL D.

Azure RTOS proporciona un entorno certificado de seguridad de criterios comunes de EAL4 +, incluida la seguridad de la capa de IP completa a través de IPsec y la seguridad de la capa de socket a través de TLS y DTLS. Nuestra biblioteca de criptografía de software ha logrado la certificación FIPS 140-2. También aprovechamos las funcionalidades criptográficas de hardware, la protección de memoria a través de módulos de ThreadX y la compatibilidad con las características de seguridad de TrustZone ARMv8-M de ARM.

## <a name="components-of-azure-rtos"></a>Componentes de Azure RTOS

La plataforma Azure RTOS es la colección de soluciones en tiempo de ejecución, entre las que se incluyen Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo y Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTO ThreadX

Azure [RTOS ThreadX](threadx/overview-threadx.md) es un sistema operativo en tiempo real (RTOS) avanzado, diseñado específicamente para aplicaciones insertadas profundamente. Entre las múltiples ventajas que ofrece Azure RTOS ThreadX se encuentran las funciones avanzadas de programación, el envío de mensajes, la administración de interrupciones y los servicios de mensajería. Azure RTOS ThreadX tiene muchas características avanzadas, entre las que se incluyen la arquitectura picokernel, la programación de umbral de prioridad, el encadenamiento de eventos y un conjunto completo de servicios del sistema.

### <a name="azure-rtos-filex"></a>Azure RTO FileX

Azure [RTOS FileX](filex/overview-filex.md) es un sistema de archivos de alto rendimiento compatible con FAT. Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles. Al igual que Azure RTOS ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de archivos. Azure RTOS FileX admite la mayoría de los soportes físicos, como el disco RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.

### <a name="azure-rtos-guix"></a>Azure RTO GUIX

Azure [RTOS GUIX](guix/overview-guix.md) es un paquete de interfaz gráfica de usuario de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados. A diferencia de las alternativas, Azure RTOS GUIX es pequeño, rápido y fácil de migrar a prácticamente cualquier configuración de hardware capaz de admitir la salida gráfica. Azure RTOS GUIX también ofrece un atractivo visual excepcional y una API intuitiva y potente para el desarrollo de interfaces de usuario a nivel de aplicación.

### <a name="azure-rtos-netx"></a>Azure RTO NetX

Azure [RTOS NetX](netx/overview-netx.md) es una implementación de alto rendimiento de estándares de protocolos TCP/IP. Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles. Azure RTOS NetX tiene una arquitectura Piconet exclusiva. Combinado con una API de copia de cero, lo convierte en un ajuste perfecto para las aplicaciones profundamente incrustadas de hoy en día que requieren conectividad de red.

### <a name="azure-rtos-netx-duo"></a>Azure RTO NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo es una pila de red TCP/IP avanzada y de nivel industrial diseñada específicamente para aplicaciones de IoT y en tiempo real insertadas profundamente. Azure RTOS NetX Duo es una pila de red IPv4 e IPv6 dual, mientras que NetX es la pila de red IPv4 original, esencialmente un subconjunto de Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTO USBX

Azure [RTOS USBX](usbx/overview-usbx.md) es un host USB de alto rendimiento, un dispositivo y una pila insertada "on-the-go" (OTG). Está totalmente integrado con ThreadX y está disponible para todos los procesadores compatibles con Azure RTOS ThreadX. Al igual que Azure RTOS ThreadX, Azure RTOS USBX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las aplicaciones profundamente insertadas, que requieren una interfaz con dispositivos USB.

### <a name="windows-tools"></a>Herramientas de Windows

Azure [RTOS GUIX Studio](guix/about-guix-studio.md) proporciona un completo entorno de diseño de aplicaciones GUI, lo que facilita la creación y el mantenimiento de todos los elementos gráficos de la GUI de la aplicación. Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino.

Azure [RTOS TraceX](tracex/overview-tracex.md) es una herramienta de análisis basada en host que proporciona a los desarrolladores una vista gráfica de los eventos del sistema en tiempo real y les permite visualizar y comprender mejor el comportamiento de sus sistemas en tiempo real.

## <a name="the-azure-rtos-advantage"></a>La ventaja de Azure RTOS
Azure RTOS proporciona las siguientes ventajas con respecto a otros sistemas operativos en tiempo real.

### <a name="most-deployed-rtos"></a>RTOS más implementado

Azure RTOS tiene de más de 6200 millones de implementaciones en todo el mundo, de acuerdo con la principal empresa de inteligencia de mercado de M2M, VDC Research. La popularidad de Azure RTOS se debe a su confiabilidad, calidad, tamaño, rendimiento, características avanzadas, facilidad de uso y tiempo de comercialización general.

> *"Hemos seguido la trayectoria de crecimiento de THREADX en los mercados inalámbricos y de IoT desde la fundación de la empresa y estamos cada vez más impresionados de la adopción de THREADX por parte del sector".* – Chris Rommel, Vicepresidente Ejecutivo, VDC Research.

### <a name="intuitive-and-consistent-api-design"></a>Diseño de API intuitivo y coherente

* API intuitiva y coherente.
* Convención de nomenclatura sustantivo-verbo.
* Todas las API tienen un prefijo inicial, como *tx_* en el caso de ThreadX y *nx_* en el de FileX, para identificar fácilmente el componente de Azure RTOS al que pertenecen.
* Coherencia funcional en todas las API. Por ejemplo, todas las funciones de API que se suspenden tienen un tiempo de espera opcional que funciona de forma idéntica.
* Muchas API están directamente disponibles desde los ISR de la aplicación.
- Devoluciones de llamada de notificación de usuario opcionales para operaciones de archivos y soporte físico.
* Modelo de programación basado en eventos (API).

### <a name="high-efficiency"></a>Alta eficacia

- Superficie de código pequeña.
- Superficie de código escalable en función de los servicios usados.
- Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4.
- Ejecución rápida Azure RTOS está diseñado pensando en la velocidad y tiene una capa mínima de llamadas a funciones internas, lo que ayudar a lograr el rendimiento más rápido posible.

### <a name="fastest-time-to-market"></a>Tiempo de comercialización más rápido

Azure RTOS es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener. Como resultado, Azure RTOS es uno de los más populares sistemas operativos en tiempo real para dispositivos IoT integrados, incluidos muchos SoC de Broadcom, Gainspan, etc. Nuestra ventaja continua de plazo de comercialización se basa en lo siguiente:

* Disponibilidad completa del código fuente.
* API fácil de usar.
* Conjunto de características completo y avanzado.
* Documentación de calidad.

### <a name="one-simple-license"></a>Una licencia sencilla

No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.

### <a name="full-highest-quality-source-code"></a>Código fuente completo y de máxima calidad

A lo largo de los años, el código fuente de Azure RTOS ha colocado el listón en calidad y facilidad de comprensión. Además, la convención de tener una función por archivo facilita la navegación por el origen.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Certificado previamente por TUV y UL para varios estándares de seguridad

Azure RTOS ha sido certificado por los SG-TUV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 SIL 4, CEI-62304 SW Clase de seguridad C, ISO 26262 ASIL D y EN 50128. La certificación confirma que Azure RTOS se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "seguridad funcional de sistemas relacionados con la seguridad electrónica de electricidad, electrónica y programable". SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="Certificación SGS-TUV":::

Azure RTOS ha sido reconocido por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998. UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.

:::image type="content" source="media/cru-logo-certification.png" alt-text="Certificación UL CRU":::

Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.

En los casos en los que la aplicación necesite certificación adicional, hay un servicio de certificación disponible con Microsoft para proporcionar una certificación llave en mano para varios estándares con la plataforma de hardware real e incluso abarcando el código de la aplicación. Póngase en contacto con nosotros para más detalles sobre nuestro servicio de certificación.

### <a name="eal4-common-criteria-security-certification"></a>Certificación de seguridad EAL4+ de Common Criteria

Azure RTOS ha logrado la certificación de seguridad EAL4+ de Common Criteria. El objetivo de la evaluación (TOE) cubre Azure RTOS ThreadX, Azure RTOS NetX Duo, TLS de Azure RTOS NetX Secure y MQTT de Azure RTOS NetX. Representa los protocolos de IoT más habituales que requieren los sensores, dispositivos, enrutadores perimetrales y puertas de enlace con alto grado de inserción.

:::image type="content" source="media/eal-logo-certification.png" alt-text="Certificación EAL":::

El recurso de evaluación de seguridad de TI usado para la certificación de seguridad de Microsoft Azure RTOS SC es Brightsight BV y la entidad de certificación es SERTIT.

### <a name="fips-140-2-validated"></a>Validación conforme a FIPS 140-2

Las bibliotecas criptográficas de Azure RTOS han logrado la certificación del Estándar federal de procesamiento de información 140-2 (FIPS 140-2) para software, que especifica los requisitos para los módulos criptográficos. FIPS 140-2 requiere que todos los organismos y departamentos gubernamentales federales que usan seguridad basada en cifrado cumplan los estándares específicos relacionados con el nivel y las funcionalidades de cifrado. Estos estándares de seguridad basados en el cifrado también se reconocen en Canadá y en la Unión Europea.

El laboratorio de evaluación de la seguridad de la información que se usó para las bibliotecas criptográficas de Azure RTOS fue atsec y la entidad de certificación es el [Instituto nacional de estándares y tecnología (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394).

### <a name="supports-most-popular-architectures"></a>Compatible con las arquitecturas más populares

Azure RTOS se ejecuta de serie en los microprocesadores de 32 y 64 bits más populares, se ha probado exhaustivamente y es totalmente compatible, incluidas las siguientes arquitecturas avanzadas.

- **Dispositivos analógicos**: SHARC, Blackfin, CM4xx

- **Andes Core**: RISC-V

- **Ambiqmicro**: Apollo MCU

- **ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

- **Cadence**: Xtensa, Diamond

- **CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

- **Cypress**: RISC-V

- **EnSilica**: eSi-RISC

- **Infineon**: XMC1000, XMC4000, TriCore

- **Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

- **Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

- **Microsemi**: RISC-V

- **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

- **Renesas**: SH, HS, V850, RX, RZ, Synergy

- **Silicon Labs**: EFM32

- **Synopsys**: ARC 600, 700, ARC EM, ARC HS

- **ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

- **Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

- **Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

- **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*

## <a name="in-the-context-of-azure-iot"></a>En el contexto de Azure IoT

Además de conectarse directamente a Azure IoT o conectarse indirectamente a través de Azure IoT Edge, Azure RTOS también está disponible en dispositivos Azure Sphere. La combinación de Azure RTOS y Azure Sphere reúne el mejor procesamiento en tiempo real y la mejor seguridad en un solo dispositivo.
