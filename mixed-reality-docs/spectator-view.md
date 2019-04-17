---
title: Vista del espectador
description: Visualizar hologramas desde un dispositivo externo como un medio para demostrar una experiencia de realidad mixta en una pantalla externa o grabación de vídeo de una experiencia de realidad mixta.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Vista del espectador, iOS, iPhone, iPad, OpenCV, cámara, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, demostración, registro
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602268"
---
# <a name="spectator-view-for-hololens"></a>Vista del espectador para HoloLens

![Rotulador](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>Refactorizar actual

> [!NOTE]
>Vista del espectador para HoloLens se están refactorizando activamente. Este trabajo está diseñado para consolidar la versión preliminar y Pro códigos base y ampliar la compatibilidad a HoloLens 2. 

Para ver el actual estado de la refactorización de vista del espectador consulte ramas ' característica/spectatorView' en el MixedRealityToolkit y MixedRealityToolkit Unity repositorios:

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

y

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>Información general

Cuando uso un HoloLens, nos olvidamos a menudo que una persona que no dispone de él no experimentar las maravillas que podemos. Vista del espectador permite que otros vean en una pantalla 2D, lo que ve un usuario de HoloLens en su mundo.
Vista del espectador (versión preliminar) es rápido y asequible enfoque grabación hologramas en HD, mientras el espectador Vista Pro está destinado a la grabación de calidad profesional de hologramas.

En la tabla siguiente se muestra las opciones y sus capacidades. Elija la opción que mejor se adapte a sus necesidades de grabación de vídeo:

|                                      | Vista del espectador (versión preliminar) |              Espectador ver Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Calidad de alta definición                         |         Full HD         |        Calidad profesional grabación (según lo determinado por DSLR)      |
| Movimiento fácil cámara                      |            ✔            |                                             |
| Vista de la tercera persona                    |            ✔            |                      ✔                      |
| Se pueden transmitir a pantallas           |            ✔            |                      ✔                      |
| portátil                             |            ✔            |                                             |
| Inalámbrico                             |            ✔            |                                             |
| Requisitos de hardware adicionales         |     iPhone (o iPad)    | HoloLens plataforma trípode + DSLR + PC + + Unity |
| Inversión de hardware                  |           Bajo           |                     Alto                    |
| Multiplataforma                       |           iOS           |                                             |
| Puede interactuar Visor                  |            ✔            |                                             |
| Funciones de red requieren (UNET scripting) |            ✔            |                      ✔                      |
| Duración del programa de instalación en tiempo de ejecución               |         Instantánea         |                     Nivel lento                    |

## <a name="spectator-view-preview"></a>Vista del espectador (versión preliminar)

![Rotulador](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>Casos de uso

- Hologramas rodaje en HD: Utiliza la vista del espectador (versión preliminar), puede registrar una experiencia de realidad mixta con un iPhone. Registro de full HD y aplicar suavizado de contorno para hologramas e incluso sombras. Es una manera rápida y rentable para capturar vídeo de hologramas.
- Demostraciones en vivo: Experiencias de realidad mixta de Stream en vivo a un dispositivo Apple TV directamente desde su iPhone o iPad, libre de posposición!
- Compartir la experiencia con los invitados: Permiten a los usuarios que no sean HoloLens experimentar hologramas directamente desde sus teléfonos o tabletas.

### <a name="current-features"></a>Características actuales

- La detección automática para agregar teléfonos a la sesión de red.
- Control de sesión automático, por lo que los usuarios se agregan a la sesión correcta.
- Sincronización espacial de hologramas, por lo que todos los usuarios ven hologramas en el mismo lugar exacto.
- compatibilidad con iOS (dispositivos habilitados para ARKit).
- Varios de los invitados de iOS.
- Grabación de vídeo hologramas sonido de ambiente + + sonido holograma.
- Compartir la hoja para que pueda guardar vídeo, enviarlo por correo electrónico o compartir con otras aplicaciones auxiliares.


>[!NOTE] 
>No se puede usar el código de vista del espectador (versión preliminar) con el código de versión Pro de vista del espectador. Se recomienda implementarla en los nuevos proyectos donde se requiere la grabación de vídeo de hologramas.

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>Licencias

- [OpenCV - (licencia BSD de cláusula de 3)](https://opencv.org/license.html)
- [Unity ARKit - (licencia MIT)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>Cómo configurar la vista del espectador (versión preliminar)

### <a name="requirements"></a>Requisitos

- [Complemento de vista del espectador y archivos binarios necesarios de OpenCV](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -más información sobre cómo integrar el complemento nativo de vista del espectador encontrará a continuación. Desde los archivos binarios generados, necesitará:

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Vista del espectador utiliza redes de Unity (UNET) de detección de redes y sincronizando espacial. Esto significa que toda la interactividad durante la aplicación debe sincronizarse entre los dispositivos.
- Unity 2017.2.1p2 o posterior
- Hardware
    - Un HoloLens
    - PC Windows que ejecutan Windows 10
    - Dispositivo compatible ARKit (iPhone 6s y versiones posteriores o iPad Pro 2016 y versiones posteriores / iPad 2017 y versiones posteriores)-con iOS 11 o superior
    - Equipo Mac con xcode 9.2 y versiones posteriores
- Cuenta de desarrollador de Apple, gratuita o [de pago](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Compilar el complemento de vista del espectador nativo

Para generar los archivos necesarios, siga estos pasos: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>Configuración del proyecto

1. Preparación de la escena, lo que garantiza que un gameobject de raíz del mundo contiene todos los gameobjects visible dentro de su escena.

    ![Raíz del mundo](images/SpecViewPhoneWorldRoot2.PNG)

2. Agregue el recurso prefabricado SpectatorView ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) en la escena.
3. Agregue el recurso prefabricado SpectatorViewNetworking ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) en la escena.
4. Seleccione el gameobject SpectatorViewNetworking y en el componente SpectatorViewNetworkingManager, hay algunas cosas que puede vincular. Si no modifica izquierda este componente buscará los scripts necesarios en tiempo de ejecución.
    - Marcador detección HoloLens -> SpectatorView, Hololens o MarkerDetection
    - Marcador generación 3D -> SpectatorView/IPhone/SyncMarker/3DMarker

    ![Detección de redes SpectatorView](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>La aplicación de red

- Vista del espectador usa UNET para sus redes y administra todas las conexiones de cliente de host para usted.
- Los datos específicos de la aplicación tienen que estar sincronizado e implementado por el usuario, mediante, por ejemplo, SyncVars, NetworkTransform, NetworkBehavior.
- Para obtener más información sobre redes de Unity, visite [participan varios jugadores y redes](https://docs.unity3d.com/Manual/UNet.html). (Tenga en cuenta: UNet está desusado; la refactorización actual de la base de código de vista del espectador resolverá este problema)

### <a name="building-for-each-platform-hololens-or-ios"></a>Creación de aplicaciones para cada plataforma (iOS o HoloLens)

- Al compilar para iOS, asegúrese de que quitar el componente GLTF de MRTK como esto aún no es compatible con esta plataforma.
- En el nivel superior de la prefabricado SpectatorView hay un componente denominado a 'Plataforma modificador'. Seleccione la plataforma que desea compilar.
    - Si ha seleccionado 'Hololens' debería ver todos los gameobjects bajo el gameobject iPhone en el prefabricado SpectatorView inactivo y todos los gameobjects en 'Hololens' convertido en activo.
    - Esto puede tardar un rato como según la plataforma elija el HoloToolkit se va a agregar o quitar del proyecto.

    ![Selector de plataforma](images/SpecViewPhoneSwitcher.PNG)

- Asegúrese de que crear todas las versiones de la aplicación con la misma instancia de editor de Unity (lo que Unity no cerrar entre compilaciones) debido a un problema sin resolver con Unity.

### <a name="running-your-app"></a>Ejecutar la aplicación

Una vez que ha creado e implementado una versión de aplicación en iPhone y en HoloLens, debe ser capaz de conectarse a ellos.

1. Asegúrese de que ambos dispositivos están en la misma red Wi-Fi.
2. Inicie la aplicación en ambos dispositivos, en ningún orden específico. El proceso de inicio de la aplicación en el iPhone debe desencadenar la cámara de HoloLens para activar y empezar a disfrutar de las imágenes.
3. En cuanto se inicia la aplicación de iPhone, buscará superficies, como los pisos o tablas. Cuando se encuentran las superficies, debería ver un marcador similar al siguiente. Mostrar este marcador para el HoloLens.

    ![Rotulador](images/SpecViewPhoneMarker.PNG)

4. Una vez que se ha detectado el marcador por la HoloLens debería desaparecer y ambos dispositivos deben conectados y sincronizados espacialmente.

### <a name="recording-video"></a>Grabación de vídeo

1. Para capturar y guardar un vídeo desde el iPhone, pulse y mantenga presionada la pantalla durante 1 segundo. Se abrirá el menú de la grabación.
2. Pulse el botón de grabación rojo, se iniciará una cuenta atrás antes de empezar a grabar la pantalla.
3. Para finalizar la grabación pulse y mantenga la pantalla para otro 1 segundo, a continuación, puntee en el botón Detener.
4. Cuando se cargue el vídeo grabado, aparecerá un botón de vista previa (botón azul), pulse para ver el vídeo grabado.
5. Abra la hoja del recurso compartido y seleccione Guardar en el álbum de cámara.

### <a name="example-scene"></a>Escena de ejemplo

Puede encontrar una escena de ejemplo en [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>Solución de problemas

**El Editor de Unity no se conecta a una sesión hospedada por un dispositivo HoloLens**

- Esto podría ser el Firewall de Windows.
- Vaya a opciones de Firewall de Windows.
- Permitir que una aplicación o una característica a través de Firewall de Windows.
- Para todas las instancias del Editor de Unity en el paso de la lista, dominio, privado o público.
- A continuación, vuelva a las opciones de Firewall de Windows.
- Haga clic en Configuración avanzada.
- Haga clic en reglas de entrada.
- Todas las instancias del Editor de Unity deben tener una marca de verificación verde.
- Para las instancias del Editor de Unity que no tengan una marca de verificación verde:
    - Haga doble clic en él.
    - En el cuadro de diálogo acción seleccione Permitir la conexión.
    - Haga clic en Aceptar.
    - Reinicie el Editor de Unity.

**En tiempo de ejecución, la pantalla del iPhone dice "Buscar piso..." pero no se muestra un marcador de AR.**

- El iPhone está buscando una superficie horizontal por lo que intente señalar la cámara iPhone hacia el suelo o una tabla. Esto le ayudará a ARKit encontrar superficies necesarios que se sincronice espacialmente con HoloLens.

**Cámara HoloLens no activa automáticamente cuando iPhone intenta unirse.**

- Asegúrese de que se ejecutan HoloLens y iPhone en la misma red Wi-Fi.

**Al iniciar una aplicación de vista del espectador en un dispositivo móvil, otros hololens que ejecutan otras aplicaciones de la vista del espectador encender su cámara**

- El componente NewDeviceDiscovery GoTo y cambie el puerto de la clave de difusión y difusión a dos valores únicos.
- Vaya a SpectatorViewDiscovery y cambiar la clave de difusión y el puerto de difusión a otro conjunto de números únicos.

**No se conectan el HoloLens con el Editor de Unity de mac.**

- Se trata de un problema conocido que podría vincularse a la versión de Unity. Al compilar para el iPhone todavía debe trabajar y conectar con normalidad.

**La cámara de HoloLens activa, pero no es capaz de analizar el marcador.**

- Asegúrese de que crear todas las versiones de la aplicación con la misma instancia de Editor de Unity (lo que Unity no cerrar entre compilaciones). Esto es debido a un problema desconocido con Unity.

## <a name="spectator-view-pro"></a>Espectador ver Pro

![Configuración de vista del espectador](images/spectatorview-300px.png)

Uso de Pro de vista del espectador implica estos cuatro componentes:
1. Una aplicación creada específicamente para habilitar la vista del espectador, que se basa en [comparten experiencias en realidad mixta](shared-experiences-in-mixed-reality.md).
2. Un usuario wearing HoloLens mediante la aplicación.
3. Una plataforma de cámara espectador vista que proporciona un vídeo de la perspectiva de la tercera persona.
4. Un PC de escritorio que se ejecuta la aplicación de experiencia compartida y la composición la hologramas en un vídeo de vista del espectador.

![Configuración de vista Pro spectator](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>Casos de uso

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Vista del espectador puede utilizarse para compartir sus creaciones holográficas, tanto si son una demostración en directo, un clip de vídeo o una imagen fija.*


Hay tres escenarios fundamentales que funcionan correctamente con esta tecnología:

**1. Captura de fotografías**<br>
Con esta tecnología, puede capturar imágenes de alta resolución de sus hologramas. Estas imágenes se pueden usar para presentar contenido en los eventos de marketing, enviar a los clientes potenciales o incluso enviar la aplicación para que el Store de Windows. Podrá decidir qué cámara de fotografía que le gustaría usar para capturar estas imágenes, por lo tanto puede ser preferible una cámara DSLR de calidad.


![Ejemplo de captura fotográfica Vista Pro spectator](images/fall-350px.jpg)<br>
*Ejemplo de captura de fotografías - dándole el suelo está formado por lava.*


**2. Captura de vídeo**<br>
Vídeos son la mejor historia indicando el mecanismo para compartir una experiencia de aplicación holográfica con muchas personas. Vista del espectador le permite elegir la cámara, lente y tramas que mejor se adapte a cómo desea que presente su aplicación. Lo coloca en el control de la calidad de vídeo en función del hardware de vídeo que tiene disponible.

![Ejemplo de captura de vídeo vista Pro spectator](images/spectatorviewvideo.gif)<br>
*Ejemplo de captura de vídeo: grabar una experiencia de colaboración de realidad mixta.*


**3. Demostraciones en vivo**<br>
Vista del espectador es un enfoque preferido para demostraciones en vivo, como la posición de la cámara permanece constante o controlada. Dado que puede usar una cámara de vídeo de alta calidad, también puede generar imágenes de alta calidad destinadas a una pantalla grande. Esto también es adecuado para la transmisión de demostraciones en vivo en una pantalla, posiblemente a participantes diligente en línea esperando su turno.

### <a name="comparing-video-capture-techniques"></a>Comparación de las técnicas de captura de vídeo

[Mixto captura realidad](mixed-reality-capture.md) (MRC) proporciona un vídeo compuesto de lo que está viendo el usuario HoloLens de una persona del primer punto de vista. Vista del espectador genera un vídeo desde una perspectiva de la tercera persona, lo que permite el observador de vídeo ver el entorno con hologramas y el usuario con un dispositivo HoloLens. Porque tiene una opción de cámara, también pueden generar vistas espectador una resolución mayor y mejor calidad de las imágenes de la cámara integrada de HoloLens usa para imágenes MRC. Por este motivo, la vista del espectador es más adecuada para imágenes de la aplicación en la Windows Store, vídeos, de marketing o para proyectar una vista activa para una audiencia.

![Espectador Vista Pro profesional cámara que se usa en las presentaciones de conferencia de Microsoft](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Espectador Vista Pro profesional cámara que se usa en las presentaciones de conferencia de Microsoft*


Vista del espectador ha sido una parte esencial de cómo Microsoft HoloLens ha presentado experiencias para el público desde el principio cuando el producto se presentó en enero de 2015. El programa de instalación profesional utiliza tenía altas demandas y una etiqueta de precio costosa para ir con él. Por ejemplo, la cámara utiliza una señal genlock para garantizar una sincronización precisa que se coordina con el sistema de seguimiento de HoloLens. En esta configuración, mover la cámara de vista del espectador era posible manteniendo hologramas estable para que coincida con la experiencia de alguien que está viendo la experiencia directamente en HoloLens.

La versión de código abierto de vista del espectador equilibra la capacidad para mover la plataforma de pruebas de la cámara con el fin de reducir considerablemente el costo de la configuración general. Este proyecto usa una cámara externa rígidamente montada en un HoloLens para tomar fotos de alta definición y vídeo de su proyecto Unity holográfico. **Durante las demostraciones en vivo, la cámara debe permanecer en una posición fija.** Movimiento de la cámara puede provocar inestabilidad holograma o desfase. Esto es porque el tiempo del marco del vídeo y la representación de hologramas en el equipo es posible que no se sincronice con precisión. Por lo tanto, mantener la cámara estables o limitar el movimiento generará un resultado cerca de lo que puede ver la persona con un HoloLens.

Para que la aplicación esté lista para la vista del espectador, debe crear un [compartido experiencia](holograms-240.md) aplicación y asegúrese de ejecutar la aplicación en HoloLens así como de escritorio en el editor de Unity. La versión de escritorio de la aplicación tendrá los componentes adicionales creados en esa fuente el vídeo con el hologramas representados de composición.

## <a name="how-to-set-up-spectator-view-pro"></a>Configuración de Pro de vista del espectador 

### <a name="requirements"></a>Requisitos

![Plataforma de pruebas spectator Vista Pro](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>Lista de compras de hardware

A continuación es una lista recomendada de hardware, pero puede experimentar con otras unidades compatibles demasiado. 

|Componente de hardware                                                                     |Recomendación               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|Una configuración de PC que funciona para el desarrollo holográfico con el emulador de HoloLens  |                              | 
|Cámara con salida de HDMI o SDK de la captura de fotografías                                             | Para la captura de vídeo y fotos, hemos probado el [Canon EOS 5D marca III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) cámara. Para obtener demostraciones en vivo, hemos probado el [Blackmagic diseño producción cámara 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).<br><br>Tenga en cuenta, debería funcionar cualquier cámara con HDMI out (p. ej. GoPro). Muchos de nuestros vídeos usan el [Canon EF 14mm f/2.8 L II USM Ultra-Wide ángulo fijo lente](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), pero debe elegir un objetivo de la cámara que satisfaga sus necesidades. | 
|Tarjeta para su PC obtener los marcos de color de la cámara para calibrar la plataforma de pruebas y obtener una vista previa de la escena de composición de captura |  Hemos probado el [Blackmagic diseño intensidad Pro 4K tarjeta de captura](https://www.amazon.com/dp/B00U3QNP7Q). | 
|Cables                                                                                 |  [HDMI a HDMI Mini](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) para conectar la cámara a la tarjeta de captura. Asegúrese de que adquirir un factor de forma HDMI que se adapte a la cámara. (GoPro, por ejemplo, se genera a través de [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)<br><br>[Cable HDMI](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) para ver el compuesto de fuente en un monitor de vista previa o televisión | 
|Las máquinas corchete de aluminio para conectar su HoloLens con la cámara. | [Corchete de aluminio](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D imprime el adaptador para conectar el montaje de HoloLens con la zapata con conexión para cámara.| [Adaptador impresa 3D](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Sujetador zapata con conexión para montar el adaptador zapata con conexión para                                       |  [Sujetador zapata con conexión para](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|Herramientas, bolts y frutos secos ordenados                                                |  [1/4-20" frutos secos](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20 "x 3/4" Bolts](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[Controlador de tuerca 7/16](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>Componentes de software

1. Descargar software desde el [proyecto de GitHub para la vista del espectador](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).
2. [Tarjeta de captura Blackmagic SDK](https://www.blackmagicdesign.com/support). \
 Búsqueda de escritorio vídeo SDK para desarrolladores en "Descargas más recientes".
3. [En tiempo de ejecución de vídeo de escritorio Blackmagic](https://www.blackmagicdesign.com/support). \
 Busque la actualización de Software de escritorio de vídeo en "Descargas más recientes". \
 Garantizar a las coincidencias de número de versión de la versión del SDK.
4. [3.1 OpenCV](https://opencv.org/releases.html) de calibración o captura de vídeo sin la tarjeta de captura Blackmagic.
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (opcional). \
 Si está utilizando una cámara Canon y tener acceso al SDK Canon, puede conecto la cámara al PC para aprovechar las imágenes de mayor resolución.
6. Unity para el desarrollo de aplicaciones holográfica. \
 Versión compatible puede encontrarse en el proyecto de OSS.
7. Visual Studio 2015 con las últimas actualizaciones.

### <a name="building-your-own-spectator-view-pro-camera"></a>Creación de su cámara espectador Vista Pro

**TENGA EN CUENTA &AMP; DECLINACIÓN DE RESPONSABILIDADES:** Al realizar modificaciones en el hardware de HoloLens (incluidos, pero sin limitarse a, la configuración de su HoloLens para "vista del espectador") básica deben observarse precauciones de seguridad. Leer todas las instrucciones y los manuales antes de realizar modificaciones. Es su responsabilidad siga todas las instrucciones y usar herramientas como se indica. Es posible que ha comprado o con licencia de su HoloLens con una garantía limitada o sin ninguna garantía. Lea su aplicable [HoloLens contrato de licencia o condiciones de uso y venta](https://www.microsoft.com/hololens/support/warranty) para comprender las opciones de garantía.

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Ensamblado de plataforma de pruebas

![Plataforma de Pro de vista del espectador montado con cámara HoloLens y DSLR.](images/assembly.gif)<br>
*Plataforma de Pro de vista del espectador montado con cámara HoloLens y DSLR*


* Use un destornillador T7 para quitar la cinta del pelo del HoloLens. Una vez separados los tornillos, echar un vistazo enviarlas con un clip desde el otro lado.
* Quitar el límite de un tornillo en el interior parte frontal del hipervisor de HoloLens con un certificado destornillador pequeño.
* Utilice un destornillador T15 para quitar los tornillos torx pequeño del soporte de HoloLens, quite el y en forma de enlace de datos adjuntos.
* Coloque el HoloLens en el corchete de cierre, alinear el agujero expuesto en el interior del visor con la extrusión en la parte frontal del corchete. El PIN en la parte inferior del corchete mantendrá armas de HoloLens en su lugar.
* Volver a adjuntar se y datos adjuntos en forma de enlace para proteger la HoloLens para el soporte.
* Adjunte el sujetador zapata con conexión para a la zapata con conexión para de la cámara.
* Conecte el adaptador de montaje al sujetador zapata con conexión para.
* Girar el adaptador para que el lado estrecho es hacia adelante y en paralelo a la lente.
* Proteger el adaptador en su lugar una tuerca 1/4" con el controlador de tuerca 7/16 con.
* Coloque el corchete en el adaptador para que la parte frontal del visor de HoloLens sea lo más parecida posible a la parte delantera de la lente.
* Adjunte el corchete con 4 1/4" domine los componentes con el controlador de tuerca 7/16.

#### <a name="pc-setup"></a>Configuración de PC
* Instalar el software de la sección de componentes de software.
* Agregue la tarjeta de captura a una ranura PCIe abierta en la placa base.
* Conecte un cable HDMI de la cámara a la ranura HDMI externa (HDMI-In) en la tarjeta de captura.
* Conecte un cable HDMI de la ranura HDMI center (HDMI salida) en la tarjeta de captura a un monitor de vista previa opcional.

#### <a name="camera-setup"></a>Configuración de cámara
* Cambiar la cámara al modo de vídeo, por lo que se genera en la resolución de 1920 x 1080 completa en lugar de un recortada resolución 3:4 de la fotografía.
* Busque la configuración de la cámara HDMI y habilite **creación de reflejo** o **Monitor Dual**.
* Configure la resolución de salida en 1080 p.
* Desactivar **Live vista en la vista de pantalla** para las superposiciones de pantalla no aparecen en la composición de fuente.
* Encienda la cámara **Live vista**.
* Si usa el **Canon SDK** y le gustaría usar una unidad flash, deshabilite **silenciosa LV Shoot**.
* Conecte un cable HDMI desde la cámara a la ranura HDMI externa (HDMI-In) en la tarjeta de captura.

#### <a name="calibration"></a>Calibración

Después de configurar la plataforma de pruebas de vista del espectador, debe calibrar con el fin de obtener el desplazamiento de posición y rotación de la cámara para su HoloLens.
* Abra la solución de Visual Studio de calibración bajo Calibration\Calibration.sln.
* En esta solución, puede encontrar el dependencies.props de archivo que crea macros para las ubicaciones de inc de los orígenes de parte 3ª.
* Actualizar este archivo con la ubicación instaló OpenCV 3.1, el SDK Blackmagic y el SDK de Canon (si procede)

![Instantánea de las ubicaciones de dependencia en Visual Studio](images/dependencies-600px.png)<br>
*Instantánea de las ubicaciones de dependencia en Visual Studio*


* Imprimir el patrón de calibración Calibration\CalibrationPatterns\2_66_grid_FULL.png en una superficie plana rígido.
* Conecte su HoloLens en su equipo a través de USB.
* Actualizar las definiciones del preprocesador **HOLOLENS_USER** y **HOLOLENS_PW** en **stdafx.h** con credenciales de portal de HoloLens en su dispositivo.
* Conectar la cámara a la tarjeta de captura a través de HDMI y enciéndalo.
* Ejecute la solución de calibración.
* Mover el patrón de tablero alrededor de la vista similar al siguiente:

![Calibración de la plataforma de Pro de vista del espectador](images/calibration.gif)<br>
*Calibración de la plataforma de Pro de vista del espectador*


* Una imagen se realizará automáticamente cuando un tablero de cuadros está en la vista. Busque la luz blanca en el visor de HoloLens antes de avanzar a la postura siguiente.
* Cuando haya terminado, presione **ENTRAR** con la aplicación de calibración de enfoque para crear un **CalibrationData.txt** archivo.
* Este archivo se guardará en **Documents\CalibrationFiles\CalibrationData.txt**
* Inspeccione este archivo para ver si los datos de calibración están precisos:
   * **RMS DSLR** debe aproximarse a 0.
   * **HoloLens RMS** debe aproximarse a 0.
   * **RMS estéreo** puede ser de 20 a 50, esto es aceptable ya que el campo de visión entre las dos cámaras pueden ser diferentes.
   * **Traducción** es la distancia desde la cámara de HoloLens al objetivo de la cámara adjunta. Se trata en metros.
   * **Rotación** debe aproximarse a la identidad.
   * **DSLR_fov** valor y debe aproximarse el campo de visión vertical se esperan de longitud de la lente. focal y cualquier factor de recorte del cuerpo de la cámara.
* Si cualquiera de los valores anteriores no parece que tiene sentido, vuelva a calibrar.
* Copie este archivo a la **activos** directorio en el proyecto de Unity.

### <a name="compositor"></a>Compositor

El compositor es una extensión de Unity que se ejecuta como una ventana en el editor de Unity. Para habilitar esta opción, la solución de Visual Studio de Compositor en primer lugar debe compilarse.
* Abra la solución de Visual Studio de Compositor en Compositor\Compositor.sln
* Actualizar dependencies.props con los mismos criterios de la solución de calibración anterior. Si ha seguido los pasos de calibración, este archivo ya se habrá actualizado.
* Compilar la solución completa como la versión y la arquitectura que coincide con la arquitectura de la versión de Unity. En caso de duda, compilación x86 y x64.
* Si ha compilado la solución para x64, genere también el proyecto SpatialPerceptionHelper como x86 desde que se ejecutará en el HoloLens.
* Cierre Unity si se está ejecutando la aplicación. Unity debe ser una nueva versión si se cambia los archivos DLL en tiempo de ejecución.
* Ejecute Compositor\CopyDLL.cmd para copiar los archivos DLL que se crea a partir de esta solución para el proyecto de Unity. Este script copiará los archivos DLL en el proyecto de ejemplo incluido. Una vez que haya configurado su propio proyecto, puede ejecutar CopyDLL con un argumento de línea de comandos que señala al directorio de recursos del proyecto para copiar allí también.
* Inicie la aplicación de ejemplo Unity.

### <a name="unity-app"></a>Aplicación de Unity

El compositor se ejecuta como una ventana del Editor de Unity. El proyecto de ejemplo incluido tiene todo lo ha configurado para trabajar con la vista del espectador una vez el compositor que se copia los archivos DLL.

Vista del espectador requiere que la aplicación que se ejecute como un [compartido experiencia](holograms-240.md). Esto significa que cualquier cambio de estado de la aplicación que se producen en el HoloLens necesario para la conexión en red para actualizar la aplicación en ejecución en Unity demasiado.

Si a partir de un nuevo proyecto de Unity, deberá hacer primero algunas opciones de configuración:
* Copia **activos/Addons/HolographicCameraRig** desde el proyecto de ejemplo a su proyecto.
* Agregue el MixedRealityToolkit más reciente al proyecto, incluidos **compartir**, **csc.rsp**, **gmcs.rsp**, y **smcs.rsp**.
* Agregue su **CalibrationData.txt** archivo a su directorio de recursos.

![Instantánea de directorio de activos de Unity](images/files-400px.png)

* Agregar el **HolographicCameraRig\Prefabs\SpectatorViewManager** prefabricado a la escena y rellene los campos:
   * **HolographicCameraManager** debe rellenarse con el recurso prefabricado de HolographicCameraManager desde el directorio prefabricado HolographicCameraRig.
   * **Delimitador** debe rellenarse con el recurso prefabricado de anclaje desde el directorio prefabricado HolographicCameraRig.
   * **Uso compartido** debe rellenarse con el recurso prefabricado de compartir desde el MixedRealityToolkit.
   * Nota: Si cualquiera de estos prefabricados ya existe en la jerarquía de proyecto, se usará el prefabricados existentes en lugar de estos clientes.
   * **IP de la vista del espectador** debe ser la dirección IP de su HoloLens conectados a la plataforma de pruebas de vista del espectador.
   * **IP del servicio de uso compartido** debe ser la dirección IP del equipo que ejecuta el MixedRealityToolkit SharingService.
   * Opcional: Si tiene varios espectador ver las plataformas que se adjunta a varios PC del, **IP de equipo Local** debe establecerse con el equipo se comunicará la plataforma de pruebas de la vista del espectador.

![Propiedades del Administrador de la vista del espectador en Unity](images/spectatorviewmanager-500px.png)

* Iniciar el MixedRealityToolkit **servicio de uso compartido**
* Compile e implemente la aplicación como un UWP D3D para el HoloLens asociada a la plataforma de pruebas de la vista del espectador.
* Implementar la aplicación en cualquier otro dispositivo HoloLens en la experiencia.
* Compruebe el **ejecutar en segundo plano** casilla en **edición/proyecto configuración/Reproductor**.

![Ejecutar en la configuración de fondo en Unity](images/run-in-bg-400px.png)
* Inicie la ventana de compositor en **Spectator vista/Compositor**

![Vista de Compositor de vista del espectador en Unity](images/compositor-500px.png)

* Esta ventana le permite:
   * Iniciar grabación de vídeo
   * Tomar una foto
   * Cambiar la opacidad holograma
   * Cambiar el desplazamiento de trama (que ajusta la marca de tiempo de color para representar la latencia de la tarjeta de captura)
   * Abra el directorio de en que las capturas se guardan
   * Solicitar datos de asignación espacial de la cámara de vista del espectador (si existe un SpatialMappingManager en el proyecto)
   * Visualización de vista compuesta la escena, así como color, hologramas y canal alfa individualmente.
   * Encienda la cámara.
   * Presione reproducir en Unity.
   * Cuando se mueve la cámara, deben ser hologramas en Unity dónde se encuentra en el mundo real en relación con el color de la cámara de fuente.

## <a name="see-also"></a>Vea también

* [Captura de realidad mixta](mixed-reality-capture.md) 
* [Mixto captura realidad para desarrolladores](mixed-reality-capture-for-developers.md)
* [Compartir experiencias en realidad mixta](shared-experiences-in-mixed-reality.md)
* [Código de vista (versión preliminar) del espectador en GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Código nativo de espectador View (vista previa) en GitHub](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [Código de vista Pro spectator en GitHub](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
