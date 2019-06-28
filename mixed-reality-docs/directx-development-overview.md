---
title: Introducción al desarrollo de DirectX
description: Creación de un motor de realidad mixta basada en DirectX utilizando directamente las API de Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Representación de DirectX, holográfica, aplicación nativa, nativo, WinRT, aplicación de WinRT, API, motor personalizado, de plataforma de middleware
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414384"
---
# <a name="directx-development-overview"></a>Introducción al desarrollo de DirectX


Las aplicaciones de Windows Mixed Reality utilizan el [representación holográfica](rendering.md), [que mirar](gaze.md), [gesto](gestures.md), [controlador de movimiento](motion-controllers.md), [voz](voice-input.md), y [asignación espacial](spatial-mapping.md) API para compilar [la realidad mixta](mixed-reality.md) experiencias para HoloLens e inmersivos. Puede crear aplicaciones de realidad mixta mediante un motor 3D, como [Unity](unity-development-overview.md), o se puede programar directamente a las API de realidad mixta de Windows con DirectX 11 o DirectX 12. Si saca provecho de la plataforma directamente, estará básicamente creando su propio software intermedio o un marco de trabajo. Las API de Windows admiten aplicaciones escritas en ambos C++ y C#. Si opta por usar C#, la aplicación puede aprovechar la [SharpDX](http://sharpdx.org/) biblioteca de software de código abierto.


Es compatible con Windows Mixed Reality [dos tipos de aplicaciones](app-views.md):
* **Mixto aplicaciones de realidad** (Win32 o UWP) que usan el [HolographicSpace API](getting-a-holographicspace.md) para representar un [vista envolvente](app-views.md) al usuario que rellena la presentación de auriculares.
* **Aplicaciones 2D** (UWP) que usan otros marcos, XAML o DirectX para representar [vistas 2D](app-views.md#2d-views) en tabletas táctiles en el inicio de Windows Mixed Reality.


Las diferencias entre el desarrollo de DirectX para [vistas 2D y envolventes](app-views.md) son principalmente relacionados con holográfica representación y entrada espacial. La aplicación de UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) o HWND de la aplicación Win32 son necesario y no cambian en gran medida, como hacen las APIs WinRT disponibles para su aplicación. Sin embargo, debe usar un subconjunto diferente de estas API pueden aprovechar características holográficas. Por ejemplo, la cadena de intercambio es administrada por el sistema para appslications holográfica. Trabajar con la API de HolographicSpace en lugar de DXGI que [presentan marcos](rendering-in-directx.md).

Para empezar a desarrollar aplicaciones envolventes:
* Para **aplicaciones para UWP**, [crear un nuevo proyecto UWP con las plantillas de Visual Studio](creating-a-holographic-directx-project.md). En función de su lenguaje, **Visual C++**  o **Visual C#** , puede encontrar las plantillas UWP en **Windows Universal**  >   **Holográfica**.
* Para **aplicaciones Win32**, [iniciar desde el *BasicHologram* ejemplo Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Esto es una excelente manera de obtener el código que necesita para agregar compatibilidad con la representación holographic a una aplicación o un motor existente. Se presentan conceptos y código en la plantilla de forma que resultará familiar a cualquier desarrollador de software interactivo en tiempo real.


## <a name="getting-started"></a>Introducción

Los temas siguientes describen los requisitos básicos de cómo agregar compatibilidad con Windows Mixed Reality al middleware basado en DirectX:

* [Creación de un proyecto de DirectX holográfico](creating-a-holographic-directx-project.md): La plantilla de aplicación holográfica junto con la documentación muestra las diferencias entre lo que está acostumbrado, así como los requisitos especiales introducidos por un dispositivo que se ha diseñado para funcionar mientras se apoya en la cabeza.
* [Obtener un HolographicSpace](getting-a-holographicspace.md): En primer lugar, deberá crear un HolographicSpace que le proporcionará la secuencia de objetos HolographicFrame que representan cada posición principal desde el que procesan de la aplicación.
* [Representación en DirectX](rendering-in-directx.md): Puesto que una cadena de intercambio holográfica tiene dos destinos de representación, deberá realizar algunos cambios en la forma en la aplicación se representa.
* [Sistemas de coordenadas en DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality aprende y actualiza su comprensión del mundo, como el usuario le guía en torno a. Se trata de sistemas de coordenadas espaciales que las aplicaciones utilizan para razonar sobre el entorno del usuario, incluyendo los delimitadores espaciales y el usuario define fase espacial.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades de realidad mixta y entradas

Para habilitar la mejor experiencia posible para los usuarios de su appslication envolvente, querrá admitir los siguientes bloques de creación de claves:

* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)


Hay otras características clave que le convenga usar muchas aplicaciones envolventes que también se exponen a las aplicaciones DirectX:

* [Delimitadores espaciales compartidos en DirectX](shared-spatial-anchors-in-directx.md)
* [Cámara localizable en DirectX](locatable-camera-in-directx.md)
* [Entrada desde teclado, ratón y controlador en DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
