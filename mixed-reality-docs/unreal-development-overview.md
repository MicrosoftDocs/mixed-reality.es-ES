---
title: Introducción al desarrollo con Unreal
description: Información general sobre el desarrollo para realidad mixta con Unreal Engine 4
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851569"
---
# <a name="unreal-development-overview"></a>Introducción al desarrollo con Unreal

Ahora, Unreal Engine 4 es totalmente compatible con el desarrollo para dispositivos con Windows Mixed Reality (VR) y HoloLens 2 (AR). Si no estás familiarizado con el desarrollo con Unreal, la página <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Introducción a Unreal Engine 4</a> te resultará ideal para explorarlo. Si necesitas recursos, Unreal dispone de un <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> completo. 

Una vez que hayas adquirido un conocimiento básico del desarrollo con Unreal, consulta el tutorial de la sección siguiente para obtener información sobre cómo compilar y ejecutar aplicaciones en HoloLens. No olvides visitar los <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">foros de realidad mixta de Unreal</a> para interactuar con la comunidad que compila aplicaciones de realidad mixta en Unreal. Es un lugar idóneo en el que buscar soluciones a los problemas con los que puedes encontrarte.

## <a name="tutorial"></a>Tutorial

Aprende a [compilar e implementar una aplicación de ajedrez sencilla](unreal-uxt-ch1.md) para HoloLens 2 con nuestro tutorial detallado. En este tutorial se usa el complemento UX Tools para desarrollar aplicaciones con componentes de experiencia de usuario interactivos, como un botón y un manipulador. Para obtener más información sobre el complemento UX Tools, consulta la siguiente sección sobre MRTK. 

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality Toolkit para Unreal

[Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) es un conjunto de componentes, en forma de complementos, ejemplos y documentación, diseñado para acelerar el desarrollo de aplicaciones de realidad mixta con Unreal Engine. El primer componente que se publica como parte de este kit de herramientas es [UX Tools para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), un complemento que se puede agregar al proyecto de HoloLens 2 para proporcionar características de experiencia de usuario para aplicaciones de HoloLens 2. La documentación de Mixed Reality Toolkit y UX Tools para Unreal se puede encontrar en sus respectivos repositorios de GitHub. 

## <a name="performance"></a>Rendimiento

Una aplicación de HoloLens 2 debe ejecutarse a 60 fotogramas por segundo para que los hologramas presenten estabilidad y capacidad de respuesta. Para lograrlo en la aplicación, te recomendamos que sigas nuestras [recomendaciones de rendimiento para Unreal](performance-recommendations-for-unreal.md). 

## <a name="guides-to-specific-features"></a>Guías para características específicas

Para obtener información sobre cómo usar características específicas en Unreal, consulta las guías siguientes: 
* [Seguimiento de las manos](unreal-hand-tracking.md)
* [Seguimiento de los ojos](unreal-gaze-input.md)
* [Asignación espacial](unreal-spatial-mapping.md)
* [Delimitadores espaciales](unreal-spatial-anchors.md)
* [Entrada de voz](unreal-voice-input.md)
* [Cámara de HoloLens](unreal-hololens-camera.md)
* [Códigos QR](unreal-qr-codes.md)

## <a name="supported-features"></a>Funciones admitidas

| Característica de HoloLens 2 | Versión anterior de Unreal Engine admitida |
| ----------- | ----------- |
| Compatibilidad con ARM64 | 4.23 |
| Streaming desde un equipo | 4.23 |
| Asignación espacial | 4.23 |
| Seguimiento de manos y articulaciones | 4.23 |
| Seguimiento de los ojos | 4.23 |
| Entrada de voz | 4.23 |
| Delimitadores espaciales | 4.23 |
| Acceso a la cámara | 4.23 |
| Códigos QR | 4.23 |
| Audio espacial | 4.23 |
| Compatibilidad con la pantalla de espectador para streaming | 4.24 |
| LSR plana por streaming | 4.24 |
| Las aplicaciones de muestra ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) y [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Modo multivista móvil: resultados de rendimiento de 60 fps | 4.25 |
| Representación de tercera cámara | 4.25 |
| Streaming desde una aplicación de escritorio empaquetada | 4.25 |
| Azure Spatial Anchors para HoloLens 2 (beta) | 4.25 |
| Compatibilidad con OpenXR (beta) | 4.25 |
| Compatibilidad con UX Tools (0.8) | 4.25 |
| Tutoriales y documentación para desarrolladores | 4.25 |

## <a name="see-also"></a>Consulta también
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Documentación de Unreal para streaming e implementación en el emulador y el dispositivo</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Instrucciones de rendimiento de Unreal para dispositivos móviles</a>
