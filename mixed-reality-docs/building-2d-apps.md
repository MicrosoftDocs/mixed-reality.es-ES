---
title: Actualización de aplicaciones para UWP en 2D para la realidad mixta
description: En este artículo se describe la actualización de la aplicación de Plataforma universal de Windows de 2D existente para que se ejecute en HoloLens y en los auriculares de Windows Mixed Reality.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicación 2D, UWP, aplicación plana, HoloLens, auriculares envolvente, modelo de aplicación, botón atrás, barra de la aplicación, PPP, resolución, escala
ms.openlocfilehash: 46d2a9ca044dee977faecc84d610dc0811a4bfb7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436991"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Actualización de aplicaciones para UWP en 2D para la realidad mixta

Windows Mixed Reality permite a los usuarios ver los hologramas como si fueran más adecuados en su mundo físico o digital. En su núcleo, tanto HoloLens como los equipos de escritorio que se adjuntan a los accesorios de auriculares envolvente son dispositivos de Windows 10. Esto significa que puede ejecutar prácticamente todas las aplicaciones de Plataforma universal de Windows (UWP) en el almacén como aplicaciones 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creación de una aplicación para UWP en 2D para la realidad mixta

El primer paso para llevar una aplicación 2D a los auriculares de realidad mixta es hacer que la aplicación se ejecute como una aplicación 2D estándar en el monitor de escritorio.

### <a name="building-a-new-2d-uwp-app"></a>Creación de una nueva aplicación para UWP en 2D

Para compilar una nueva aplicación de 2D para Mixed Reality, solo tiene que compilar una aplicación estándar de 2D Plataforma universal de Windows (UWP). No es necesario ningún otro cambio en la aplicación para que esa aplicación se ejecute como una pizarra en la realidad mixta.

Para empezar a crear una aplicación de UWP en 2D, consulte el artículo [creación de su primera aplicación](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) .

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Incorporación de una aplicación de la tienda 2D existente a UWP

Si ya tiene una aplicación de Windows en 2D en la tienda, primero debe asegurarse de que tiene como destino la Plataforma universal de Windows de Windows 10 (UWP). Estos son los posibles puntos de partida que puede tener con la aplicación de la tienda hoy:
<br>

|  Punto de partida  |  Destino de la plataforma de manifiesto AppX  |  ¿Cómo se convierte en universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifiesto de aplicación de Silverlight |  [Migrar a WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone universal 8,1  |  8,1 manifiesto de AppX que no incluye el destino de la plataforma  |  [Migrar la aplicación a la Plataforma universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Tienda Windows 8  |  8 manifiesto AppX que no incluye el destino de la plataforma  |  [Migrar la aplicación a la Plataforma universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Tienda Windows 8,1 universal  |  8,1 manifiesto de AppX que no incluye el destino de la plataforma  |  [Migrar la aplicación a la Plataforma universal de Windows](https://msdn.microsoft.com/library/mt148501.aspx) | 

Si tiene una aplicación de Unity de 2D compilada actualmente como una aplicación de Win32 (el destino de compilación "equipo, Mac & Linux independiente"), puede dirigirse a la realidad mixta cambiando Unity al destino de compilación "Plataforma universal de Windows".

Hablaremos sobre las formas en que puede restringir la aplicación específicamente a HoloLens mediante la familia de dispositivos Windows. Holographic [a continuación](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Ejecutar la aplicación en 2D en un casco con Windows Mixed Reality

Si ha implementado la aplicación 2D en el equipo de escritorio en el que está desarrollando e intentando usarlo en el monitor, ya está listo para probarlo en un casco de escritorio envolvente.

Solo tiene que ir al menú Inicio dentro del casco de realidad mixta e iniciar la aplicación desde allí. El shell de escritorio y el shell holográfica comparten el mismo conjunto de aplicaciones UWP, por lo que la aplicación ya debe estar presente una vez que se haya implementado desde Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Establecer como destino los auriculares que se envolverán y HoloLens

Enhorabuena. La aplicación está usando Windows 10 Plataforma universal de Windows (UWP).

La aplicación ahora es capaz de ejecutarse en los dispositivos Windows de hoy en día, como escritorio, móviles, Xbox, la realidad mixta de Windows y los auriculares que se envolverán, y HoloLens, así como los futuros dispositivos Windows. Sin embargo, para tener como destino realmente todos esos dispositivos, deberá asegurarse de que la aplicación esté destinada a la familia de dispositivos Windows. universal.

### <a name="change-your-device-family-to-windowsuniversal"></a>Cambiar la familia de dispositivos a Windows. universal

Ahora vamos a pasar al manifiesto de AppX para asegurarse de que la aplicación para UWP de Windows 10 pueda ejecutarse en HoloLens:
* Abra el archivo de solución de la aplicación con **Visual Studio** y navegue hasta el manifiesto del paquete de la aplicación.
* Haga clic con el botón derecho en el archivo **Package. appxmanifest** de la solución y vaya a **Ver código** .<br>
  ![package. appxmanifest en Explorador de soluciones](images/openappxmanifest-500px.png)<br>
* Asegúrese de que la plataforma de destino es Windows. universal en la sección de dependencias.
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Guardar!

Si no usa Visual Studio para su entorno de desarrollo, puede abrir **AppXManifest. XML** en el editor de texto de su elección para asegurarse de que tiene como destino **Windows. universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Ejecutar en el emulador de HoloLens

Ahora que la aplicación para UWP tiene como destino "Windows. universal", vamos a compilar la aplicación y ejecutarla en el [emulador de HoloLens](using-the-hololens-emulator.md).
* Asegúrese de que ha [instalado el emulador de HoloLens](install-the-tools.md).
* En Visual Studio, seleccione la configuración de compilación **x86** para la aplicación.

  ![configuración de compilación x86 en Visual Studio](images/x86setting.png)<br>
* Seleccione **emulador de HoloLens** en el menú desplegable destino de implementación.

  ![Emulador de HoloLens en la lista de destinos de implementación](images/deployemulator-500px.png)<br>
* Seleccione **Depurar > iniciar depuración** para implementar la aplicación e iniciar la depuración.
* El emulador se iniciará y ejecutará la aplicación.
* Con un teclado, un mouse o una controladora Xbox, coloca la aplicación en el mundo para iniciarla.

  ![Emulador de HoloLens cargado con un ejemplo de UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Pasos siguientes

En este momento, pueden producirse dos cosas:
1. La aplicación mostrará la pantalla de presentación y comenzará a ejecutarse después de colocarla en el emulador. Increíble!
2. O bien, después de ver una animación de carga para un holograma de 2D, la carga se detendrá y solo verá la aplicación en la pantalla de presentación. Esto significa que se produjo un error y que se realizará una investigación más para entender cómo hacer que la aplicación cobre vida en la realidad mixta.

Para llegar a la parte inferior de lo que puede estar causando que la aplicación para UWP no se inicie en HoloLens, tendrá que depurar.

### <a name="running-your-uwp-app-in-the-debugger"></a>Ejecutar la aplicación para UWP en el depurador

Estos pasos le guiarán a través de la depuración de la aplicación para UWP mediante el depurador de Visual Studio.
* Si todavía no lo ha hecho, abra la solución en Visual Studio. Cambie el destino al **emulador de HoloLens** y la configuración de compilación a **x86**.
* Seleccione **Depurar > iniciar depuración** para implementar la aplicación e iniciar la depuración.
* Coloque la aplicación en el mundo con el mouse, el teclado o la controladora Xbox.
* Visual Studio ahora debería interrumpir en algún lugar del código de la aplicación.
  - Si la aplicación no se bloquea inmediatamente o se interrumpe en el depurador debido a un error no controlado, siga un paso de prueba de las características principales de la aplicación para asegurarse de que todo esté en funcionamiento y en funcionamiento. Es posible que vea errores como los que se muestran a continuación (excepciones internas que se están controlando). Para asegurarse de que no se pierdan los errores internos que afectan a la experiencia de la aplicación, ejecute las pruebas automatizadas y las pruebas unitarias para asegurarse de que todo se comporta según lo esperado.

![El emulador de HoloLens se cargó con un ejemplo de UWP que muestra una excepción del sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Actualizar la interfaz de usuario

Ahora que la aplicación para UWP se está ejecutando en auriculares más envolventes y/o HoloLens como un holograma de 2D, vamos a asegurarnos de que parece bonito. Estos son algunos aspectos que se deben tener en cuenta:
* Windows Mixed Reality ejecutará todas las aplicaciones 2D con una resolución fija y un PPP equivalentes a los píxeles efectivos de 853x480. Considere la posibilidad de que su diseño necesite perfeccionarse a esta escala y revise las instrucciones de diseño que se indican a continuación para mejorar su experiencia en HoloLens y en auriculares de gran tamaño.
* Windows Mixed Reality [no admite](app-model.md) mosaicos dinámicos 2D. Si la funcionalidad principal muestra información sobre un icono dinámico, considere la posibilidad de mover esa información de nuevo a la aplicación o explore los [iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>resolución de vista de aplicación 2D y factor de escala

![Del diseño con capacidad de respuesta](images/scale-500px.png)

Windows 10 mueve todo el diseño visual de píxeles de pantalla reales a **píxeles efectivos**. Esto significa que los desarrolladores diseñan su interfaz de usuario siguiendo las directrices de la interfaz de usuario de Windows 10 para píxeles efectivos y el escalado de Windows garantiza que los píxeles efectivos son el tamaño adecuado para la facilidad de uso en dispositivos, resoluciones, PPP, etc. Vea esta [excelente lectura en MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) para obtener más información, así como esta [presentación de compilación](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Incluso con la capacidad exclusiva para colocar aplicaciones en su mundo a una gran distancia, se recomiendan distancias de visualización similares a las de la televisión para obtener la mejor legibilidad y la interacción con la función de toque y gesto. Por eso, una pizarra virtual en la Página principal de la realidad mixta mostrará la vista plana de UWP en:

**1280x720, 150% ppp** (píxeles efectivos 853x480)

Esta resolución tiene varias ventajas:
* Este diseño de píxeles efectivo tendrá aproximadamente la misma densidad de información que una tableta o un pequeño escritorio.
* Coincide con el PPP fijo y los píxeles efectivos de las aplicaciones UWP que se ejecutan en Xbox One, lo que permite experiencias sin problemas en todos los dispositivos.
* Este tamaño es bueno cuando se escala a través de nuestra gama de distancias de funcionamiento para aplicaciones del mundo.

### <a name="2d-app-view-interface-design-best-practices"></a>procedimientos recomendados de diseño de la interfaz de vista de aplicaciones 2D

**No**
* Siga las [directrices de la interfaz de usuario de Windows 10 (hig)](https://dev.windows.com/design) para los estilos, tamaños de fuente y tamaños de botón. HoloLens realizará el trabajo para asegurarse de que la aplicación tendrá patrones de aplicación compatibles, tamaños de texto legible y un tamaño de destino de aciertos adecuado.
* Asegúrese de que la interfaz de usuario sigue las prácticas recomendadas para que el [diseño responda](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) mejor a la resolución y el PPP únicos de HoloLen.
* Use las recomendaciones de tema de color "Light" desde Windows.

**No:**
* Cambie la interfaz de usuario demasiado drásticamente cuando esté en realidad mixta para asegurarse de que los usuarios tengan una experiencia familiar dentro y fuera del casco.

### <a name="understand-the-app-model"></a>Descripción del modelo de aplicación

El [modelo de aplicación](app-model.md) de la realidad mixta está diseñado para usar la Página principal de realidad mixta, donde muchas aplicaciones se encuentran juntas. Piense en esto como el equivalente de realidad mixta del escritorio, donde se ejecutan muchas aplicaciones 2D a la vez. Esto tiene implicaciones en el ciclo de vida de la aplicación, los mosaicos y otras características clave de la aplicación.

### <a name="app-bar-and-back-button"></a>Barra de aplicación y botón atrás

las vistas 2D se decoran con una barra de la aplicación por encima de su contenido. La barra de la aplicación tiene dos puntos de personalización específicos de la aplicación:

**Título:** muestra el nombre para *Mostrar del icono* asociado a la instancia de la aplicación.

**Botón atrás:** genera el evento *[solicitado](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* cuando se presiona. *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* controla la visibilidad del botón atrás.

![interfaz de usuario de la barra de la aplicación en la vista de aplicación 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interfaz de usuario de la barra de aplicación en la vista de aplicación 2D*

### <a name="test-your-2d-apps-design"></a>Prueba del diseño de la aplicación 2D

Es importante probar la aplicación para asegurarse de que el texto se puede leer, de que los botones son de destino y de que la aplicación global tiene el aspecto correcto. Puede [probar](testing-your-app-on-hololens.md) en un auricular de escritorio, HoloLens, un emulador o un dispositivo táctil con la resolución establecida en 1280x720 @150%.

## <a name="new-input-possibilities"></a>Nuevas posibilidades de entrada

HoloLens usa sensores avanzados de profundidad para ver el mundo y ver los usuarios. Esto permite gestos de mano avanzados como el [floración](system-gesture.md#bloom) y [el toque de aire](gaze-and-commit.md#composite-gestures). Los micrófonos eficaces también habilitan las [experiencias de voz](voice-input.md).

Con los auriculares de escritorio, los usuarios pueden usar los controladores de movimiento para apuntar a las aplicaciones y tomar medidas. También pueden usar un controlador de juegos, orientados a objetos con miras.

Windows se encarga de toda esta complejidad en el caso de las aplicaciones UWP, la traducción de los movimientos de [miración](gaze-and-commit.md), gestos, voz y del controlador de movimiento a [eventos de puntero](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) que abstraen el mecanismo de entrada. Por ejemplo, un usuario puede haber realizado una pulsación aérea con su mano o haber extraído el desencadenador SELECT en un controlador de movimiento, pero las aplicaciones 2D no necesitan saber de dónde procede la entrada, sino que solo ven una prensa táctil 2D, como si estuvieran en una pantalla táctil.

Estos son los conceptos y escenarios de alto nivel que debe comprender para la entrada al llevar su aplicación de UWP a HoloLens:
* [Mira](gaze-and-commit.md) los eventos de mantener el mouse, que pueden desencadenar inesperadamente menús, controles flotantes u otros elementos de la interfaz de usuario para que aparezcan simplemente Gazing en torno a la aplicación.
* Mira fijamente no es tan preciso como la entrada del mouse. Use los objetivos de aciertos de tamaño adecuado para HoloLens, similares a las aplicaciones móviles táctiles. Los elementos pequeños cerca de los bordes de la aplicación son especialmente difíciles de interactuar con ellos.
* Los usuarios deben cambiar los modos de entrada para pasar de desplazamiento a dos movimientos de movimiento. Si la aplicación se ha diseñado para la entrada táctil, considere la posibilidad de asegurarse de que no se bloquee ninguna funcionalidad principal detrás de dos dedos. Si es así, considere la posibilidad de tener mecanismos de entrada alternativos, como botones que puedan iniciar dos movimientos de dedo. Por ejemplo, la aplicación de mapas puede hacer zoom con dos movimientos panorámicos, pero tiene un botón más, menos y girar para simular las mismas interacciones de zoom con un solo clic.

La [entrada de voz](voice-input.md) es una parte fundamental de la experiencia de realidad mixta. Se han habilitado todas las API de voz que se encuentran en Windows 10 al encender Cortana al usar un casco.

## <a name="publish-and-maintain-your-universal-app"></a>Publicar y mantener la aplicación universal

Una vez que la aplicación esté en funcionamiento, empaquete la aplicación para [enviarla a la Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Consulta también
* [Modelo de aplicaciones](app-model.md)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Controladores de movimiento](motion-controllers.md)
* [Entrada de voz](voice-input.md)
* [Envío de aplicaciones a Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
