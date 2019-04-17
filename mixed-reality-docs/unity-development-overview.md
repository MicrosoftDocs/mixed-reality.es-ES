---
title: Introducción al desarrollo de Unity
description: Pasos para compilar para mezclar las aplicaciones de realidad en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mixto en realidad, desarrollo, introducción, nuevo proyecto, portabilidad, funcionalidad, cámara, simulación, emulación, documentación
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605673"
---
# <a name="unity-development-overview"></a>Introducción al desarrollo de Unity

La ruta de acceso más rápido a la compilación un [holográfica](app-views.md) con [Unity](http://aka.ms/HoloLensUnity). Se recomienda que dedique un tiempo para explorar el [tutoriales de Unity](https://unity3d.com/learn/tutorials). Si necesita activos, Unity tiene un completo [Asset Store](https://www.assetstore.unity3d.com/). Una vez que han generado un conocimiento básico de Unity, puede visitar el [Mixed Reality Academy](academy.md) para obtener información sobre los aspectos específicos del desarrollo de realidad mixta con Unity. No olvide visitar la [foros Unity Mixed Reality](http://forum.unity3d.com/forums/hololens.102/) para ponerse en contacto con el resto de la Comunidad de creación de aplicaciones de realidad mixta en Unity y encontrar soluciones a problemas que pueden surgir.

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portar una aplicación existente de Unity a Windows Mixed Reality

Si tiene un proyecto de Unity existente que se va a portar a Windows Mixed Reality, continúe con el [Guía de migración de Unity](porting-guides.md) para empezar a trabajar.

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Configuración de un nuevo proyecto de Unity para Windows Mixed Reality

Para empezar a crear aplicaciones de realidad mixta con Unity, en primer lugar [instalar las herramientas de](install-the-tools.md). Si le como destino inmersivos Windows Mixed Reality, en lugar de HoloLens, necesitará una versión especial de Unity por ahora.

Si acaba de crear un nuevo proyecto de Unity, hay un pequeño conjunto de configuración de Unity, deberá cambiar para Windows Mixed Reality, dividida en dos categorías: por proyecto y por la escena.

### <a name="per-project-settings"></a>Configuración por proyecto

Para tener como destino Windows Mixed Reality, primero debe configurar su proyecto de Unity para exportar como una aplicación plataforma Universal de Windows:
1. Seleccione **archivo > configuración de compilación...**
2. Seleccione **Universal Windows Platform** en la plataforma de lista y haga clic en **Cambiar plataforma**
3. Establecer **SDK** a **10 Universal**
4. Establecer **dispositivo de destino** a **cualquier dispositivo** para admitir inmersivos o cambie a **HoloLens**
5. Establecer **tipo de compilación** a **D3D**
6. Establecer **UWP SDK** a **instalada más reciente**

A continuación, es necesario informar a Unity que se debe crear la aplicación que estamos intentando exportar una [vista envolvente](app-views.md) en lugar de una vista 2D. Para hacerlo habilitando "Realidad Virtual admite":
1. Desde el **configuración de compilación...**  ventana abierta **configuración del Reproductor...**
2. Seleccione el **configuración de plataforma Universal de Windows** ficha
3. Expanda el **configuración XR** grupo
4. En el **XR configuración** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar el **dispositivos de realidad Virtual** lista.
5. En el **XR configuración** grupo, confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible. (Esto puede aparecer como "Windows Holographic" en versiones anteriores de Unity)

Ahora puede hacer la aplicación básica representación holográfica y entrada espacial. Para ir más allá y aprovechar las ventajas de cierta funcionalidad, la aplicación debe declarar las capacidades adecuadas en su manifiesto. Las declaraciones del manifiesto se pueden realizar en Unity, por lo que se incluyen en cada exportación proyecto posterior. La configuración se encuentran en **configuración del Reproductor > configuración de plataforma Universal de Windows > configuración de publicación > capacidades**. Las capacidades para habilitar las API de Unity usados para Mixed Reality aplicables son:

|  Capacidad  |  API que requieren la capacidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a [asignación espacial](spatial-mapping.md) mallas en HoloLens)&mdash;*ninguna funcionalidad necesaria para seguimiento espacial general de los auriculares* | 
|  WebCam  |  PhotoCapture y VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (cuando la captura de audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y utilizar el Profiler de Unity) | 

**Configuración de calidad de Unity**

![Configuración de calidad de Unity](images/unityqualitysettings-350px.png)<br>
*Configuración de calidad de Unity*

HoloLens tiene una GPU de la clase mobile. Si la aplicación está destinada a HoloLens, querrá la configuración de calidad optimizada para rendimiento más rápido para asegurarse de que mantenemos la velocidad de fotogramas completa:
1. Seleccione **Editar > configuración del proyecto > calidad**
2. Seleccione el **desplegable** bajo el **Windows Store** logotipo y seleccione **Fastest**. Sabrá que la configuración se aplique correctamente cuando la casilla de la columna de Windows Store y **Fastest** fila es verde.

### <a name="per-scene-settings"></a>Configuración por la escena

**Configuración de la cámara de Unity**

![Configuración de la cámara de Unity](images/unitycamerasettings.png)<br>
*Configuración de la cámara de Unity*

Una vez que habilite la casilla "Compatible de realidad Virtual", la [Unity cámara](camera-in-unity.md) identificadores de componente [head seguimiento y la representación estereoscópica](rendering.md). No hay ninguna necesidad reemplazarla con una cámara personalizada para hacerlo.

Si la aplicación está destinada específicamente a HoloLens, hay algunas opciones de configuración que deben cambiarse para optimizar la muestra de transparente del dispositivo, por lo que se mostrará la aplicación a través en el mundo físico:
1. En el **jerarquía**, seleccione el **cámara principal**
2. En el **Inspector** del panel, establezca la transformación **posición** a **0, 0, 0** para que la ubicación de la cabeza a los usuarios que se inicie en el origen del mundo de Unity.
3. Cambio **borrar las marcas de** a **Color sólido**.
4. Cambiar el **en segundo plano** al color **RGBA 0,0,0,0**. Negro se representa como transparente en HoloLens.
5. Cambio **cerca de recorte planos -** a la [HoloLens recomendadas](camera-in-unity.md#clip-planes) 0,85 (metros).

Si elimina y creación de una cámara nueva, asegúrese de que la cámara es **etiquetada** como **MainCamera**.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades de realidad mixta y entradas

Una vez que ha configurado el proyecto como se describió anteriormente, los objetos del juego Unity estándares (por ejemplo, la cámara) se iluminan inmediatamente para un **escala asentada experiencia**, con la posición de la cámara actualizada automáticamente como el usuario se desplaza su cabeza por el mundo.

Agregar compatibilidad con características de Windows Mixed Reality como [fases espaciales](coordinate-systems.md#spatial-coordinate-systems), [gestos, los controladores de movimiento](gestures-and-motion-controllers-in-unity.md) o [entrada de voz](voice-input-in-unity.md) se logra mediante API integradas directamente en Unity.

Debe ser el primer paso Revisar el [experimentar escalas](coordinate-systems.md) que puede tener como destino la aplicación:
* Si desea para compilar una **sólo orientación** o **escala asentada experiencia**, deberá establecer Unity de seguimiento de tipo de espacio para [estacionarios](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si desea para crear un **permanente escala** o **experiencia sala escala**, deberá asegurarse de Unity tipo de espacio de seguimiento se estableció correctamente en [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si desea para crear un **escala world** experiencia en HoloLens, permite que los usuarios moverse más allá de 5 metros, deberá usar el [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Todos los bloques de creación para las aplicaciones de realidad mixta se exponen de manera coherente con otras API de Unity:
* [Cámara](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [Los gestos y los controladores de movimiento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistencia](persistence-in-unity.md)
* [Sonido espacial](spatial-sound-in-unity.md)
* [Asignación espacial](spatial-mapping-in-unity.md)

Hay otras características clave que muchas aplicaciones de realidad mixta querrá usar, que también se exponen a las aplicaciones de Unity:
* [Experiencias compartidas](shared-experiences-in-unity.md)
* [Cámara localizable](locatable-camera-in-unity.md)
* [Punto de enfoque](focus-point-in-unity.md)
* [Pérdida de seguimiento](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ejecuta el proyecto de Unity en un dispositivo real o simulado

Cuando esté satisfecho con el proyecto de Unity holográfico listo para probar, el paso siguiente consiste en [exportar y generar una solución de Visual Studio de Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Con esa solución frente a mano, puede, a continuación, ejecutar la aplicación en uno de tres maneras, mediante un dispositivo real o simulado:
* [Implementar en un auricular envolvente HoloLens o Windows Mixed Reality real](using-visual-studio.md)
* [Implementar en el emulador de HoloLens](using-the-hololens-emulator.md)
* [Implementar en el simulador de Windows Mixed Reality auriculares envolventes](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentación de Unity

Además de esta documentación disponible en el centro de desarrollo de Windows, Unity instala la documentación para la funcionalidad de Windows Mixed Reality junto con el Editor de Unity. El Unity proporciona documentación incluye dos secciones separadas:
1. **Referencia de scripting de Unity**
    * En esta sección de la documentación contiene detalles de la API de scripting que Unity proporciona.
    * Accesible desde el Editor de Unity a través de **Ayuda > referencia de Scripting**
2. **Manual de Unity**
    * Este manual está diseñado para ayudarle a aprender cómo usar Unity, desde las técnicas básicas y avanzadas.
    * Accesible desde el Editor de Unity a través de **Ayuda > Manual**

## <a name="see-also"></a>Vea también
* [Conceptos básicos de MR 100: Introducción a Unity](holograms-100.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportar y creación de una solución de Visual Studio de Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Usar el espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de juego de Unity](unity-play-mode.md)
* [Guías de migración](porting-guides.md)
