---
title: Introducción al desarrollo con Unreal
description: Información general sobre el desarrollo para realidad mixta con Unreal Engine 4
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 3e3862bd701d6e873f623abc9f9cda0b3085e753
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330162"
---
# <a name="unreal-development-overview"></a>Introducción al desarrollo con Unreal

La introducción a <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="los documentos de realidad mixta"> aplicaciones de realidad mixta</a> es una gran tarea. Los nuevos conceptos, las plataformas y el hardware de vanguardia pueden parecer un obstáculo. Sin embargo, si es un desarrollador de Unreal, tiene suerte. Ahora se incluye compatibilidad con los <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="documentos de Windows Mixed Reality">Windows Mixed Reality</a> (VR) y con los <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="documentos de HoloLens 2">HoloLens 2</a> (AR) en <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="las notas de la versión de Unreal Engine 4.25 más reciente</a>la versión más reciente">. En esta actualización se incluye:
* Compatibilidad del complemento UX Tools de Mixed Reality
* Compatibilidad con OpenXR
* Control remoto de la aplicación desde una aplicación de escritorio
* Un mejor rendimiento
* Captura de realidad mixta
* Compatibilidad inicial con Azure Spatial Anchors

Si no está familiarizado con el desarrollo en Unreal, no empiece a ciegas. Explore la <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">serie de tutoriales</a> de Unreal para ponerse al día y buscar recursos y soporte técnico en <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a> de Unreal y en los <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">foros</a> de la realidad mixta. Estos recursos son vínculos a la comunidad de creadores y solucionadores de problemas en el mercado de realidad mixta de hoy en día.

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality Toolkit para Unreal

[Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) es un conjunto de componentes diseñados para acelerar el desarrollo en Unreal. Cada componente incluye complementos, ejemplos y documentación para configurar experiencias envolventes. 

[UX Tools para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) es el primer componente que se va a publicar y actualmente solo se admite en HoloLens 2. El complemento del componente incluye código, planos técnicos y recursos de ejemplo de las características comunes de UX, como:
* Simulación de entrada
* Actor de interacción con la mano
* Componente de botón presionable
* Componente de manipulador
* Componente de seguimiento del comportamiento

Puede profundizar en el repositorio GitHub de [UX Tools para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) para obtener información detallada sobre la característica e información sobre cómo configurar el proyecto.

## <a name="tutorial"></a>Tutorial

Crear algo con sus propias manos es la mejor manera de aprender una nueva habilidad. Aprender a [compilar e implementar una aplicación de ajedrez sencilla](unreal-uxt-ch1.md) para HoloLens 2 con el complemento UX Tools es una excelente manera de empezar. 

La serie completa de tutoriales proporciona un contacto práctico con escenarios y componentes de UX interactivos comunes. Trabajará en la configuración del proyecto, agregará interacciones a la escena y lo implementará en un dispositivo o emulador. Lo único que necesita es Windows 10, un emulador y Visual Studio 2019.


## <a name="performance"></a>Rendimiento

El desarrollo para la realidad mixta incluye puntos de control de rendimiento que dependen de la plataforma. Una aplicación de HoloLens 2 debe ejecutarse a 60 fotogramas por segundo para que los hologramas presenten estabilidad y capacidad de respuesta. Afortunadamente, Unreal proporciona [recomendaciones de rendimiento](performance-recommendations-for-unreal.md) para lograrlo en sus aplicaciones.

## <a name="guides-to-specific-features"></a>Guías para características específicas

Hay varias características clave del desarrollo de la realidad mixta que nuestra serie de tutoriales no cubre. Consulte las siguientes guías para obtener más información y aplicaciones prácticas: 
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
