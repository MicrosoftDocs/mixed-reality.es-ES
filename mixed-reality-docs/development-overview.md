---
title: Información general sobre desarrollo
description: En este artículo se describen los bloques de creación básicos de desarrollo de una aplicación de Windows Mixed Reality.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Introducción, conceptos básicos, HoloLens, HoloLens 2, auriculares envolvente, Unity, Visual Studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873975"
---
# <a name="development-overview"></a>Información general sobre desarrollo

Las aplicaciones de realidad mixta se pueden desarrollar con diversas tecnologías de desarrollo.  HoloLens ejecuta aplicaciones que se compilan con el [plataforma universal de Windows](https://dev.windows.com/getstarted).  Los auriculares envolventes se ejecutan Plataforma universal de Windows aplicaciones, así como las aplicaciones Win32.
Al familiarizarse con las herramientas de middleware como Unity, puede empezar a crear experiencias de realidad mixta hoy mismo.  Aproveche el kit de [herramientas de realidad mixta](install-the-tools.md) de código abierto para empezar a trabajar rápidamente.
Los <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">servicios de realidad mixta</a>, como los delimitadores espaciales de <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure</a>, tienen SDK que se pueden integrar también en diversas tecnologías de desarrollador multiplataforma.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Conceptos básicos del desarrollo de realidad mixta

Las experiencias de [realidad mixta](mixed-reality.md) están habilitadas por nuevas características de Windows para el reconocimiento del entorno. Estas permiten a los desarrolladores colocar un [holograma](hologram.md) en el mundo real y a los usuarios desplazarse por los mundos digitales literalmente caminando. 

Estos son los bloques de compilación principales para el desarrollo de la realidad mixta:

<table>
<tr>
<th>Entrada</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> <a href="gaze.md">Mirada con la cabeza</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Mirada con ojo</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Manos y <a href="gestures.md">gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Controlador para juegos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controladores de movimiento</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percepción y características espaciales</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordenadas del mundo</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Sonido espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Asignación espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



El modelo de interacción básica para [HoloLens](hololens-hardware-details.md) es [mirada](gaze.md), [gesto](gestures.md) y [voz](voice-input.md), que a veces se conoce como *GGV*. Los [cascos envolventes de Windows Mixed Reality](immersive-headset-hardware-details.md) también usan la mirada y la voz, pero utilizan [controladores de movimiento](motion-controllers.md) en lugar de gestos.


Todos los dispositivos de realidad mixta basados en Windows se benefician del ecosistema de entrada disponible para Windows, incluido el mouse, el teclado, los controladores de juegos, etc. Con HoloLens, los [accesorios de hardware](hardware-accessories.md) se conectan a través de Bluetooth. Con cascos envolventes, los accesorios se conectan al equipo host a través de Bluetooth, USB y otros protocolos admitidos.

Las características de reconocimiento del entorno como [coordenadas](coordinate-systems.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md) proporcionan las funcionalidades necesarias para combinar la realidad. La asignación espacial es exclusiva de HoloLens, y permite que los hologramas interactúen con el usuario y el mundo físico en torno a él. Los sistemas de coordenadas permiten que el movimiento del usuario afecte al movimiento en el mundo digital.

Los [hologramas](hologram.md) se componen de luz y sonido, que dependen de la [representación holográfica](rendering.md). Entender la experiencia de selección de ubicación y de persistencia, tal como se muestra en la [página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) (a veces denominada el "shell"), es una excelente manera de afianzarte en la experiencia del usuario.

## <a name="tools-for-developing-for-mixed-reality"></a>Herramientas para desarrollar la realidad mixta

Las herramientas que utilices dependerán del [estilo de aplicación](app-views.md) que desees compilar.
* [Las aplicaciones con una vista 2D](building-2d-apps.md) aprovechan las herramientas para compilar aplicaciones de la plataforma universal de Windows adecuadas para entornos como Windows Phone, PC y tabletas. Estas aplicaciones se experimentan como proyecciones 2D que se colocan en la página principal de Windows Mixed Reality y pueden funcionar en varios tipos de dispositivo (incluidos el teléfono y el PC).
* Las aplicaciones envolventes y holográficas necesitan herramientas diseñadas para aprovechar las ventajas de las API de Windows Mixed Reality. [Recomendamos el uso de Unity](unity-development-overview.md) para compilar aplicaciones de realidad mixta. Los desarrolladores interesados en compilar su propio motor pueden [utilizar DirectX y otras API de Windows](directx-development-overview.md).

Independientemente del tipo de aplicación que estés compilando, estas herramientas facilitarán tu experiencia en el desarrollo de aplicaciones:
* [Visual Studio y Windows SDK](using-visual-studio.md)
* [Portal de dispositivos Windows](using-the-windows-device-portal.md)
* [Emulador de HoloLens](using-the-hololens-emulator.md) (El emulador de HoloLens 2 estará disponible próximamente)
* [Simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Criterios de calidad de aplicaciones](app-quality-criteria.md)

## <a name="see-also"></a>Vea también
* [Instalación de las herramientas](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Servicios de realidad mixta</a>
* [Tutoriales de realidad mixta](tutorials.md)
* [Proyectos de código abierto](open-source-projects.md)
* [MR Basics 100: introducción a Unity](holograms-100.md)
* [Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Envío de una aplicación a la tienda Windows](submitting-an-app-to-the-microsoft-store.md)
