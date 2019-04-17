---
title: Actualización de aplicaciones UWP 2D de realidad mixta
description: Este artículo describe la actualización de la aplicación Universal Windows Platform 2D existente para ejecutarse en HoloLens y Windows Mixed Reality inmersivos.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Aplicación 2D, UWP, la aplicación sin formato, HoloLens, envolventes auriculares con micrófono, modelo de aplicación, realizar una copia de botón, barra de la aplicación, PPP, resolución de escalado
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602187"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Actualización de aplicaciones UWP 2D de realidad mixta

Windows Mixed Reality permite al usuario ver hologramas como si fueran derecho próximos, en el mundo físico o digital. En esencia, HoloLens y los equipos de escritorio adjuntar accesorios de auriculares envolventes son dispositivos de Windows 10; Esto significa que podemos casi todas las aplicaciones de plataforma Universal de Windows (UWP) se ejecutan en el Store como aplicaciones 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creación de una aplicación UWP 2D de realidad mixta

El primer paso para volver a poner una aplicación 2D para auriculares de realidad mixta es para que la aplicación que se ejecuta como una aplicación 2D estándar en el monitor de escritorio.

### <a name="building-a-new-2d-uwp-app"></a>Creación de una nueva aplicación para UWP 2D

Para crear una nueva aplicación 2D para mixed reality, sólo tiene que crear una aplicación de plataforma Universal de Windows (UWP) de 2D estándar. Ningún otro cambio de aplicación es necesario para esa aplicación, a continuación, ejecutar como una pizarra en realidad mixta.

Para empezar a compilar una aplicación UWP 2D, consulte el [crear su primera aplicación](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) artículo.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Portar una aplicación de Store 2D existente a UWP

Si ya tiene una aplicación de Windows 2D en el Store, primero debe asegurarse de tiene como destino la plataforma Universal de Windows de Windows 10 (UWP). Estos son todos los posibles puntos de partida que pudiera haber suscrito con la aplicación Store hoy mismo:
<br>

|  Punto de partida  |  Destino de la plataforma de manifiesto AppX  |  ¿Cómo realizar esta Universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifiesto de la aplicación de Silverlight |  [Migrar a WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Universal de Windows Phone 8.1  |  8.1 manifiesto AppX que no incluya la plataforma de destino  |  [Migrar la aplicación a la plataforma Universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  Manifiesto de AppX 8 que no incluya la plataforma de destino  |  [Migrar la aplicación a la plataforma Universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8.1 Universal  |  8.1 manifiesto AppX que no incluya la plataforma de destino  |  [Migrar la aplicación a la plataforma Universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 

Si tiene una aplicación de Unity 2D que hoy en día se compila como una aplicación de Win32 ("PC, Mac y Linux Standalone" destino de compilación), puede dirigirse a la realidad mixta mediante el cambio de Unity al destino build "Universal Windows Platform" en su lugar.

Hablaremos sobre las formas que la aplicación se puede restringir específicamente a HoloLens con la familia de dispositivos Windows.Holographic [debajo](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Ejecutar la aplicación 2D auriculares envolventes Windows Mixed Reality

Si ha implementado la aplicación 2D para el equipo de escritorio donde va a desarrollar y probar en el monitor, ya está listo para probarlo en un auricular escritorio envolvente.

Simplemente vaya al menú Inicio dentro de los auriculares de realidad mixta e inicie la aplicación a partir de ahí. El shell de escritorio y el shell holográfico comparten el mismo conjunto de aplicaciones para UWP y, por lo que la aplicación ya debe estar presente cuando se haya implementado desde Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Destinado a inmersivos y HoloLens

¡Enhorabuena! La aplicación está utilizando la plataforma Universal de Windows de Windows 10 (UWP).

La aplicación ahora es capaz de ejecutarse en dispositivos de Windows de hoy en día, como el escritorio, móviles, Xbox, inmersivos Windows Mixed Reality y HoloLens, así como futuros dispositivos de Windows. Sin embargo, para están dirigidos a todos los dispositivos, deberá asegurarse de que la aplicación está destinada a la familia de dispositivos de Windows.Universal.

### <a name="change-your-device-family-to-windowsuniversal"></a>Cambiar la familia de dispositivos a Windows.Universal

Ahora pasemos a su manifiesto de AppX para asegurarse de que la aplicación de Windows 10 UWP puede ejecutarse en HoloLens:
* Abra el archivo de solución de la aplicación con **Visual Studio** y navegue hasta el manifiesto del paquete de aplicación
* Haga clic en el **Package.appxmanifest** de archivos de la solución y vaya a **ver código**<br>
  ![Package.appxmanifest en el Explorador de soluciones](images/openappxmanifest-500px.png)<br>
* Asegúrese de que la plataforma de destino es Windows.Universal en la sección de dependencias
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* ¡Guardar!

Si no usa Visual Studio para el entorno de desarrollo, puede abrir **AppXManifest.xml** en el editor de texto que prefiera para asegurarse de que tiene como destino el **Windows.Universal**  *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Ejecutar en el emulador de HoloLens

Ahora que la aplicación de UWP tiene como destino "Windows.Universal", vamos a compilar la aplicación y ejecutarla el [emulador de HoloLens](using-the-hololens-emulator.md).
* Asegúrese de tener [instalado el emulador de HoloLens](install-the-tools.md).
* En Visual Studio, seleccione el **x86** crear configuración de la aplicación

  ![x86 crear configuración en Visual Studio](images/x86setting.png)<br>
* Seleccione **emulador de HoloLens** en el menú desplegable de destino de implementación

  ![Emulador de HoloLens en la lista de destinos de implementación](images/deployemulator-500px.png)<br>
* Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración.
* El emulador se inicie y ejecute la aplicación.
* Con un teclado, mouse o un mando de Xbox, colocar la aplicación en el mundo para iniciarlo.

  ![Emulador de HoloLens cargado con un ejemplo UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Pasos siguientes

En este momento, puede suceder dos cosas:
1. La aplicación mostrará su presentación y empezar a ejecutar cuando se ha colocado en el emulador. ¡Impresionante!
2. O bien, una vez que aparezca una animación de carga para un holograma 2D, se detendrá la carga y solo verá la aplicación en su pantalla de presentación. Esto significa que algo ha ido mal y tardará más investigación para comprender cómo hacer que la aplicación a la vida en realidad mixta.

Para llegar a la parte inferior de las posibles causas de la aplicación de UWP no se inicie en HoloLens, tendrá que depurar.

### <a name="running-your-uwp-app-in-the-debugger"></a>Ejecuta la aplicación para UWP en el depurador

Estos pasos le guiará a través de la depuración de la aplicación para UWP con el depurador de Visual Studio.
* Si aún no lo ha hecho, abra la solución en Visual Studio. Cambiar el destino para la **emulador de HoloLens** y la configuración de compilación para **x86**.
* Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración.
* Colocar la aplicación en el mundo con el mouse, un teclado o un mando de Xbox.
* Ahora, Visual Studio debe pararse en algún lugar en el código de aplicación.
  - Si la aplicación inmediatamente no bloqueará o interrumpir el depurador debido a un error no controlado, a continuación, vaya a través de un paso de prueba de las características principales de la aplicación para asegurarse de que todo está ejecutándose y funcional. Es posible que vea errores como la imagen de abajo (excepciones internas que se controlan). Para asegurarse de que no pase por alto los errores internos que afectan a la experiencia de la aplicación, ejecutar sus pruebas automatizadas y pruebas unitarias para asegurarse de que todo se comporta según lo previsto.

![Emulador de HoloLens cargado con un ejemplo UWP que muestra una excepción del sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Actualizar la interfaz de usuario

Ahora que se ejecuta la aplicación para UWP en inmersivos o HoloLens como un holograma 2D, a continuación nos aseguraremos parece atractivo. Estos son algunos aspectos a tener en cuenta:
* Windows Mixed Reality se ejecutará todas las aplicaciones 2D a una resolución fija y una resolución que equivale a 853 x 480 píxeles efectivos. Tenga en cuenta si el diseño debe perfeccionamiento a esta escala y revise la Guía de diseño siguiente para mejorar su experiencia en HoloLens e inmersivos.
* Windows Mixed Reality [no admite](app-model.md) vivas 2D. Si la funcionalidad básica es que muestra información sobre un icono dinámico, considere la posibilidad de mover esa información de vuelta en la aplicación o explorar [los iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>Factor de resolución y la escala de la vista de aplicación 2D

![Desde el diseño con capacidad de respuesta](images/scale-500px.png)

Windows 10 se mueve todo el diseño visual de píxeles real de la pantalla para **píxeles efectivos**. Esto significa que, a los desarrolladores diseñan su interfaz de usuario siguiendo las directrices de interfaz humana de Windows 10 para píxeles efectivos y escalado de Windows garantiza que los píxeles efectivos son el tamaño adecuado para su uso en todos los dispositivos, las resoluciones, PPP, etcetera. Vea este [lectura excelente en MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) para obtener más información, así como esto [compilación presentación](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Incluso con la capacidad única de colocar las aplicaciones en el mundo en un intervalo de distancias, se recomiendan las distancias de visualización de TV similares para generar el mejor legibilidad y la interacción con el gesto de mirada /. Por este motivo, una pizarra virtual en el hogar de realidad mixta mostrará su vista plana de UWP en:

**1280 x 720, 150% ppp** (píxeles efectivos 853 x 480)

Esta resolución tiene varias ventajas:
* Este diseño píxel efectivo tendrá sobre la misma densidad de información como una tableta o escritorio pequeña.
* Asigna los PPP fijo y los píxeles efectivos para aplicaciones UWP que se ejecutan en Xbox One, permitir experiencias de conexión directa entre dispositivos.
* Este tamaño se ve bien al escalar a través de nuestro intervalo de funcionamiento distancias para las aplicaciones del mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>Prácticas recomendadas de diseño de interfaz de vista de aplicación 2D

**Hacer:**
* Siga el [directrices de interfaz humana (HIG) de Windows 10](https://dev.windows.com/design) para los estilos, los tamaños de fuente y tamaño de botón. HoloLens realizará el trabajo para asegurarse de que su aplicación tendrá patrones de aplicaciones compatibles, los tamaños de texto legible y ajuste de tamaño de destino apropiado de posicionamiento.
* Asegúrese de la siguiente interfaz de usuario los procedimientos recomendados para [diseño dinámico](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) para tener un aspecto óptimo en de HoloLen solución exclusivo y PPP.
* Use las recomendaciones de tema de color "light" de Windows.

**No:**
* Cambiar la interfaz de usuario demasiado drásticamente cuando en realidad mixta, para asegurarse de que los usuarios tienen una experiencia familiar dentro y fuera de los auriculares.

### <a name="understand-the-app-model"></a>Entender el modelo de aplicación

El [modelo de aplicación](app-model.md) para realidad mixta está diseñada para usar el hogar Mixed Reality, que muchas aplicaciones se encuentran juntos. Piense en esto como el equivalente de realidad mixta del escritorio, donde se ejecutan muchas aplicaciones 2D a la vez. Esto tiene implicaciones sobre el ciclo de vida de aplicación, mosaicos y otras características clave de la aplicación.

### <a name="app-bar-and-back-button"></a>Barra de la aplicación y el botón Atrás

Vistas de 2D se representan con una barra de la aplicación por encima de su contenido. La barra de la aplicación tiene dos puntos de personalización específicos de la aplicación:

**Título:** muestra el *displayname* del icono asociado a la instancia de aplicación

**Botón Atrás:** provoca la *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* evento cuando se presiona. Visibilidad del botón Atrás se controla mediante  *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.

![Aplicación de interfaz de usuario de la barra en la vista de la aplicación 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Aplicación de interfaz de usuario de la barra en la vista de la aplicación 2D*

### <a name="test-your-2d-apps-design"></a>Probar el diseño de la aplicación 2D

Es importante probar la aplicación para asegurarse de que el texto es legible, los botones son como destino y la aplicación global parece correcta. También puede [probar](testing-your-app-on-hololens.md) en escritorio auriculares, un HoloLens, un emulador o un dispositivo táctil con la resolución que se establece en 1280 x 720 @150%.

## <a name="new-input-possibilities"></a>Nuevas posibilidades de entrada

HoloLens usa sensores avanzados profundidad para ver el mundo y ver los usuarios. Esto permite que los gestos de mano avanzadas como [bloom](gestures.md#bloom) y [pulsar en el aire](gestures.md#air-tap). Micrófonos eficaz también habilitar [experiencias de voz](voice-input.md).

Con auriculares de escritorio, los usuarios pueden usar los controladores de movimiento para apuntar a las aplicaciones y realizar acciones. También puede usar un controlador para juegos, seleccionar objetos con su mirada.

Windows se encarga de todo de esta complejidad para las aplicaciones UWP, traducir los [que mirar](gaze.md), gestos, voz y movimiento de entrada de controlador a [eventos de puntero](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) que abstraen el mecanismo de entrada. Por ejemplo, un usuario tiene puede hacer un punteo aire con la mano o extraído de la selección del desencadenador en un controlador de movimiento, pero las aplicaciones 2D no es necesario saber dónde proviene la entrada, sólo verán un toque 2D presione, como si se encuentra en una pantalla táctil.

Estos son los conceptos y escenarios de alto nivel que debe comprender para la entrada cuando lleva su aplicación para UWP a HoloLens:
* [Observación](gaze.md) se convierte en eventos de mantener el mouse, que pueden desencadenar inesperadamente menús, controles flotantes u otros elementos de interfaz de usuario que emerja acaba por gazing alrededor de la aplicación.
* Mirada no es tan preciso como entrada del mouse. Use el tamaño apropiado posicionamiento destinos para HoloLens, similar a las aplicaciones móviles de toque. Son especialmente difíciles interactuar con elementos pequeños cerca de los bordes de la aplicación.
* Los usuarios deben cambiar los modos de entrada para ir desde el desplazamiento al método de arrastrar para dos dedos panorámica. Si la aplicación se ha diseñado para la entrada táctil, considere la posibilidad de garantizar que ninguna funcionalidad principal está bloqueada detrás de panorámica de dos dedos. Si es así, considere la posibilidad de tener mecanismos de entrada alternativos, como botones que pueden iniciar panorámica de dos dedos. Por ejemplo, la aplicación mapas puede usar el zoom con dos dedos panorámica, pero tiene un signo más, menos y gira el botón para simular las mismas interacciones de zoom con clics únicos.

[Entrada de voz](voice-input.md) es una parte fundamental de la experiencia de realidad mixta. Hemos habilitado todos la speech API que se encuentran en fortalecer Cortana al usar auriculares de Windows 10.

## <a name="publish-and-maintain-your-universal-app"></a>Publicar y mantener su aplicación Universal

Una vez que la aplicación está en funcionamiento, empaquetar la aplicación a [enviarla a la Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](app-model.md)
* [Gaze](gaze.md)
* [Gesto](gestures.md)
* [Controladores de movimiento](motion-controllers.md)
* [Voz](voice-input.md)
* [Envío de una aplicación a la Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
