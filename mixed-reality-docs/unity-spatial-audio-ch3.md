---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y cospatiala el audio del vídeo.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182752"
---
# <a name="spatializing-audio-from-a-video"></a>Espacialización del audio de un vídeo
En este tercer capítulo del módulo de audio espacial de los tutoriales de Unity de HoloLens 2, hará lo siguiente:
* Importar un vídeo y agregar un reproductor de vídeo
* Reproducir el vídeo en un Quadrangle
* Enrute el audio del vídeo al Quadrangle y Spatial el audio

## <a name="import-a-video-and-add-a-video-player"></a>Importar un vídeo y agregar un reproductor de vídeo

Arrastre un archivo de vídeo al panel **proyecto** del proyecto de Unity. Puede usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) desde el proyecto de ejemplo de audio espacial.

![Carpeta assets con vídeo](images/spatial-audio/assets-folder-with-video.png)

Ajustar la configuración de calidad en el clip de vídeo puede garantizar una reproducción fluida de HoloLens 2. Haga clic en el archivo de vídeo en el panel **proyecto** . Después, en el panel **Inspector** del archivo de vídeo, invalide la configuración de las aplicaciones de la tienda Windows y:
* Habilitar **Transcode**
* Establecer **códec** en H264
* Establecer el **modo de velocidad de bits** en baja
* Establecer **calidad espacial** en calidad espacial media

Después de estos ajustes, el panel del **Inspector** para el archivo de vídeo tendrá el siguiente aspecto:

![Panel de propiedades de vídeo](images/spatial-audio/video-property-pane.png)

A continuación, agregue un objeto de **reproductor de vídeo** a la **jerarquía** haciendo clic con el botón derecho en el panel de **jerarquías** y eligiendo **vídeo > reproductor de**vídeo:

![Reproductor de vídeo en jerarquía](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>Reproducir vídeo en un Quadrangle
El objeto **reproductor de vídeo** necesita un objeto de juego con textura en el que representar el vídeo. En primer lugar, agregue un **cuádruple** a la **jerarquía** ; para ello, haga clic con el botón derecho en el panel de **jerarquías** y elija **objeto 3D > cuádruple**:

![Agregar cuatro a la jerarquía](images/spatial-audio/add-quad-to-hierarchy.png)

Para asegurarse de que el **cuádruple** aparece delante del usuario cuando se inicia la aplicación, establezca la propiedad **posición** de **cuádruple** en (0, 0, 2) y la propiedad **escala** en (1,28, 0,72, 1). Después de estos cambios, el componente de **transformación** en el panel del **Inspector** de la **cuádruple** tendrá el siguiente aspecto:

![Transformación cuádruple](images/spatial-audio/quad-transform.png)

Para crear una textura entre el **cuádruple** y el vídeo, cree una nueva **textura de representación**. En el panel **proyecto** , haga clic con el botón derecho y seleccione **crear-> Mostrar textura**:

![Crear textura de representación](images/spatial-audio/create-render-texture.png)

En el panel **Inspector** de la **textura de representación**, establezca la propiedad **size** para que coincida con la resolución nativa del vídeo de 1280x720. A continuación, para garantizar un buen rendimiento de la representación en HoloLens 2, establezca la propiedad de **búfer de profundidad** en una **profundidad de 16 bits como mínimo**. Después de esta configuración, el panel del **Inspector** para la **textura de representación** tendrá el siguiente aspecto:

![Representar propiedades de textura](images/spatial-audio/render-texture-properties.png)

A continuación, use la nueva **textura de representación** como textura para la **cuádruple**:
1. Arrastre la **textura de representación** desde el panel **proyecto** hasta el **cuádruple** de la **jerarquía** .
2. Para garantizar un buen rendimiento en HoloLens 2, en el panel **Inspector** de la serie **, seleccione**el **sombreador estándar del kit de herramientas de realidad mixta**.

Con esta configuración, el componente de **textura** en el panel del **Inspector** de la **cuádruple** tendrá el siguiente aspecto:

![Propiedades de textura cuádruple](images/spatial-audio/quad-texture-properties.png)

Para establecer el nuevo **reproductor de vídeo** y **representar la textura** para reproducir el clip de vídeo, abra el panel del **Inspector** para el **reproductor de vídeo** y:
* Establecer la propiedad **clip de vídeo** en el archivo de vídeo
* Marque la casilla **bucle**
* Establecer la **textura de destino** en la nueva textura de representación

El panel del **Inspector** del **reproductor de vídeo** tendrá ahora el siguiente aspecto:

![Propiedades del reproductor de vídeo](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatial el audio del vídeo
En el panel **Inspector** del **cuádruple**, cree un **origen de audio** al que enrutará el audio desde el vídeo:
* Haga clic en **Agregar componente** en la parte inferior del panel.
* Agregar un **origen de audio**

Después, en el **origen de audio**:
* Establecer el **resultado** en el mezclador
* Active la casilla **Spatial**
* Mueve el control deslizante de **mezcla espacial** a 1 (3D)

Después de estos cambios, el componente **origen de audio** del panel **Inspector** de la **cuádruple** tendrá el siguiente aspecto:

![Inspector de fuente de audio cuádruple](images/spatial-audio/quad-audio-source-inspector.png)

Para configurar el **reproductor de vídeo** para que enrute su audio a la **fuente de audio** en el **cuádruple**, abra el panel del **Inspector** para el **reproductor de vídeo** y:
* Establecer el **modo de salida de audio** en "origen de audio"
* Establezca la propiedad **origen de audio** en su cuádruple

Después de estos cambios, el panel del **Inspector** del **reproductor de vídeo** tendrá el siguiente aspecto:

![Reproductor de vídeo conjunto de audio origen](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>Pasos siguientes
Pruebe la aplicación en HoloLens 2 o en el editor de Unity. Verá y oirá el vídeo y el audio del vídeo se encontrará espacial.

Continúe con el [capítulo 4](unity-spatial-audio-ch4.md) para usar el botón para habilitar y deshabilitar la espacialización en tiempo de ejecución.

