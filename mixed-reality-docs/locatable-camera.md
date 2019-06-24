---
title: Cámara localizable
description: Información general acerca de la cámara frontal de HoloLens, cómo funciona y los perfiles y las soluciones disponibles para los desarrolladores.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: cámara, hololens, cámara de color, frontal accesibles desde
ms.openlocfilehash: f661fc82fbeab9a870e8ccf7044c9bb375bed7e3
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326290"
---
# <a name="locatable-camera"></a>Cámara localizable

HoloLens incluyen una cámara de mundo orientado montada en la parte frontal del dispositivo que permite que las aplicaciones ver lo que ve el usuario. Los desarrolladores tienen acceso y control de la cámara, tal como harían para las cámaras de color en los smartphones, equipos portátiles o equipos de escritorio. El mismos windows universales [záznam média](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) y foundation de windows media API que funcionan en el escritorio y móviles funcionan en HoloLens. Unity [también se ha ajustado estas ventanas API](locatable-camera-in-unity.md) abstraer uso simple de la cámara en HoloLens para tareas como teniendo regulares fotos y vídeos (con o sin hologramas) y buscar la posición de la cámara en y perspectiva en el escena.

## <a name="device-camera-information"></a>Información de la cámara de dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primera generación)

* Cámara de fotografías y vídeo (PV) enfoque fijo, con el balance de blanco automático, exposición automática y canalización de procesamiento de imagen completa
* LED de privacidad en blanco accesible desde el mundo se iluminará cada vez que la cámara está activa
* La cámara admite los siguientes modos (todos los modos son relación de aspecto 16:9) en fps 5, 15, 20, 24 y 30:

  |  Vídeo  |  Vista previa  |  Todavía  |  Campo horizontal de visión (FOV-H) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modo predeterminado con estabilización de vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Imagen fija de mayor resolución | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Resolución de sobrebarrido (relleno) antes de estabilización de vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modo de vídeo grande FOV con sobrebarrido | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Baja potencia y tareas de procesamiento de modo de baja resolución de imagen | 

### <a name="hololens-2"></a>HoloLens 2

* Cámara de fotografías y vídeo (PV) enfoque automático, con el balance de blanco automático, exposición automática y canalización de procesamiento de imagen completa
* LED de privacidad en blanco accesible desde el mundo se iluminará cada vez que la cámara está activa
* La cámara admite los siguientes modos (todos los modos de vídeo son relación de aspecto 16:9):

  >[!NOTE]
  >Estos modos están sujetos a cambios antes de la disponibilidad general de HoloLens 2.

  |  Vídeo  |  Vista previa  |  Todavía  |  Velocidades de fotogramas  |  Campo horizontal de visión (FOV-H) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|----------|
  |  1920x1080 |  1920x1080 |  N/D |  30, 15 fps  |  54deg  |  (modo predeterminado con estabilización de vídeo) | 
  |  N/D |  N/D |  3904X2196 |  N/D  |  64deg |  Imagen fija de mayor resolución | 
  |  2272x1278 |  2272x1278 |  N/D |  30, 15 fps  |  64deg |  Resolución de sobrebarrido (relleno) antes de estabilización de vídeo | 
  |  1952x1100 |  1952x1100 |  1952x1100  |  30, 15 fps  |  64deg |  Transmisión de alta calidad | 
  |  1280x720 |  1280x720 |  N/D |  30, 15, fps 5  |  64deg |  Modo de baja energía o resolución de transmisión por secuencias y las tareas de procesamiento de imágenes | 

## <a name="locating-the-device-camera-in-the-world"></a>Localización de la cámara del dispositivo en el mundo

Cuando HoloLens toma fotografías y vídeos, los fotogramas capturados incluyen la ubicación de la cámara en el mundo, así como el modelo de la lente de la cámara. Esto permite que las aplicaciones para razonar sobre la posición de la cámara en el mundo real para escenarios de creación de imágenes aumentados. Los desarrolladores de forma creativa pueden implementar sus propios escenarios mediante un procesamiento de imágenes favorito o bibliotecas de visión artificial personalizado.

"Cámara" en otra parte de la documentación de HoloLens puede hacer referencia a la "juego cámara virtual" (frustum de la aplicación se representa en). A menos que se indica lo contrario, "cámara" en esta página se refiere a la cámara de color RGB reales.

Los detalles en esta página mediante portada el [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) clase, sin embargo, hay también las API a las funciones intrínsecas de cámara de extracción y ubicaciones mediante [Media Foundation atributos](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Consulte la [ejemplo de seguimiento de caras holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) para obtener más información.

### <a name="images-with-coordinate-systems"></a>Imágenes con sistemas de coordenadas

Cada marco de imagen (si foto o vídeo) incluye un [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) cuya raíz comienza en la cámara en el momento de captura que se puede acceder mediante el [CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) propiedad de su [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Además, cada marco contiene una descripción del modelo de lente de cámara que se encuentra en la [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) propiedad. Juntas, estas transformaciones definen para cada píxel un rayo en el espacio 3D que representa la ruta de acceso realizada por el photons que generó el píxel. Estos rayos pueden estar relacionados con otro contenido en la aplicación mediante la obtención de la transformación de sistema de coordenadas del marco a otro sistema de coordenadas (por ejemplo, desde un [marco estático de referencia](coordinate-systems.md#stationary-frame-of-reference)). En resumen, cada marco de imagen ofrece lo siguiente:
* Datos de píxeles (en formato RGB, NV12, JPEG, etc.)
* Un [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) desde la ubicación de la captura
* Un [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) clase que contiene el modo de lente de la cámara

### <a name="camera-to-application-specified-coordinate-system"></a>Cámara al sistema de coordenadas especificado por la aplicación

Para ir desde el 'CameraIntrinsics' y 'CameraCoordinateSystem' al aplicación o sistema de coordenadas, necesitará lo siguiente:

[Cámara localizable en Unity](locatable-camera-in-unity.md): Clase PhotoCaptureFrame proporciona automáticamente CameraToWorldMatrix (por lo que no es necesario preocuparse por las transformaciones CameraCoordinateSystem).

[Cámara localizable en DirectX](locatable-camera-in-directx.md): Muestra la manera bastante sencilla para consultar la transformación entre el sistema de coordenadas de la cámara y coordinate system(s) de su propia aplicación.

### <a name="distortion-error"></a>Error de distorsión

En HoloLens, el vídeo y sigue los flujos de imagen son distorsiones en la canalización de procesamiento de la imagen del sistema antes de que los marcos están disponibles para la aplicación (la secuencia de vista previa contiene los fotogramas distorsionados originales). Dado que sólo el CameraIntrinsics se ponen a disposición, aplicaciones deben asumir la imagen marcos representan una cámara pinhole perfecto, sin embargo el undistortion funcione en el procesador de imágenes puede dejar un error de hasta 10 píxeles en HoloLens (primera generación) Cuando se usa el CameraIntrinsics en los metadatos del marco. En muchos casos de uso, este error no se importa, pero si se están alineando hologramas a marcadores/pósteres de mundo real, por ejemplo, y tenga en cuenta un < 10 px de desplazamiento (aproximadamente 11mm para hologramas colocado 2 metros de distancia) distorsión de este error podría ser la causa. 

## <a name="locatable-camera-usage-scenarios"></a>Escenarios de uso de la cámara localizable

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar una foto o vídeo en el mundo donde capturó

Los marcos de la cámara del dispositivo incluyen una transformación "Cámara a World", que puede usarse para mostrar exactamente donde el dispositivo estaba cuando se tomó la imagen. Por ejemplo podría colocar un pequeño icono holográfico en esta ubicación (CameraToWorld.MultiplyPoint(Vector3.zero)) y draw incluso una pequeña flecha en la dirección que la cámara enfrentaba (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Etiqueta / modelo / póster / seguimiento de objetos

Muchas aplicaciones de realidad mixta usan una imagen reconocible o patrón visual para crear un punto trackable en el espacio. A continuación, se utiliza para representar objetos con relación a la que elija o creación una ubicación conocida. Algunos usos de HoloLens incluyen buscar un objeto del mundo real se etiqueta con fiducials (por ejemplo, un monitor de TV con un código QR), colocar hologramas sobre fiducials y visualmente con no HoloLens dispositivos como tabletas que se configuraron para comunicarse con HoloLens a través de emparejamiento Wi-Fi.

Para reconocer una pauta visual y, a continuación, colocar ese objeto en el espacio global de aplicaciones, necesitará algunas cosas:
1. Una imagen patrón reconocimiento Kit de herramientas, como el código QR, AR etiquetas, buscador de cara, rastreadores de círculo, etcetera OCR.
2. Recopile los marcos de imagen en tiempo de ejecución y pasarlos a la capa de reconocimiento
3. Unproject sus ubicaciones de las imágenes en las posiciones del mundo, o los rayos mundo probablemente. Consulte
4. Coloque los modelos de virtuales a través de estas ubicaciones del mundo

Algunos vínculos de procesamiento de imagen importantes:
* [OpenCV](http://opencv.org/)
* [QR etiquetas](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantener una velocidad de fotogramas de aplicación interactiva es crítico, especialmente al tratar con algoritmos de reconocimiento de imagen de ejecución prolongada. Por este motivo, usamos frecuentemente el siguiente patrón:
1. Subproceso principal: administra el objeto de cámara
2. Subproceso principal: solicitudes nuevos marcos (asincrónico)
3. Subproceso principal: pasar nuevos marcos a seguimiento de subproceso
4. Seguimiento de subproceso: imagen de los procesos para recopilar los puntos clave
5. Subproceso principal: encuentra el modelo virtual se desplaza para que coincida con los puntos clave
6. Subproceso principal: repita el paso 2

Algunos sistemas de marcador de imagen solo proporcionan una ubicación de píxel único (otros proporcionan la transformación completa en cuyo caso no se necesitará en esta sección), que equivale a un rayo de ubicaciones posibles. Para llegar a una sola ubicación 3d, a continuación, podemos aprovechar varios rayos y buscar el resultado final mediante su intersección aproximado. Para ello deberá:
1. Obtener un bucle que se va a recopilar varias imágenes de la cámara
2. Buscar los puntos de función asociado y los rayos su mundo
3. Cuando haya un diccionario de funciones, cada uno con varios rayos del mundo, puede usar el código siguiente a la solución en la intersección de los rayos:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Dadas dos o más ubicaciones de etiqueta sometidas a seguimiento, puede colocar una escena modelled para ajustar el escenario actual de los usuarios. Si no se puede suponer la gravedad, necesitará tres ubicaciones de etiqueta. En muchos casos, que se usa una combinación de colores simple donde esferas blancos representan en tiempo real realiza un seguimiento de las ubicaciones de la etiqueta y esferas azules representan ubicaciones de etiqueta pueden modelar, esto permite al usuario medir la calidad de la alineación de visualmente. Se supone la siguiente configuración en todas nuestras aplicaciones:
* Dos o más ubicaciones pueden modelar etiqueta
* Una 'espacio de calibración' que en la escena es el elemento primario de las etiquetas
* Identificador de la característica de cámara
* Comportamiento que se mueve el espacio de calibración para alinear las etiquetas modelled con las etiquetas en tiempo real (estamos cuidados al mover el espacio primario, no los marcadores modelled por sí mismos, porque otros connect es posiciones en relación con ellos).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Seguimiento o identificar estacionarios etiquetados o en movimiento reales objetos/caras mediante LED u otras bibliotecas de módulo de reconocimiento

Ejemplos:
* Robots industriales con LED (u objetos de los códigos QR para mover más lento)
* Identificar y reconocer objetos en la sala de reuniones
* Identificar y reconocer las personas del salón (por ejemplo, lugar holográfica tarjetas de contacto a través de caras)

## <a name="see-also"></a>Vea también
* [Cámara localizable en DirectX](locatable-camera-in-directx.md)
* [Cámara localizable en Unity](locatable-camera-in-unity.md)
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Introducción de captura de medios](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Ejemplo de seguimiento de caras holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
