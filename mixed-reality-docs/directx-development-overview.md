---
title: Información general sobre el desarrollo de DirectX
description: Compilar un motor de realidad mixta basado en DirectX mediante las API de realidad mixta de Windows directamente.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, representación holográfica, nativa, aplicación nativa, WinRT, aplicación WinRT, API de plataforma, motor personalizado, middleware
ms.openlocfilehash: 58b311038633dc325cc2c5425fd09b9a0192b161
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861702"
---
# <a name="directx-development-overview"></a>Información general sobre el desarrollo de DirectX


Las aplicaciones de Windows Mixed Reality usan las API de [representaciónde holográficas](rendering.md), [miradas](gaze.md), [gestos](gestures.md), [controladores de movimiento](motion-controllers.md), [voz](voice-input.md) y [mapas espaciales](spatial-mapping.md) para crear experiencias de [realidad mixtas](mixed-reality.md) para HoloLens y auriculares envolventes. Puede crear aplicaciones de realidad mixtas mediante un motor 3D, como [Unity](unity-development-overview.md), o puede codificar directamente las API de Windows Mixed Reality con DirectX 11 o DirectX 12. Si está aprovechando la plataforma directamente, básicamente creará su propio middleware o marco. Las API de Windows admiten aplicaciones C++ escritas C#tanto en como en. Si decide usar C#, la aplicación puede aprovechar la biblioteca de software de código abierto de [SharpDX](http://sharpdx.org/) .


Windows Mixed Reality admite [dos tipos de aplicaciones](app-views.md):
* **Aplicaciones de realidad mixta** (UWP o Win32) que usan la [API HolographicSpace](getting-a-holographicspace.md) para presentar una [vista envolvente](app-views.md) al usuario que rellena la pantalla del casco.
* **aplicaciones 2D** (UWP) que usa DirectX, XAML u otros marcos de trabajo para representar [vistas 2D](app-views.md#2d-views) en tabletas en la Página principal de Windows Mixed Reality.


Las diferencias entre el desarrollo de DirectX para las [vistas 2D y las vistas](app-views.md) envolventes están relacionadas principalmente con la representación holográfica y la entrada espacial. El [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) de la aplicación de UWP o el HWND de la aplicación de Win32 son necesarios y, en gran medida, son las mismas que las API de WinRT disponibles para la aplicación. Sin embargo, debe usar un subconjunto diferente de estas API para aprovechar las características holográficas. Por ejemplo, la cadena de intercambio la administra el sistema para Holographic appslications. Trabajará con la API de HolographicSpace en lugar de DXGI para [presentar](rendering-in-directx.md)fotogramas.

Para empezar a desarrollar aplicaciones envolventes:
* En el caso de las **aplicaciones UWP**, [cree un nuevo proyecto de UWP con las plantillas de Visual Studio](creating-a-holographic-directx-project.md). En función del lenguaje, **el C++ objeto visual** o el **objeto visual C#** , puede encontrar las plantillas UWP en **Windows universal** > **Holographic**.
* En el caso de **las aplicaciones Win32**, [empiece en el ejemplo *BasicHologram* de Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Esta es una excelente manera de obtener el código que necesita para agregar compatibilidad de representación holográfica a una aplicación o un motor existentes. El código y los conceptos se presentan en la plantilla de forma que resulte familiar a cualquier desarrollador de software interactivo en tiempo real.


## <a name="getting-started"></a>Introducción

En los temas siguientes se describen los requisitos básicos para agregar compatibilidad con Windows Mixed Reality a middleware basado en DirectX:

* [Creación de un proyecto de DirectX holográfica](creating-a-holographic-directx-project.md): La plantilla de aplicación holográfica junto con la documentación muestra las diferencias entre lo que se usa, así como los requisitos especiales introducidos por un dispositivo diseñado para funcionar mientras se encuentra en su cabeza.
* [Obtención de un HolographicSpace](getting-a-holographicspace.md): En primer lugar, deberá crear un HolographicSpace que proporcionará a la aplicación la secuencia de objetos HolographicFrame que representan cada posición principal de la que se va a representar.
* [Representación en DirectX](rendering-in-directx.md): Puesto que una cadena de intercambio holográfica tiene dos destinos de representación, deberá realizar algunos cambios en la forma en que se representa la aplicación.
* [Sistemas de coordenadas en DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality aprende y actualiza su conocimiento del mundo a medida que el usuario se recorre. Esto proporciona sistemas de coordenadas espaciales que las aplicaciones usan para el entorno del usuario, incluidos los delimitadores espaciales y la fase espacial definida por el usuario.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades y entradas de realidad mixta

Para habilitar la mejor experiencia posible para los usuarios de la appslication envolvente, querrá admitir los siguientes bloques de creación de claves:

* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)


Hay otras características clave que muchas aplicaciones envolventes desearán usar y que también se exponen a las aplicaciones de DirectX:

* [Delimitadores espaciales compartidos en DirectX](shared-spatial-anchors-in-directx.md)
* [Entrada desde teclado, ratón y controlador en DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
