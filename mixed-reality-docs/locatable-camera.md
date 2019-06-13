---
title: Cámara localizable
description: Información general acerca de la cámara frontal de HoloLens, cómo funciona y los perfiles y las soluciones disponibles para los desarrolladores.
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: cámara, hololens, cámara de color, frontales, hololens, 2, cv, computer vision o estimación, marcadores, código qr, qr, fotos, vídeo
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028612"
---
# <a name="locatable-camera"></a>Cámara localizable

HoloLens incluyen una cámara de mundo orientado montada en la parte frontal del dispositivo que permite que las aplicaciones ver lo que ve el usuario. Los desarrolladores tienen acceso y control de la cámara, tal como harían para las cámaras de color en los smartphones, equipos portátiles o equipos de escritorio. El mismos windows universales [záznam média](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) y foundation de windows media API que funcionan en el escritorio y móviles funcionan en HoloLens. Unity [también se ha ajustado estas ventanas API](locatable-camera-in-unity.md) abstraer uso simple de la cámara en HoloLens para tareas como teniendo regulares fotos y vídeos (con o sin hologramas) y buscar la posición de la cámara en y perspectiva en el escena.

## <a name="device-camera-information"></a>Información de la cámara de dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primera generación)

* Cámara de fotografías y vídeo (PV) enfoque fijo con balance de blanco automático, exposición automática y la canalización de procesamiento de imagen completa.
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

* Cámara de fotografías y vídeo (PV) enfoque automático con balance de blanco automático, exposición automática y la canalización de procesamiento de imagen completa.
* LED de privacidad en blanco accesible desde el mundo se iluminará cada vez que la cámara está activa.
* HoloLens 2 admite los perfiles de la cámara. Obtenga información sobre cómo [detectar y seleccionar las capacidades de cámara](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* La cámara admite los siguientes perfiles y las resoluciones (todos los modos de vídeo son relación de aspecto 16:9):
  
  | Perfil                                         | Vídeo     | Vista previa   | Todavía     | Velocidades de fotogramas | Campo horizontal de visión (FOV-H) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Heredado, BalancedVideoAndPhoto 0, 100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | Grabación de vídeo de alta calidad                |
  | Heredado, BalancedVideoAndPhoto 0, 100             |           |           | 3904x2196 |             | 64.69                            | Captura de fotografías de alta calidad                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | Escenarios de larga duración                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | Escenarios de larga duración                     |
  | VideoConferencing,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 1128x635  |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |

>[!NOTE]
>Los clientes pueden aprovechar [mixto captura realidad](mixed-reality-capture.md) vídeos o fotografías de la aplicación, que incluyen hologramas y estabilización de vídeo.
>
>Como desarrollador, existen consideraciones que debe tener en cuenta al crear la aplicación si desea buscar tan eficaz como sea posible al contenido de captura de un cliente. También puede habilitar (y personalizar) captura la realidad mixta de directamente dentro de la aplicación. Obtenga más información en [mixto captura realidad para los desarrolladores](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localización de la cámara del dispositivo en el mundo

Cuando HoloLens toma fotografías y vídeos, los fotogramas capturados incluyen la ubicación de la cámara en el mundo, así como la proyección en perspectiva de la cámara. Esto permite que las aplicaciones para razonar sobre la posición de la cámara en el mundo real para escenarios de creación de imágenes aumentados. Los desarrolladores de forma creativa pueden implementar sus propios escenarios mediante un procesamiento de imágenes favorito o bibliotecas de visión artificial personalizado.

"Cámara" en otra parte de la documentación de HoloLens puede hacer referencia a la "juego cámara virtual" (frustum de la aplicación se representa en). A menos que se indica lo contrario, "cámara" en esta página se refiere a la cámara de color RGB reales.

Los detalles sobre esta cubren la página [Media Foundation atributos](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), sin embargo, hay también las API para extraer la cámara utilizando las funciones intrínsecas [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).  

### <a name="images-with-coordinate-systems"></a>Imágenes con sistemas de coordenadas

Cada marco de imagen (si foto o vídeo) incluye un sistema de coordenadas, así como dos transformaciones importantes. La "vista" transformar mapas desde el sistema de coordenadas proporcionado a la cámara y el "proyección" se asigna desde la cámara a píxeles de la imagen. Juntas, estas transformaciones definen para cada píxel un rayo en el espacio 3D que representa la ruta de acceso realizada por el photons que generó el píxel. Estos rayos pueden estar relacionados con otro contenido en la aplicación mediante la obtención de la transformación de sistema de coordenadas del marco a otro sistema de coordenadas (por ejemplo, desde un [marco estático de referencia](coordinate-systems.md#stationary-frame-of-reference)). En resumen, cada marco de imagen ofrece lo siguiente:
* Datos de píxeles (en formato RGB, NV12, JPEG, etc.)
* 3 fragmentos de metadatos (almacenados como [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) que hacen cada fotograma "localizable":

|  Nombre del atributo  |  Tipo  |  GUID  |  Descripción | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  Almacena el [del sistema de coordenadas](coordinate-systems-in-directx.md) del fotograma capturado | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  Almacena extrínsecos transformación de la cámara en el sistema de coordenadas | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  Almacena la transformación de proyección de la cámara | 

La transformación de proyección representa las propiedades intrínsecas (longitud focal, centro de proyección, sesgar) de la lente asignado en un plano de la imagen que se extiende desde -1 a + 1 en el eje X e Y.

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

Las distintas aplicaciones tendrán distintos sistemas de coordenadas. Presentamos una visión general del flujo para localizar un píxel de la cámara para una sola aplicación:

![Transformaciones aplicadas a los sistemas de coordenadas de la cámara](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>Cámara al sistema de coordenadas especificado por la aplicación

Para ir desde el 'CameraView' y 'CameraCoordinateSystem' al aplicación o sistema de coordenadas, necesitará lo siguiente:

[Cámara localizable en Unity](locatable-camera-in-unity.md): Clase PhotoCaptureFrame proporciona automáticamente CameraToWorldMatrix (por lo que no es necesario preocuparse por las transformaciones CameraCoordinateSystem).

[Cámara localizable en DirectX](locatable-camera-in-directx.md): Muestra la manera bastante sencilla para consultar la transformación entre el sistema de coordenadas de la cámara y coordinate system(s) de su propia aplicación.

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>Sistema de coordenadas especificado por la aplicación en coordenadas de píxel

Supongamos que desea buscar o dibujar en una ubicación específica de 3d en una imagen de la cámara:

Las transformaciones de vista y proyección, mientras ambas matrices de 4 x 4, deben utilizarse de forma ligeramente diferente. Es decir, después de realizar la proyección, uno 'normalizarán por w', este paso adicional en la proyección simula cómo varias ubicaciones diferentes de 3d pueden acabar como la misma ubicación 2d en una pantalla (es decir, algo a lo largo de un radio determinado se mostrará en el mismo píxel). Por lo que la clave de puntos (en el código del sombreador):

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>Píxeles al sistema de coordenadas especificado por la aplicación

Ir de píxeles a coordenadas universales es un poco más complicado:

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

Donde definimos UnProject como:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

Para buscar la ubicación del mundo real de un punto, será necesario: mundo dos rayos y encontrar su intersección o un tamaño conocido de los puntos.

### <a name="distortion-error"></a>Error de distorsión

En HoloLens, el vídeo y sigue los flujos de imagen son distorsiones en la canalización de procesamiento de la imagen del sistema antes de que los marcos están disponibles para la aplicación (la secuencia de vista previa contiene los fotogramas distorsionados originales). Ya está disponible solo en la matriz de proyección, aplicaciones deben asumir la imagen marcos representan una cámara pinhole perfecto, sin embargo el undistortion funcione en el procesador de imágenes puede dejar un error de hasta 10 píxeles cuando se usa en la matriz de proyección los metadatos del marco. En muchos casos de uso, este error no se importa, pero si se están alineando hologramas a marcadores/pósteres de mundo real, por ejemplo, y tenga en cuenta un < 10 px de desplazamiento (aproximadamente 11mm para hologramas colocado 2 metros de distancia) distorsión de este error podría ser la causa.

## <a name="locatable-camera-usage-scenarios"></a>Escenarios de uso de la cámara localizable

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar una foto o vídeo en el mundo donde capturó

Los marcos de la cámara del dispositivo incluyen una transformación "Cámara a World", que puede usarse para mostrar exactamente donde el dispositivo estaba cuando se tomó la imagen. Por ejemplo podría colocar un pequeño icono holográfico en esta ubicación (CameraToWorld.MultiplyPoint(Vector3.zero)) y draw incluso una pequeña flecha en la dirección que la cámara enfrentaba (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="painting-the-world-using-a-camera-shader"></a>El dibujo del mundo mediante un sombreador de cámara

En esta sección vamos a crear un material 'sombreador' ese colores en el mundo en función de donde se mostraba en la vista de la cámara de un dispositivo. Eficazmente lo que haremos es que cada vértice descifrará su ubicación en relación con la cámara y, a continuación, cada píxel utilizará la matriz de proyección' ' figura fuera que está asociada con la textura de imagen. Por último y, opcionalmente, se deberá atenuar las esquinas de la imagen para que parezca más como un sueño similar de memoria:

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

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
2. Buscar el [puntos de característica asociados](#pixel-to-application-specified-coordinate-system)y sus rayos world
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

### <a name="render-holograms-from-the-cameras-position"></a>Representar hologramas desde la posición de la cámara

Nota: Si intenta crear las suyas propias [mixto captura realidad (MRC)](mixed-reality-capture.md), que combina hologramas con el flujo de la cámara, puede usar el [efectos MRC](mixed-reality-capture-for-developers.md) o habilitar la propiedad showHolograms en [ Cámara localizable en Unity](locatable-camera-in-unity.md).

Si desea realizar un procesamiento especial directamente en la secuencia de cámara RGB, es posible representar hologramas en el espacio de la posición de la cámara en sincronización con una fuente de vídeo con el fin de proporcionar una vista previa grabación/live holograma personalizado.

En Skype, hacemos esto para mostrar que el cliente remoto lo está viendo el usuario de HoloLens y que puedan interactuar con el mismos hologramas. Antes de enviar a través de cada fotograma de vídeo a través del servicio Skype, obtenemos datos cámara correspondientes de cada fotograma. Hemos, a continuación, los metadatos intrínsecos y extrínsecos de la cámara con el fotograma de vídeo del paquete y, a continuación, enviarla a través del servicio Skype.

En el lado receptor, con Unity, nos hemos ya sincronizados todos los hologramas en el espacio del usuario HoloLens con el mismo sistema de coordenadas. Esto nos permite usar extrínsecos metadatos de la cámara para colocar la cámara de Unity en el lugar exacto en el mundo (en relación con el resto de los hologramas) que el usuario HoloLens estaba de pie cuando se capturó ese fotograma de vídeo y use la información intrínsecos de cámara para Asegúrese de que la vista es el mismo.

Una vez que tenemos la cámara configurado correctamente, combinamos qué hologramas ve la cámara en el marco que hemos recibido de Skype, crear una vista de realidad mixta de cuál es el usuario de HoloLens ve mediante Graphics.Blit.

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
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
