---
title: Cámara de HoloLens en Unreal
description: Guía para usar la cámara de HoloLens en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, 3rd camera, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840124"
---
# <a name="hololens-camera-in-unreal"></a>Cámara de HoloLens en Unreal

## <a name="third-camera-mixed-reality-capture"></a>Captura de realidad mixta de la tercera cámara

La Captura de realidad mixta (MRC) de la tercera cámara se puede usar para representar una captura de realidad mixta desde la perspectiva de la cámara en el visor de HoloLens, en lugar de la perspectiva de las texturas del ojo.  Esto mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC. 

Para participar con MRC de tercera cámara, llama a SetEnabledMixedRealityCamera y ResizeMixedRealityCamera con las dimensiones de vídeo deseadas. 

![Tercera cámara](images/unreal-camera-3rd.PNG)

Después, graba un vídeo de MRC en el portal de dispositivos de HoloLens. 

## <a name="pv-camera"></a>Cámara de foto y vídeo

También se puede recuperar la textura de la cámara web en el juego en tiempo de ejecución.  Para obtener la textura de la cámara web en HoloLens, asegúrate de que la funcionalidad "Webcam" esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades). 

Para activar la cámara web en tiempo de ejecución, usa función StartCameraCapture.  Detén la captura con la función StopCameraCapture. 

![Inicio y detención de la cámara](images/unreal-camera-startstop.PNG)

Para representar la imagen de la cámara, crea primero una instancia de material dinámico basada en un material del proyecto.  En este caso, basada en un material denominado PVCamMat.  Define este valor en una variable con el tipo Material Instance Dynamic Object Reference (Referencia de objeto dinámico de instancia de material).  A continuación, establece el material del objeto en la escena que representará la fuente de la cámara en esta nueva instancia de material dinámico e inicia un temporizador que se usará para enlazar la imagen de la cámara con el material. 

![Representación de la cámara](images/unreal-camera-render.PNG)

Crea una nueva función para este temporizador, en este caso, MaterialTimer, y llama a GetARCameraImage para obtener la textura de la cámara web.  Si esta textura es válida, define un parámetro de textura en el sombreador para esta imagen.  De lo contrario, vuelve a iniciar el temporizador de materiales. 

![Textura de cámara](images/unreal-camera-texture.PNG)

El material debe tener un parámetro que coincida con el nombre de SetTextureParameterValue enlazado con una entrada de color para mostrar correctamente la imagen de la cámara. 

![Textura de cámara](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Consulta también
* [Cámara localizable](locatable-camera.md)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
