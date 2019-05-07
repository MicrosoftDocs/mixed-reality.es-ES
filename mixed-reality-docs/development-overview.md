---
title: Información general sobre desarrollo
description: En este artículo se describe los bloques de creación básicos de desarrollo de una aplicación de Windows Mixed Reality.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: al obtener iniciados, conceptos básicos, HoloLens, HoloLens 2, auriculares envolventes, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873975"
---
# <a name="development-overview"></a>Información general sobre desarrollo

Mediante una variedad de tecnologías de desarrollo, se pueden desarrollar aplicaciones de realidad mixta.  HoloLens ejecuta aplicaciones que se generan con el [Universal Windows Platform](https://dev.windows.com/getstarted).  Inmersivos ejecutan aplicaciones de la plataforma Universal de Windows, así como aplicaciones de Win32.
Obteniendo familiarizado con las herramientas de software intermedio como Unity, puede empezar a compilar experiencias de realidad mixta hoy.  Aprovechar el código abierto [Kit de herramientas de realidad mixta](install-the-tools.md) para empezar a trabajar rápidamente.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixto servicios realidad</a>, tales como <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, tienen los SDK que pueden integrar en diversas tecnologías de desarrollo multiplataforma.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Aspectos básicos del desarrollo de realidad mixta

[La realidad mixta](mixed-reality.md) experiencias están habilitadas por nuevas características de Windows para ver una descripción del entorno. Estas permiten a los desarrolladores colocar un [holograma](hologram.md) en el mundo real, y permitir a los usuarios desplazarse por los mundos digitales recorriendo sobre literalmente. 

Estos son los bloques de creación fundamentales para el desarrollo de realidad mixta:

<table>
<tr>
<th>Entrada</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> <a href="gaze.md">Mirada HEAD</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Mirada ojo</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Manos / <a href="gestures.md">gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controladores de movimiento</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percepción y las características espaciales</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordenadas universales</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Sonido espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Asignación espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



El modelo de interacción básica para [HoloLens](hololens-hardware-details.md) es [que mirar](gaze.md), [gesto](gestures.md), y [voz](voice-input.md), que a veces se conoce como *GGV* . [Inmersivos Windows Mixed Reality](immersive-headset-hardware-details.md) también use mirada y voz, pero el intercambio [motion controladores](motion-controllers.md) para los gestos.


Todos los dispositivos de realidad mixta basada en Windows se benefician del ecosistema de entrada disponible para Windows, incluido el mouse, teclado, configuración de los controles y mucho más. Con HoloLens, [accesorios de hardware](hardware-accessories.md) están conectados a través de Bluetooth. Con inmersivos, Accesorios conexión con el equipo host a través de Bluetooth, USB y otros protocolos admitidos.

Las características de comprensión del entorno como [coordenadas](coordinate-systems.md), [sonido espacial](spatial-sound.md), y [asignación espacial](spatial-mapping.md) proporcionan las capacidades necesarias para combinar la realidad. Asignación espacial es exclusivo de HoloLens y permite hologramas interactuar con el usuario y el mundo físico en torno a ellas. Sistemas de coordenadas permiten el desplazamiento del usuario influir en movimiento en el mundo digital.

[Hologramas](hologram.md) se realizan de la luz y sonido, que se basan en [representación holográfica](rendering.md). Descripción de la experiencia de selección de ubicación y de persistencia, como se muestra en el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (a veces denominado el "shell") es una excelente manera de corriente electrostática en la experiencia del usuario.

## <a name="tools-for-developing-for-mixed-reality"></a>Herramientas para desarrollar la realidad mixta

Las herramientas que utilice dependerá de la [estilo de aplicación](app-views.md) desea compilar.
* [Aplicaciones con una vista 2D](building-2d-apps.md) Aproveche las herramientas para compilar aplicaciones de la plataforma Universal de Windows adecuado para entornos como tabletas, PC y Windows Phone. Estas aplicaciones tienen experiencia como 2D proyecciones que se colocan en el inicio de Windows Mixed Reality y pueden funcionar en varios tipos de dispositivo (incluyendo phone y PC).
* Las aplicaciones envolventes y holográficas necesitan herramientas diseñadas para aprovechar las ventajas de las API de Windows Mixed Reality. Nos [recomienda usar Unity](unity-development-overview.md) para compilar aplicaciones de realidad mixta. Los desarrolladores interesados en crear su propio motor pueden [utilizar DirectX y otras API de Windows](directx-development-overview.md).

Independientemente del tipo de aplicación que está compilando, estas herramientas facilitarán su experiencia de desarrollo de aplicaciones:
* [Visual Studio y el SDK de Windows](using-visual-studio.md)
* [Portal de dispositivos Windows](using-the-windows-device-portal.md)
* [Emulador de HoloLens](using-the-hololens-emulator.md) (emulador de HoloLens 2 próximamente)
* [Simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Criterios de calidad de aplicaciones](app-quality-criteria.md)

## <a name="see-also"></a>Vea también
* [Instalación de las herramientas](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Servicios de realidad mixta</a>
* [Tutoriales de realidad mixtas](tutorials.md)
* [Proyectos de código abierto](open-source-projects.md)
* [MR Basics 100: introducción a Unity](holograms-100.md)
* [Directrices para compatibilidad de hardware mínimas PC de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Envío de una aplicación para el Store de Windows](submitting-an-app-to-the-microsoft-store.md)
