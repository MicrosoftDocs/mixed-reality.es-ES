---
title: Introducción al desarrollo de Unity
description: Pasos para compilar para mezclar las aplicaciones de realidad en Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixto en realidad, desarrollo, introducción, nuevo proyecto, portabilidad, funcionalidad, cámara, simulación, emulación, documentación
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414520"
---
# <a name="unity-development-overview"></a>Introducción al desarrollo de Unity

La ruta de acceso más rápido a la compilación un [holográfica](app-views.md) con [Unity](http://aka.ms/HoloLensUnity). Se recomienda que se tome el tiempo para explorar el [tutoriales de Unity](https://unity3d.com/learn/tutorials). Si necesita activos, Unity tiene un completo [Asset Store](https://www.assetstore.unity3d.com/). Una vez que han generado un conocimiento básico de Unity, puede visitar el [tutoriales](tutorials.md) para obtener información sobre los aspectos específicos del desarrollo de realidad mixta con Unity. No olvide visitar la [foros Unity Mixed Reality](http://forum.unity3d.com/forums/hololens.102/) para ponerse en contacto con el resto de la Comunidad de creación de aplicaciones de realidad mixta en Unity y encontrar soluciones a problemas que pueden surgir.


Para empezar a crear aplicaciones de realidad mixta con Unity, en primer lugar [instalar las herramientas de](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuevo proyecto de Unity con el Kit de herramientas de realidad mixta 

La manera más fácil desarrollar en Unity es con la Ayuda del Kit de herramientas de realidad mixta. Lo ayudará a el programa de instalación con el proyecto automáticamente y proporcionan un conjunto de características de realidad mixta para acelerar el desarrollo. Consulte [v2 del Kit de herramientas de realidad mixta](mrtk-getting-started.md) para obtener más información y empezar a trabajar. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portar una aplicación existente de Unity a Windows Mixed Reality

Si tiene un proyecto de Unity existente que se va a portar a Windows Mixed Reality, continúe con el [Guía de migración de Unity](porting-guides.md) para empezar a trabajar.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurar el nuevo proyecto de Unity para Windows Mixed Reality

Si desea crear un nuevo proyecto de Unity sin importar el Kit de herramientas de realidad mixta, hay un pequeño conjunto de configuración de Unity, deberá cambiar manualmente para Windows Mixed Reality. Estos se dividen en dos categorías: por proyecto y por la escena. Vea aquí guía paso a paso para [configurar nuevo Unity Project para Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades de realidad mixta y entradas

Una vez que se ha configurado MRTK V2 con el proyecto o configurado el proyecto como se describió anteriormente, los objetos del juego Unity estándares (por ejemplo, la cámara) se iluminan inmediatamente para un **escala asentada experiencia**, con la posición de la cámara actualizada como el usuario mueve automáticamente su cabeza por el mundo.

Agregar compatibilidad con características de Windows Mixed Reality, tales como [fases espaciales](coordinate-systems.md#spatial-coordinate-systems), [gestos, los controladores de movimiento](gestures-and-motion-controllers-in-unity.md) o [entrada de voz](voice-input-in-unity.md) se logra mediante API integradas directamente en Unity. 

En primer lugar, revise el [experimentar escalas](coordinate-systems.md) que puede tener como destino la applicatioin:
* Si desea para compilar una **sólo orientación** o **escala asentada experiencia**, deberá establecer Unity de seguimiento de tipo de espacio para [estacionarios](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si desea para crear un **permanente escala** o **experiencia sala escala**, deberá asegurarse de Unity tipo de espacio de seguimiento se estableció correctamente en [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Si desea para crear un **escala world** experiencia en HoloLens que permite a los usuarios moverse más allá de 5 metros, deberá usar el [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Todos los bloques de creación para las aplicaciones de realidad mixta se exponen de manera coherente con otras API de Unity. También están disponibles a través del Kit de herramientas de realidad mixta.
* [Cámara](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [Los gestos y los controladores de movimiento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistencia](persistence-in-unity.md)
* [Sonido espacial](spatial-sound-in-unity.md)
* [Asignación espacial](spatial-mapping-in-unity.md)

Hay otras características clave que muchas aplicaciones querrá usar de la realidad mixta y que también se exponen a las aplicaciones de Unity:
* [Experiencias compartidas](shared-experiences-in-unity.md)
* [Cámara localizable](locatable-camera-in-unity.md)
* [Punto de enfoque](focus-point-in-unity.md)
* [Pérdida de seguimiento](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ejecuta el proyecto de Unity en un dispositivo real o simulado

Cuando esté satisfecho con el proyecto de Unity holográfico listo para las pruebas, el paso siguiente consiste en [exportar y generar una solución de Visual Studio de Unity](exporting-and-building-a-unity-visual-studio-solution.md).

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
* [La realidad mixta Toolkit v2](mrtk-getting-started.md)
* [MR Basics 100: introducción a Unity](holograms-100.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reproducción de Unity](unity-play-mode.md)
* [Guías de migración](porting-guides.md)
