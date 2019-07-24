---
title: Introducción al desarrollo de Unity
description: Introducción a la creación de aplicaciones de realidad mixta en Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, portabilidad, capacidad, cámara, simulación, emulación, documentación
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414520"
---
# <a name="unity-development-overview"></a>Introducción al desarrollo de Unity

La ruta más rápida para compilar una [aplicación de realidad mixta](app-views.md) es con [Unity](http://aka.ms/HoloLensUnity). Se recomienda dedicar tiempo a explorar los tutoriales de [Unity](https://unity3d.com/learn/tutorials). Si necesita recursos, Unity tiene un almacén de [recursos](https://www.assetstore.unity3d.com/)completo. Una vez que haya integrado una comprensión básica de Unity, puede visitar los [tutoriales](tutorials.md) para conocer los aspectos específicos del desarrollo de la realidad mixta con Unity. No olvide visitar los foros de la [realidad mixta de Unity](http://forum.unity3d.com/forums/hololens.102/) para interactuar con el resto de la comunidad que crea aplicaciones de realidad mixta en Unity y encontrar soluciones a los problemas con los que puede encontrarse.


Para empezar a crear aplicaciones de realidad mixta con Unity, [Instale primero las herramientas](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuevo proyecto de Unity con el kit de herramientas de realidad mixta 

La forma más fácil de desarrollar en Unity es con la ayuda del kit de herramientas de realidad mixta. Le ayudará a configurar con Project automáticamente y proporcionará un conjunto de características de realidad mixta para acelerar el desarrollo. Consulte [Mixed Reality Toolkit V2](mrtk-getting-started.md) para obtener más información y comenzar. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Trasladar una aplicación existente de Unity a Windows Mixed Reality

Si tiene un proyecto de Unity existente que va a migrar a Windows Mixed Reality, siga la guía de [portabilidad de Unity](porting-guides.md) para comenzar.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configuración del nuevo proyecto de Unity para Windows Mixed Reality

Si desea crear un nuevo proyecto de Unity sin importar el kit de herramientas de realidad mixta, hay un pequeño conjunto de opciones de Unity que debe cambiar manualmente para Windows Mixed Reality. Estas se dividen en dos categorías: por proyecto y por escena. Consulte aquí para obtener una guía paso a paso para [configurar un nuevo proyecto de Unity para Windows Mixed Reality](Configure-Unity-Project.md) .

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades y entradas de realidad mixta

Una vez que haya configurado MRTK V2 con el proyecto, o haya configurado el proyecto como se describió anteriormente, los objetos de juego de Unity estándar (como la cámara) se encenderán inmediatamente para una **experiencia de escalado original**, con la posición de la cámara actualizada automáticamente como el el usuario mueve su encabezado a través del mundo.

La adición de compatibilidad con las características de Windows Mixed Reality, como las [fases espaciales](coordinate-systems.md#spatial-coordinate-systems), [los gestos, los controladores de movimiento](gestures-and-motion-controllers-in-unity.md) o la [entrada de voz](voice-input-in-unity.md) se consigue mediante las API integradas directamente en Unity. 

En primer lugar, revise las escalas de la [experiencia](coordinate-systems.md) que puede tener como destino su applicatioin:
* Si está pensando en crear una experiencia **solo de orientación** o **de escalado ajustada**, deberá establecer el tipo de espacio de seguimiento de Unity en [estacionaria](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si está pensando en crear una experiencia de escalado **permanente** o **de escalado de habitación**, deberá asegurarse de que el tipo de espacio de seguimiento de Unity se establece correctamente en [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si está pensando en crear una experiencia de **escala mundial** en HoloLens que permita a los usuarios moverse más allá de 5 metros, deberá usar el componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) .

Todos los bloques de creación principales para aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity. También están disponibles a través del kit de herramientas de realidad mixta.
* [Cámara](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [Gestos y controladores de movimiento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistence](persistence-in-unity.md)
* [Sonido espacial](spatial-sound-in-unity.md)
* [Asignación espacial](spatial-mapping-in-unity.md)

Hay otras características clave que muchas aplicaciones de realidad mixta desearán usar y que también se exponen a las aplicaciones de Unity:
* [Experiencias compartidas](shared-experiences-in-unity.md)
* [Cámara localizable](locatable-camera-in-unity.md)
* [Punto de enfoque](focus-point-in-unity.md)
* [Pérdida de seguimiento](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ejecución del proyecto de Unity en un dispositivo real o simulado

Una vez que tenga el proyecto Holographic Unity listo para las pruebas, el paso siguiente consiste en [exportar y compilar una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Con esa solución de VS en mano, puede ejecutar la aplicación de una de estas tres maneras, mediante un dispositivo real o simulado:
* [Implementación en un casco real de HoloLens o Windows Mixed Reality](using-visual-studio.md)
* [Implementación en el emulador de HoloLens](using-the-hololens-emulator.md)
* [Implementar en el simulador de auriculares envolvente de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentación de Unity

Además de esta documentación disponible en el centro de desarrollo de Windows, Unity instala la documentación de la funcionalidad de Windows Mixed Reality junto con el editor de Unity. La documentación proporcionada por Unity incluye dos secciones independientes:
1. **Referencia de scripting de Unity**
    * Esta sección de la documentación contiene detalles de la API de scripting que proporciona Unity.
    * Accesible desde el editor de Unity a través de la **ayuda > referencia** de scripting
2. **Manual de Unity**
    * Este manual está diseñado para ayudarle a aprender a usar Unity, desde técnicas básicas y avanzadas.
    * Accesible desde el editor de Unity a través de la **ayuda > manual**

## <a name="see-also"></a>Vea también
* [Kit de herramientas de realidad mixta V2](mrtk-getting-started.md)
* [MR Basics 100: introducción a Unity](holograms-100.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reproducción de Unity](unity-play-mode.md)
* [Guías de portabilidad](porting-guides.md)
