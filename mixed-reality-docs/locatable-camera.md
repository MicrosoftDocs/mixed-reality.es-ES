---
title: Cámara localizable
description: Información general sobre la cámara frontal de HoloLens, cómo funciona y los perfiles y las soluciones disponibles para los desarrolladores.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: cámara, hololens, cámara de color, frontal cara, hololens 2, CV, Computer Vision, fiducial, Marks, código QR, QR, Foto, vídeo
ms.openlocfilehash: 368943dd70c721a41ca7c265a19ecb7c394db312
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861721"
---
# <a name="locatable-camera"></a>Cámara localizable

HoloLens incluye una cámara mundial montada en la parte frontal del dispositivo que permite a las aplicaciones ver lo que ve el usuario. Los desarrolladores tienen acceso y control de la cámara tal como lo harían para las cámaras de color en smartphones, portátiles o de escritorio. La misma captura universal de Windows [media](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) y las API de Windows Media Foundation que funcionan en Mobile y Desktop funcionan en HoloLens. Unity [también ha encapsulado estas API de Windows](locatable-camera-in-unity.md) para simplificar el uso de la cámara en HoloLens para tareas como realizar fotos y vídeos regulares (con o sin hologramas) y buscar la posición de la cámara en y en la perspectiva de la escena.

## <a name="device-camera-information"></a>Información de cámara de dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primera generación)

* Cámara de foto/vídeo (PV) de enfoque fijo con equilibrio de blanco automático, exposición automática y canalización de procesamiento de imágenes completas.
* El LED de privacidad en blanco para el mundo se iluminará siempre que la cámara esté activa
* La cámara admite los siguientes modos (todos los modos tienen una relación de aspecto de 16:9) a 30, 24, 20, 15 y 5 FPS:

  |  Vídeo  |  Vista previa  |  ¿  |  Campo horizontal de la vista (H-Field) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modo predeterminado con estabilización de vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Imagen fija de mayor resolución | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Resolución de sobrebarrido (relleno) antes de la estabilización de vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modo de vídeo de hiperjuego grande con sobrebarrido | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Modo de baja energía/baja resolución para las tareas de procesamiento de imágenes | 

### <a name="hololens-2"></a>HoloLens 2

* Centrar automáticamente la cámara de foto/vídeo (PV) con el equilibrio de blancos automático, la exposición automática y la canalización de procesamiento de imágenes completas.
* El LED de privacidad en blanco orientado al mundo se iluminará cada vez que la cámara esté activa.
* HoloLens 2 admite distintos perfiles de cámara. Obtenga información acerca de cómo [detectar y seleccionar funcionalidades de la cámara](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* La cámara admite los siguientes perfiles y resoluciones (todos los modos de vídeo tienen una relación de aspecto de 16:9):
  
  | Perfil                                         | Vídeo     | Vista previa   | ¿     | Velocidades de fotogramas | Campo horizontal de la vista (H-Field) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64,69                            | Grabación de vídeo de alta calidad                |
  | Legacy, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15, 30       | 64,69                            | Flujo de vista previa para la captura de fotografías de alta calidad |
  | Legacy, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64,69                            | Captura de fotografías de alta calidad                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64,69                            | Escenarios de larga duración                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64,69                            | Escenarios de larga duración                     |
  | Videoconferencia, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 640 x 360   |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Videoconferencia, escenarios de larga duración |

>[!NOTE]
>Los clientes pueden aprovechar la [captura de realidad mixta](mixed-reality-capture.md) para tomar vídeos o fotos de la aplicación, que incluyen hologramas y estabilización de vídeo.
>
>Como desarrollador, existen consideraciones que debe tener en cuenta a la hora de crear la aplicación si quiere que se vea lo mejor posible cuando un cliente captura contenido. También puede habilitar (y personalizar) la captura de realidad mixta desde directamente dentro de la aplicación. Obtenga más información en [captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localizar la cámara del dispositivo en el mundo

Cuando HoloLens toma fotos y vídeos, los fotogramas capturados incluyen la ubicación de la cámara en el mundo, así como el modelo de lente de la cámara. Esto permite a las aplicaciones tener en cuenta la posición de la cámara en el mundo real para escenarios de creación de imágenes mejorados. Los desarrolladores pueden hacer un desarrollo creativo de sus propios escenarios mediante su procesamiento de imágenes favorito o bibliotecas personalizadas de equipos.

La "cámara" en otra parte de la documentación de HoloLens puede hacer referencia a la "cámara de juego virtual" (el frustum en el que se representa la aplicación). A menos que se indique lo contrario, "Camera" se refiere a la cámara de color RGB del mundo real.

Los detalles de esta página cubren el uso de la clase [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) , pero también hay API para extraer las ubicaciones y las funciones intrínsecas de la cámara mediante [atributos Media Foundation](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Para obtener más información, consulte el [ejemplo de seguimiento de caras holográficas](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) .

### <a name="images-with-coordinate-systems"></a>Imágenes con sistemas de coordenadas

Cada fotograma de imagen (ya sea fotográfico o vídeo) incluye una [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) raíz en la cámara en el momento de la captura a la que se puede acceder mediante la propiedad [coordenadas](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) de su [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Además, cada fotograma contiene una descripción del modelo de lente de la cámara que se puede encontrar en la propiedad [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Juntas, estas transformaciones definen para cada píxel un rayo en un espacio 3D que representa la ruta de acceso tomada por las fotografías que han producido el píxel. Estos rayos pueden estar relacionados con otro contenido de la aplicación mediante la obtención de la transformación del sistema de coordenadas del marco a algún otro sistema de coordenadas (por ejemplo, desde un [marco estacionario de referencia](coordinate-systems.md#stationary-frame-of-reference)). En Resumen, cada fotograma de imagen proporciona lo siguiente:
* Datos de píxeles (en formato RGB/NV12/JPEG/etc.)
* Un [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) de la ubicación de la captura
* Una clase [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) que contiene el modo de lente de la cámara

### <a name="camera-to-application-specified-coordinate-system"></a>Cámara a sistema de coordenadas especificado por la aplicación

Para ir de "CameraIntrinsics" y "CameraCoordinateSystem" al sistema de coordenadas del mundo o de la aplicación, necesitará lo siguiente:

[Cámara localizable en Unity](locatable-camera-in-unity.md): La clase PhotoCaptureFrame proporciona automáticamente CameraToWorldMatrix (por lo que no es necesario preocuparse por las transformaciones CameraCoordinateSystem).

[Cámara localizable en DirectX](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking): El ejemplo de seguimiento de caras holográficas muestra la forma bastante sencilla de consultar la transformación entre el sistema de coordenadas de la cámara y sus propios sistemas de coordenadas de aplicación.

### <a name="distortion-error"></a>Error de distorsión

En HoloLens, los flujos de vídeo y de imagen fija no se distorsionan en la canalización de procesamiento de imágenes del sistema antes de que los fotogramas estén disponibles para la aplicación (la secuencia de vista previa contiene los fotogramas distorsionados originales). Dado que solo están disponibles los CameraIntrinsics, las aplicaciones deben suponer que los fotogramas de imagen representan una cámara pinhole perfecta.

En HoloLens (primera generación), la función de no distorsión del procesador de imágenes todavía puede dejar un error de hasta 10 píxeles al usar CameraIntrinsics en los metadatos del marco. En muchos casos de uso, este error no es importante, pero si se alinean los hologramas con los pósteres o marcadores reales, por ejemplo, y observa un < desplazamiento 10px (aproximadamente 11mm para los hologramas ubicados en dos metros), este error de distorsión podría ser la causa. 

## <a name="locatable-camera-usage-scenarios"></a>Escenarios de uso de cámara localizables

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar una foto o un vídeo en el mundo en el que se capturó

Los fotogramas de la cámara del dispositivo tienen una transformación "cámara a mundo", que se puede usar para mostrar exactamente dónde estaba el dispositivo cuando se tomó la imagen. Por ejemplo, podría colocar un pequeño icono de Holographic en esta ubicación (CameraToWorld. MultiplyPoint (Vector3. Zero)) e incluso dibujar una pequeña flecha en la dirección en la que se encontraba la cámara (CameraToWorld. MultiplyVector (Vector3. forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Seguimiento de etiqueta/patrón/póster/objeto

Muchas aplicaciones de realidad mixta usan una imagen reconocible o un patrón visual para crear un punto de seguimiento en el espacio. A continuación, se usa para representar objetos relativos a ese punto o crear una ubicación conocida. Algunos usos de HoloLens incluyen encontrar un objeto del mundo real etiquetado con fiducials (por ejemplo, un monitor de TV con un código QR), colocar hologramas en fiducials y emparejar visualmente con dispositivos que no sean de HoloLens, como tabletas que se han configurado para comunicarse con HoloLens a través de Wi-Fi.

Para reconocer un patrón visual y, a continuación, colocar ese objeto en el espacio del mundo de las aplicaciones, necesitará algunas cosas:
1. Un kit de herramientas de reconocimiento de patrones de imagen, como código QR, etiquetas AR, buscador de caras, rastreadores de círculos, OCR, etc.
2. Recopilar fotogramas de imagen en tiempo de ejecución y pasarlos a la capa de reconocimiento
3. Vuelva a proyectar las ubicaciones de las imágenes en las posiciones mundiales o en los rayos más probables. Consulte
4. Coloque los modelos virtuales en estas ubicaciones mundiales

Algunos vínculos de procesamiento de imágenes importantes:
* [OpenCV](http://opencv.org/)
* [Etiquetas QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantener una velocidad de fotogramas de aplicación interactiva es fundamental, especialmente cuando se trabaja con algoritmos de reconocimiento de imágenes de ejecución prolongada. Por esta razón, normalmente usamos el patrón siguiente:
1. Subproceso principal: administra el objeto de cámara
2. Subproceso principal: solicita nuevos marcos (Async)
3. Subproceso principal: pasar nuevos marcos al subproceso de seguimiento
4. Subproceso de seguimiento: procesa la imagen para recopilar puntos clave
5. Subproceso principal: mueve el modelo virtual para que coincida con los puntos clave encontrados
6. Subproceso principal: repetir en el paso 2

Algunos sistemas de marcadores de imagen solo proporcionan una ubicación de un solo píxel (otros proporcionan la transformación completa en cuyo caso no se necesitará esta sección), lo que equivale a un rayo de ubicaciones posibles. Para llegar a una sola ubicación 3D, podemos aprovechar varios rayos y buscar el resultado final por su intersección aproximada. Para ello, necesitará:
1. Obtener un bucle que va a recopilar varias imágenes de la cámara
2. Busque los puntos de características asociados y sus rayos mundiales
3. Si tiene un diccionario de características, cada una con varios rayos de mundo, puede usar el código siguiente para resolver la intersección de esos rayos:

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

Dadas dos o más ubicaciones de etiquetas de las que se ha realizado un seguimiento, puede colocar una escena modelada para ajustarse al escenario actual de los usuarios. Si no puede asumir la gravedad, necesitará tres ubicaciones de etiquetas. En muchos casos se usa una combinación de colores simple en la que los esferas blancas representan ubicaciones de etiquetas de las que se realiza un seguimiento en tiempo real y las esferas azules representan ubicaciones de etiquetas modeladas, lo que permite al usuario medir visualmente la calidad de la alineación. Damos por sentado la siguiente configuración en todas las aplicaciones:
* Dos o más ubicaciones de etiquetas modeladas
* Un "espacio de calibración" que en la escena es el elemento primario de las etiquetas.
* Identificador de la característica de cámara
* Comportamiento que mueve el espacio de calibración para alinear las etiquetas modeladas con las etiquetas en tiempo real (tenemos cuidado de mover el espacio primario, no los propios marcadores modelados, ya que otras conexiones son posiciones relativas a ellos).

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Realizar un seguimiento o identificar objetos o caras del mundo real con LEDs u otras bibliotecas de reconocedores

Ejemplos:
* Robots industriales con LED (o códigos QR para objetos móviles más lentos)
* Identificar y reconocer objetos en el salón
* Identifique y reconozca a personas de la habitación (por ejemplo, coloque las tarjetas de contacto holográfica en caras)

## <a name="see-also"></a>Vea también
* [Ejemplo de cámara localizable](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Cámara localizable en Unity](locatable-camera-in-unity.md)
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Introducción a la captura multimedia](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Ejemplo de seguimiento de caras holográficas](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
