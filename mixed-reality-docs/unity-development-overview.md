---
title: Introducción al desarrollo de Unity
description: Empezar a crear aplicaciones de realidad mixta en Unity.
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, migración, funcionalidad, cámara, simulación, emulación, documentación
ms.openlocfilehash: 23b3d9a3fe419911e774722a7d2db6809c2955cf
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491099"
---
# <a name="unity-development-overview"></a>Introducción al desarrollo de Unity

La forma más rápida de crear una [aplicación de realidad mixta](app-views.md) es mediante [Unity](https://unity.com). Te recomendamos que dediques un tiempo a explorar los [tutoriales de Unity](https://unity3d.com/learn/tutorials). Si necesitas recursos, Unity cuenta con un [almacén de recursos](https://www.assetstore.unity3d.com/) completo. Una vez adquieras los conocimientos básicos sobre Unity, puede visitar los [tutoriales](tutorials.md) para aprender los aspectos específicas del desarrollo de realidad mixta con Unity. Asegúrate de visitar los [foros de la realidad mixta de Unity](https://forum.unity3d.com/forums/hololens.102/) para interactuar con el resto de la comunidad que crea aplicaciones de realidad mixta en Unity y encontrar soluciones a los problemas que puedas tener.

Para empezar a crear aplicaciones de realidad mixta con Unity, primero [instala las herramientas](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuevo proyecto de Unity con Mixed Reality Toolkit 

La forma más fácil de desarrollar aplicaciones en Unity es con Mixed Reality Toolkit. Te ayudará a definir la configuración del proyecto automáticamente y te proporcionará un conjunto de características de realidad mixta para acelerar el desarrollo. Consulta [Mixed Reality Toolkit v2](mrtk-getting-started.md) para obtener más información y comenzar a trabajar. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Migración de una aplicación existente de Unity a Windows Mixed Reality

Si tienes un proyecto de Unity existente que vas a migrar a Windows Mixed Reality, sigue los pasos que se indican en la [Guía de migración de Unity](porting-guides.md) para comenzar.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configuración de un nuevo proyecto de Unity para Windows Mixed Reality

Si quieres crear un nuevo proyecto de Unity sin importar Mixed Reality Toolkit, hay un pequeño conjunto de opciones de configuración de Unity que debes cambiar manualmente para Windows Mixed Reality. Se dividen en dos categorías: por proyecto y por escena. Consulta aquí una guía paso a paso para [configurar un nuevo proyecto de Unity para Windows Mixed Reality](Configure-Unity-Project.md).

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adición de características y entradas de realidad mixta

Una vez que hayas configurado MRTK V2 con el proyecto o hayas configurado el proyecto tal y como se describe anteriormente, los objetos de juego de Unity estándares (como la cámara) se iluminarán inmediatamente para iniciar una **experiencia sentada**, y la posición de la cámara se actualizará automáticamente a medida que el usuario mueva la cabeza en el mundo.

Para agregar compatibilidad con las características de Windows Mixed Reality, como [escenas espaciales](coordinate-systems.md#spatial-coordinate-systems), [gestos, controladores de movimiento](gestures-and-motion-controllers-in-unity.md) o [entrada de voz](voice-input-in-unity.md), se usan las API incorporadas directamente en Unity. 

En primer lugar, revisa las [escalas de experiencia](coordinate-systems.md) a las que se puede destinar la aplicación:
* Si estás pensando en crear una **experiencia de solo orientación** o una **experiencia sentada**, deberás establecer el tipo de espacio de seguimiento de Unity en [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (Estático).
* Si estás pensando en crear una **experiencia de pie** o una **experiencia de sala**, deberás asegurarte de que el tipo de espacio de seguimiento de Unity esté establecido correctamente en [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (Sala).
* Si estás pensando en crear una **experiencia de mundo** en HoloLens que permita a los usuarios moverse más allá de 5 metros, deberás usar el componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience).

Todos los bloques de creación básicos para las aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity. También están disponibles a través de Mixed Reality Toolkit.
* [Cámara](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [Gestos y controladores de movimiento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistencia](persistence-in-unity.md)
* [Sonido espacial](spatial-sound-in-unity.md)
* [Asignación espacial](spatial-mapping-in-unity.md)

Hay otras características clave que muchas aplicaciones de realidad mixta querrán usar y que también se exponen a las aplicaciones de Unity:
* [Experiencias compartidas](shared-experiences-in-unity.md)
* [Cámara localizable](locatable-camera-in-unity.md)
* [Punto de enfoque](focus-point-in-unity.md)
* [Pérdida de seguimiento](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ejecución del proyecto de Unity en un dispositivo real o simulado

Una vez que tengas el proyecto holográfico de Unity listo para las pruebas, el paso siguiente consiste en [exportar y compilar una solución de Visual Studio de Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Con esa solución de VS en mano, puedes ejecutar la aplicación de una de estas tres maneras, mediante un dispositivo real o simulado:
* [Implementación en un casco envolvente real de HoloLens o Windows Mixed Reality](using-visual-studio.md)
* [Implementación en el emulador de HoloLens](using-the-hololens-emulator.md)
* [Implementación en el simulador de casco envolvente de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentación de Unity

Además de esta documentación disponible en docs.microsoft.com, Unity instala la documentación de la funcionalidad de Windows Mixed Reality junto con Unity Editor. La documentación proporcionada por Unity incluye dos secciones independientes:
1. **Referencia de scripting de Unity**
    * Esta sección de la documentación contiene detalles de la API de scripting que proporciona Unity.
    * Es accesible desde Unity Editor a través de **Help > Scripting Reference** (Ayuda > Referencia de scripting).
2. **Manual de Unity**
    * Este manual está diseñado para ayudarte a aprender a usar Unity y ofrece técnicas básicas y avanzadas.
    * Se puede acceder a él desde Unity Editor a través de **Ayuda > Manual**.

## <a name="see-also"></a>Consulte también
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR Basics 100: introducción a Unity](holograms-100.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reproducción de Unity](unity-play-mode.md)
* [Guías de migración](porting-guides.md)
