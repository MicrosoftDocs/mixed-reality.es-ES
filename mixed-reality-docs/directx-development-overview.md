---
title: Información general sobre el desarrollo nativo
description: Cree un motor de realidad mixta basado en DirectX mediante las API de realidad mixta de Windows directamente.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, representación holográfica, nativa, aplicación nativa, WinRT, aplicación WinRT, API de plataforma, motor personalizado, middleware
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160001"
---
# <a name="native-development-overview"></a>Información general sobre el desarrollo nativo

Las aplicaciones de Windows Mixed Reality usan las siguientes API para compilar experiencias de [realidad mixta](mixed-reality.md) para HoloLens y otros auriculares envolventes:

 - [Representación de holografías](rendering.md)
 - [Gaze](gaze-and-commit.md)
 - [Hacia](gaze-and-commit.md#composite-gestures)
 - [Controlador de movimiento](motion-controllers.md)
 - [Voz](voice-input.md)
 - [Asignación espacial](spatial-mapping.md)

Puede crear aplicaciones de realidad mixta mediante un motor 3D, como [Unity](unity-development-overview.md). O bien, puede codificar directamente las API de Windows Mixed Reality con DirectX 11 o DirectX 12. Si aprovecha la plataforma directamente, básicamente crea su propio middleware o marco. Las API de Windows admiten aplicaciones escritas tanto C++ en C#como en. Si usa C#, la aplicación puede aprovechar la biblioteca de software de código abierto de [SharpDX](https://sharpdx.org/) .

Windows Mixed Reality admite [dos tipos de aplicaciones](app-views.md):
* **Aplicaciones de realidad mixta** (UWP o Win32) que usan la [API de HOLOGRAPHICSPACE](getting-a-holographicspace.md) o la [API de OpenXR](openxr.md) para presentar una [vista envolvente](app-views.md) al usuario que rellena la pantalla del casco
* **aplicaciones 2D** (UWP) que usan DirectX, XAML u otro marco de trabajo para representar [vistas 2D](app-views.md#2d-views) en pizarras en la Página principal de Windows Mixed Reality

Las diferencias entre el desarrollo de DirectX para [vistas 2D y vistas envolventes](app-views.md) se refieren principalmente a la representación holográfica y la entrada espacial. El HWND de la aplicación de [UWP o el](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) HWND de la aplicación de Win32 son necesarios y permanecen en gran medida. Lo mismo se aplica a las API de WinRT que están disponibles para la aplicación. Sin embargo, debe usar un subconjunto diferente de estas API para aprovechar las características holográficas. Por ejemplo, el sistema intercambio y el marco actual se administran mediante el sistema para aplicaciones holográficas con el fin de habilitar un bucle de trama de predicción de supuestos.

## <a name="get-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

Para empezar a desarrollar aplicaciones de OpenXR para los auriculares de la realidad de HoloLens 2 o Windows, consulte [Cómo empezar a usar OpenXR Development](openxr-getting-started.md).

## <a name="get-started-with-winrt"></a>Introducción a WinRT

Para empezar a desarrollar aplicaciones envolventes:
* En el caso de las **aplicaciones UWP**, [use las plantillas de Visual Studio para crear un nuevo proyecto de UWP](creating-a-holographic-directx-project.md). En función del lenguaje, visual C++ o visual C#, busque las plantillas UWP en **Windows universal** > **Holographic**.
* En el caso de **las aplicaciones Win32**, [empiece en el ejemplo *BasicHologram* de Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Este paso es una excelente manera de obtener el código que necesita para agregar compatibilidad de representación holográfica a una aplicación o un motor existentes. El código y los conceptos se presentan en la plantilla de forma que resulte familiar a cualquier desarrollador de software interactivo en tiempo real.

En los temas siguientes se describen los requisitos básicos al agregar compatibilidad con Windows Mixed Reality a middleware basado en DirectX.

* [Crear un proyecto de DirectX holográfica](creating-a-holographic-directx-project.md): la plantilla de aplicación holográfica junto con la documentación muestra las diferencias en comparación con lo que se usa. También se describen los requisitos especiales para un dispositivo diseñado para funcionar mientras se encuentra en su cabeza.
* [Obtener un HolographicSpace](getting-a-holographicspace.md): primero debe crear un HolographicSpace que proporcione a la aplicación la secuencia de objetos HolographicFrame que representan cada posición de encabezado desde la que se va a representar.
* [Representar en DirectX](rendering-in-directx.md): dado que un intercambio holográfica tiene dos destinos de representación, debe realizar algunos cambios en la forma en que se representa la aplicación.
* [Sistemas de coordenadas en DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality aprende y actualiza su conocimiento del mundo a medida que el usuario se recorre. Esto proporciona sistemas de coordenadas espaciales que las aplicaciones usan para el entorno del usuario, incluidos los delimitadores espaciales y la fase espacial definida por el usuario.

## <a name="add-mixed-reality-capabilities-and-inputs"></a>Agregar capacidades y entradas de realidad mixta

Para proporcionar la mejor experiencia posible a los usuarios de la aplicación envolvente, debe admitir los siguientes bloques de creación de claves:

* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Sonido espacial](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)

Estas son otras características clave que usan muchas aplicaciones envolventes que también se exponen a las aplicaciones de DirectX:

* [Delimitadores espaciales compartidos en DirectX](shared-spatial-anchors-in-directx.md)
* [Entrada desde teclado, ratón y controlador en DirectX](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vea también
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
