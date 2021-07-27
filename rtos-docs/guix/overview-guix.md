---
title: Descripción de Azure RTOS GUIX y Azure RTOS GUIX Studio
description: Azure RTOS GUIX es un paquete de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754937"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Información general de Azure RTOS GUIX y Azure RTOS GUIX Studio

La GUI insertada de Azure GUIX es la solución de GUI avanzada de nivel industrial de Microsoft diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas profundamente. Microsoft también proporciona una herramienta de diseño de escritorio WYSIWYG completa denominada Azure RTOS GUIX Studio, que permite a los desarrolladores diseñar su GUI en el escritorio y generar código de interfaz gráfica de usuario de Azure RTOS GUIX insertado que se puede exportar al destino. Azure RTOS GUIX está totalmente integrado con los RTOS de Azure RTO ThreadX y está disponible para muchos de los mismos procesadores admitidos por Azure RTOS ThreadX. Todo esto, combinado con un tamaño extremadamente pequeño, una ejecución rápida y una facilidad de uso superior, hacen de Azure RTOS GUIX la opción ideal para las aplicaciones de IoT integradas más exigentes que requieren una interfaz de usuario. 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>API eficaces

* Compatibilidad total con el dibujo de lienzo directo cuando sea necesario
* Fácil de interactuar con el código generado por Azure RTOS GUIX Studio
* API para líneas, rectángulos, polígonos, etc.
* API para círculos, arco, circular, cuerda, elipse, etc.
* API para dibujar y colocar texto
* Suavizado de contorno, relleno de textura y rellenos sólidos
* API para crear y modificar pantallas y widgets

### <a name="azure-rtos-guix-studio-generated-files"></a>Archivos generados por Azure RTOS GUIX Studio

* Archivos de código fuente ANSI C generados automáticamente
* Aísla el software de la aplicación de los detalles del diseño
* Incluye fuentes e imágenes que requiere el diseño de la interfaz de usuario
* Archivos generados compilados con código de aplicación
* El diseño de pantalla se puede actualizar sin afectar a la lógica de la aplicación
* Los identificadores de recursos crean independencia de lenguaje y tema
* Funciones de dibujo y procesamiento de eventos personalizadas proporcionadas por el usuario

### <a name="widget-library"></a>Biblioteca de widgets

* Conjunto predefinido pero personalizable de elementos comunes de la interfaz
* Extremadamente pequeño, compacto y eficaz
* La biblioteca incluye el botón, el medidor, la lista, la ventana, el desplazamiento, el control deslizante, la barra de progreso, el símbolo del sistema y muchos más
* Dibujo y apariencia totalmente personalizables
* Control de eventos y operaciones totalmente personalizables
* Solo los widgets usados están vinculados con el software de la aplicación

### <a name="math-and-utilities"></a>Matemáticas y utilidades

* Funciones para sin, cos, arcsin, arccos, tangente, raíz cuadrada
* Funciones para manipular regiones de pantalla
* Configuración e inicio del sistema
* Definición del grupo de memoria (opcional)
* Administración de temporizadores
* Administrador de animaciones
* Mantenimiento de la lista de integridad

### <a name="image-processing"></a>Procesamiento de imágenes

* Funciones para descodificar en tiempo de ejecución imágenes jpeg y png
* Aplicar la conversión de espacio de colores y interpolación
* Rotación de imagen
* Escalado de imagen
* Combinación de imagen

### <a name="event-processing"></a>Procesamiento de eventos

* Suspende automáticamente el subproceso de Azure RTOS GUIX cuando está inactivo
* Modelo de programación orientado a eventos conocido en el diseño de la interfaz de usuario
* Aísla los controladores de entrada del subproceso de dibujo de Azure RTOS GUIX
* Funciones para enviar y recibir eventos
* Tipos de eventos predefinidos para todos los tipos de widgets de Azure RTOS GUIX
* Se admiten eventos personalizados definidos por el usuario

### <a name="canvas-processing"></a>Procesamiento de lienzo

* Recorte y mantenimiento del orden Z
* Aísla la biblioteca de widgets de detalles de hardware
* Aísla la aplicación de los detalles de hardware
* Actualización automática en segundo plano de áreas desfasadas
* Se admiten varios lienzos con capas y combinación
* Se puede invocar directamente mediante el software de la aplicación

### <a name="input-device-drivers"></a>Controladores de dispositivo de entrada

* Compatibilidad específica con el hardware, Azure RTOS GUIX y la aplicación aislada de los detalles de hardware
* Touch resistente, extremo touch y teclado numérico compatible
* Eventos de entrada pasados a la cola de eventos de Azure RTOS GUIX

### <a name="display-drivers"></a>Mostrar controladores

* Compatibilidad específica del hardware
* Controladores genéricos proporcionados para todos los formatos y la profundidad de color
* Personalización para el uso de aceleradores de gráficos disponibles

### <a name="target-hardware"></a>Hardware de destino

* Casi cualquier hardware con capacidad de salida gráfica es compatible con GUIX
* Se admiten varias pantallas físicas
* Requisitos de RAM y Flash mínimos

## <a name="create-elegant-user-interfaces"></a>Crear interfaces de usuario elegantes

Azure RTOS GUIX y Azure RTOS GUIX Studio proporcionan todas las características necesarias para crear interfaces de usuario de forma exclusiva. El paquete estándar de Azure RTOS GUIX incluye varias interfaces de usuario de ejemplo, entre las que se incluyen una referencia de dispositivo médico, una referencia de smart watch, una referencia de automatización doméstica, una referencia de control industrial, una referencia de automóviles y varios ejemplos de objetos sprite y animación. Haga clic en los ejemplos de referencia que se muestran a continuación.

### <a name="home-automation"></a>Automatización de inicio

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Medicina

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Consumidor

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Electrodomésticos

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Automoción

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Industrial

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Cada referencia de Azure RTOS GUIX tiene un proyecto de Azure RTOS GUIX Studio correspondiente que define todos los elementos gráficos del diseño de referencia. Es fácil cambiar el diseño de una referencia. Simplemente abra el proyecto Azure RTOS GUIX correspondiente, realice los cambios deseados, guarde el proyecto y, a continuación, seleccione *Proyecto*.

Genere todos los archivos de salida para generar el código C para Azure RTOS GUIX. A continuación, simplemente vuelva a compilar la aplicación de destino y ejecútela para observar el diseño de referencia modificado.

### <a name="guix-memory-footprint"></a>Superficie de memoria de GUIX

Azure RTOS GUIX tiene una superficie mínima de 13,2 KB de FLASH y 4 KB de RAM para soporte básico, sin incluir la memoria necesaria para un lienzo.

En el caso de una pantalla con la tecnología interna GRAM y de actualización automática, no se requiere memoria de lienzo. Sin embargo, para mejorar el rendimiento del dibujo o para una configuración de pantalla que no use GRAM local para esta, la aplicación define un área de memoria de lienzo.

Los requisitos de memoria de lienzo son una función del tamaño de este y la profundidad de color, y se definen mediante la fórmula:

<i>Lienzo RAM (bytes) = (x * y * (bpp/8))</i>

Donde "x" y "y" son las dimensiones del lienzo (Mostrar).

La mayoría de las aplicaciones también usan recursos gráficos, que no se incluyen en los requisitos básicos de almacenamiento de la biblioteca Azure RTOS GUIX. Estos recursos incluyen fuentes, iconos gráficos (PixelMap) y cadenas estáticas. Estos datos se pueden almacenar en la sección de memoria const (es decir, FLASH).

El tamaño de este área de memoria depende de varios factores, como el número y el tamaño de las fuentes únicas utilizadas, el número y el tamaño de los iconos gráficos usados, el formato de color de salida y si cada recurso está usando datos comprimidos, ya que Azure RTOS GUIX admite la compresión RLE de los datos de fuente y de PixelMap. Los requisitos de almacenamiento de cada recurso se muestran dentro de la aplicación Azure RTOS GUIX Studio, lo que permite al usuario realizar un seguimiento y supervisar la cantidad de memoria Flash que consumirán los recursos de la aplicación.

Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS GUIX se escala automáticamente en función de los servicios que la aplicación usa realmente. Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.

#### <a name="simple-easy-to-use"></a>Simple y fácil de usar

Azure RTOS GUIX es muy simple de usar y Azure RTOS GUIX Studio lo hace aún más fácil al permitir a los desarrolladores diseñar visualmente en el escritorio y generar código C que se ejecuta en el objetivo real. Después, las aplicaciones pueden agregar sus propias funciones de control de eventos y dibujo personalizadas para completar su GUI.

El uso de la API de Azure RTOS GUIX es sencillo. La API de Azure RTOS GUIX es intuitiva y altamente funcional. Los nombres de API se componen de palabras reales y no de la "sopa de letras" ni de los nombres muy abreviados que son tan comunes en otros productos del sistema de archivos. Todas las API de Azure RTOS GUIX tienen una *gx_* inicial y siguen una convención de nomenclatura de sustantivos. Además, existe una coherencia funcional en la API. Por ejemplo, todas las API que inicializan un bloque de control widget se denominan &lt;widget_type&gt;_create y los parámetros de la función crear para cada tipo de widget siempre se definen en el mismo orden.

### <a name="comprehensive-set-of-built-in-widgets"></a>Conjunto completo de widgets integrados

* Azure RTOS GUIX ofrece un amplio conjunto de widgets integrados, entre los que se incluyen:
* Menú Accordion
* Botón
* Casilla de verificación
* Medidor circular
* Lista desplegable
* Lista horizontal
* Horizontal Scrollbar Window
* Icono
* Botón de icono
* Gráfico de líneas
* Menú
* Botón de texto de varias líneas
* Entrada de texto de varias líneas
* Vista de texto de varias líneas
* Solicitud PixelMap numérica
* Solicitud numérica
* Rueda del mouse numérico
* Botón PixelMap
* Símbolo del sistema de PixelMap
* Control deslizante PixelMap
* Sprite PixelMap
* ProgressBar
* Prompt
* Barra de progreso radial
* Radio Button
* Rueda del mouse
* Entrada de texto de una sola línea
* Control deslizante
* Rueda del mouse de cadena
* Botón de texto
* Vista de árbol
* Lista vertical
* Barra de desplazamiento vertical

También es fácil para la aplicación crear sus propios widgets de cliente.

### <a name="complete-low-level-drawing-api"></a>Completar la API de dibujo de bajo nivel

Azure RTOS GUIX proporciona una API de dibujo de lienzo sólida, lo que permite que la aplicación represente formas gráficas complejas.

Todas las funciones admiten el suavizado de contorno en los objetivos de profundidad de color alta y todas las formas se pueden rellenar, incluidos los rellenos de patrón sólido y PixelMap. Todos los primitivos de dibujo admiten el pincel alfa cuando se ejecutan con 16 bpp y una profundidad de color superior. Las funciones de dibujo incluyen:

* Dibujo de arco
* Dibujo con círculo
* Dibujo de línea
* Dibujo circular
* PixelMap Blend
* Icono de PixelMap
* Dibujo de polígono
* Dibujo de texto
* Dibujo de cuerda
* Dibujo de elipse
* Dibujo de píxeles
* Dibujo de PixelMap
* Girar PixelMap
* Dibujo de rectángulo
* Combinación de texto

### <a name="default-free-fonts-and-easy-to-add-more"></a>Fuentes gratuitas predeterminadas y fáciles de agregar

Azure RTOS GUIX proporciona un conjunto gratuito de fuentes TrueType. Los desarrolladores pueden agregar fuentes TrueType adicionales según sea necesario.

El formato de fuente Azure RTOS GUIX admite el suavizado de contorno 8 bpp, el suavizado de contorno de 4 bpp y las fuentes monocromáticas 1 bpp. En el caso de la mayoría de las aplicaciones con restricciones de recursos, Azure RTOS GUIX prerepresenta las fuentes TrueType en un formato de mapa de bits comprimido mediante nuestra herramienta de escritorio de GUIX Studio.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Implementación descodificador de JPG y PNG personalizado

Implementación del descodificador JPG y PNG personalizado, implementación del descodificador de archivos JPG y PNG. Esta implementación admite la conversión de espacio de colores, la interpolación y la creación en tiempo de ejecución de imágenes con formato PixelMap compatible con Azure RTOS GUIX.

### <a name="extensive-display-and-touchscreen-support"></a>Amplia compatibilidad con pantallas y pantallas táctiles

Azure RTOS GUIX proporciona controladores de pantalla genéricos para casi todos los formatos de color, incluido el monocromo de 1 bpp, la paleta de 8 bpp, el formato 3:3:2 de 8 bpp,

el formato 16 bpp 565 rgb, el formato 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b y el formato 32 bpp a:r:g:b. Además, Azure RTOS GUIX se integra con muchos de los aceleradores de hardware y controladores LCD más populares (ST ChromeArt, Renesas Synergy, etc.).

Azure RTOS GUIX es totalmente compatible con la pantalla táctil (incluida la compatibilidad con gestos), el lápiz y los dispositivos de entrada de teclado virtual.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Herramienta de escritorio WYSIWYG de Azure RTOS GUIX Studio

Azure RTOS GUIX Studio proporciona un entorno de diseño de pantalla WYSIWYG completo que permite al usuario arrastrar y colocar elementos gráficos usados para compilar las pantallas de la GUI. Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino. Los desarrolladores pueden generar fuentes previamente representadas para su uso en una aplicación mediante la herramienta de generación de fuentes de Azure RTOS GUIX Studio integrada. Las fuentes se pueden generar en formatos monocromo o suavizados y se optimizan para ahorrar espacio en el destino. Las fuentes pueden incluir cualquier juego de caracteres, incluidos los caracteres Unicode para aplicaciones multilingües.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure RTOS GUIX Studio facilita la importación de gráficos de archivos PNG o JPG con la conversión a los PixelMap de Azure RTOS GUIX comprimidos para su uso en el sistema de destino. Muchos de los tipos de widgets de Azure RTOS GUIX están diseñados para incorporar gráficos de usuario para una apariencia personalizada. Además, Azure RTOS GUIX Studio permite la personalización de los colores predeterminados y los estilos de dibujo usados por los widgets de Azure RTOS GUIX, lo que permite a los desarrolladores ajustar la apariencia de Azure RTOS GUIX muy fácilmente. La generación y el mantenimiento de cadenas de aplicación es otra instalación integrada de Azure RTOS GUIX Studio. Esto permite a los desarrolladores diseñar una aplicación con un lenguaje para desarrollar y agregar de forma rápida y sencilla compatibilidad para idiomas adicionales después de lanzar el producto. Se puede ejecutar una aplicación completa de Azure RTOS GUIX en un equipo de escritorio en el entorno de Azure RTOS GUIX Studio, lo que permite una generación y demostración rápidas y sencillas de conceptos de GUI, pruebas de flujos de pantalla y observación de transiciones de pantalla y animaciones. Una vez completado, un diseño se puede exportar como estructuras de datos de C listas para el destino, listas para su compilación y vinculación con las bibliotecas de Azure RTOS GUIX y Azure RTOS ThreadX.

Azure RTOS GUIX y Azure RTOS GUIX Studio admiten varios temas de recursos, lo que permite que una aplicación se pueda cambiar fácilmente de nivel en tiempo de ejecución. Las fuentes, los colores y el PixelMap se pueden cambiar en tiempo de ejecución con una API simple.

Más información sobre GUIX Studio

### <a name="complete-win32-simulation"></a>Completar la simulación de Win32

Azure RTOS GUIX se ejecuta en un equipo con Windows, usando exactamente la misma biblioteca de dibujo que se ejecuta en la placa de destino. Con Azure RTOS GUIX, puede compilar y ejecutar una aplicación GUI en el equipo y usar el mismo código de aplicación en el destino para la depuración, la creación de prototipos, la demostración y el funcionamiento del destino WYSIWYG.

### <a name="advanced-technology"></a>Tecnología avanzada

* La tecnología avanzada de Azure RTOS GUIX incorpora:
* Combinación alfa
* Suavizado de contorno
* Escalado automático
* Compresión de mapa de bits
* Combinación de lienzos
* Compatibilidad con widgets personalizados
* Compatibilidad con dibujos diferidos
* Compatibilidad con la interpolación
* Programación neutra endian
* Compatibilidad con el acelerador de hardware
* Compatibilidad multilingüe y codificación UTF-8
* Compatibilidad con varias pantallas y lienzos
* Recorte, dibujo y control de eventos optimizados
* Descodificador de JPEG y PNG runtime
* Cambio de aspecto visual y temas
* Admite monocromo a través de color verdadero de 32 bits con formatos de gráficos alfa
* Transiciones, sprites y compatibilidad con animaciones
* Simulación de Win32
* Administración de ventanas, incluidas las ventanillas y el mantenimiento de orden Z
