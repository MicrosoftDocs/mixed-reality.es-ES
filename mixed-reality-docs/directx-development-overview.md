---
title: Introducción al desarrollo de DirectX
description: Creación de un motor de realidad mixta basada en DirectX utilizando directamente las API de Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Representación de DirectX, holográfica, aplicación nativa, nativo, WinRT, aplicación de WinRT, API, motor personalizado, de plataforma de middleware
ms.openlocfilehash: 047144cb8fcf158f74375e9ec69dca92a2a1cf01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598628"
---
# <a name="directx-development-overview"></a>Introducción al desarrollo de DirectX

Uso de aplicaciones de Windows Mixed Reality el [representación holográfica](rendering.md), [que mirar](gaze.md), [gesto](gestures.md), [controlador de movimiento](motion-controllers.md), [voz ](voice-input.md) y [asignación espacial](spatial-mapping.md) API para compilar [la realidad mixta](mixed-reality.md) experiencias para HoloLens e inmersivos. Puede crear aplicaciones de realidad mixta mediante un motor 3D, como [Unity](unity-development-overview.md), o bien puede usar las API de realidad mixta de Windows con DirectX 11. Tenga en cuenta que DirectX 12 no se admite actualmente. Si saca provecho de la plataforma directamente, estará básicamente creando su propio software intermedio o un marco de trabajo. Las API de Windows admiten las aplicaciones escritas en ambos C++ y C#. Si le gustaría utilizar C#, la aplicación puede aprovechar la [SharpDX](http://sharpdx.org/) biblioteca de software de código abierto.

Es compatible con Windows Mixed Reality [dos tipos de aplicaciones](app-views.md):
* **Mezclar las aplicaciones de realidad** (UWP o Win32), que usan el [HolographicSpace API](getting-a-holographicspace.md) para representar un [vista envolvente](app-views.md) al usuario que rellena la presentación de auriculares.
* **Aplicaciones 2D** (UWP), que usan DirectX, XAML u otros marcos de trabajo para representar [vistas 2D](app-views.md#2d-views) en tabletas táctiles en el inicio de Windows Mixed Reality.

Las diferencias entre el desarrollo de DirectX para [vistas 2D y envolventes](app-views.md) son principalmente relacionados con holográfica representación y entrada espacial. La aplicación UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) o HWND de la aplicación Win32 siguen siendo necesaria y no cambian en gran medida, como hacen las APIs WinRT disponibles para su aplicación. Sin embargo, utiliza un subconjunto diferente de estas API pueden aprovechar características holográficas. Por ejemplo, la cadena de intercambio está administrada por el sistema para las aplicaciones holográficas y trabajar con la API de HolographicSpace en lugar de DXGI que [presentan marcos](rendering-in-directx.md).

Para empezar a desarrollar aplicaciones envolventes:
* Para **aplicaciones para UWP**, [crear un nuevo proyecto UWP con las plantillas de Visual Studio](creating-a-holographic-directx-project.md). En función de su lenguaje, **Visual C++**  o **Visual C#** , encontrará las plantillas UWP en **Windows Universal**  >   **Holográfica**.
* Para **aplicaciones Win32**, [crear un nuevo proyecto de escritorio de Win32](creating-a-holographic-directx-project.md#creating-a-win32-project) y, a continuación, siga las instrucciones de Win32 el [obteniendo un HolographicSpace](getting-a-holographicspace.md) página para obtener un HolographicSpace.

Esto es una excelente manera de obtener el código que necesario para agregar compatibilidad con la representación holographic a una aplicación o un motor existente. Se presentan conceptos y código en la plantilla de forma que resultará familiar a cualquier desarrollador de software interactivo en tiempo real.

## <a name="getting-started"></a>Introducción

Los temas siguientes describen los requisitos básicos de cómo agregar compatibilidad con Windows Mixed Reality al middleware basado en DirectX:
* [Creación de un proyecto de DirectX holográfico](creating-a-holographic-directx-project.md): La plantilla de aplicación holográfica junto con la documentación le mostrará las diferencias entre lo que está acostumbrado a y los requisitos especiales introducidos por un dispositivo que se ha diseñado para funcionar mientras se apoya en la cabeza.
* [Obtener un HolographicSpace](getting-a-holographicspace.md): En primer lugar, deberá crear un HolographicSpace, que le proporcionarán la secuencia de objetos HolographicFrame que representan cada posición principal desde el que procesan de la aplicación.
* [Representación en DirectX](rendering-in-directx.md): Puesto que una cadena de intercambio holográfica tiene dos destinos de representación, es probable que deba realizar algunos cambios en la forma en la aplicación se representa.
* [Sistemas de coordenadas en DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality aprende y actualiza su comprensión del mundo, como los recorridos de usuario, que proporciona a los sistemas de coordenadas espaciales que las aplicaciones usan para razonar sobre el entorno del usuario, como delimitadores espaciales y fase de espacial definido del usuario.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades de realidad mixta y entradas

Para habilitar la mejor experiencia posible para los usuarios de las aplicaciones envolventes, querrá admitir los siguientes bloques de creación de claves:
* [Mirada, gestos y controladores de movimiento de DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)

Hay otras características clave que muchas aplicaciones envolventes querrá usar, que también se exponen a las aplicaciones DirectX:
* [Compartido espaciales delimitadores en DirectX](shared-spatial-anchors-in-directx.md)
* [Cámara localizable en DirectX](locatable-camera-in-directx.md)
* [Teclado, mouse y entrada del controlador de DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
