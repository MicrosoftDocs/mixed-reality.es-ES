---
title: Cámara localizable en Unity
description: Uso de la cámara de HoloLens localizable en Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, vídeo, hololens, cámara, Unity, localizable
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597618"
---
# <a name="locatable-camera-in-unity"></a>Cámara localizable en Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Habilitación de la funcionalidad de la cámara de vídeo fotográfico

La funcionalidad "WebCam" se debe declarar para que una aplicación use la [cámara](locatable-camera.md).
1. En el editor de Unity, vaya a la página "Editar > configuración del proyecto > reproductor" para ir a la configuración del reproductor.
2. Haga clic en la pestaña "tienda Windows"
3. En la sección "configuración de publicación > funcionalidades", compruebe las funcionalidades de la **cámara web** y el **micrófono**

Solo se puede realizar una operación con la cámara a la vez. Para determinar qué modo (fotografía, vídeo o ninguno) tiene actualmente la cámara, puede comprobar UnityEngine. XR. WSA. WebCam. Mode.

## <a name="photo-capture"></a>Captura de foto

**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*<br>
**Tipo:** *fotocapture*

El tipo de *fotocaptura* le permite tomar fotografías con la cámara de vídeo fotográfico. El patrón general para usar *fotocapture* para tomar una foto es el siguiente:
1. Creación de un objeto *Fotocapture*
2. Cree un objeto *CameraParameters* con los valores que desee.
3. Iniciar el modo fotográfico a través de *StartPhotoModeAsync*
4. Tomar la foto deseada
    * opta Interactuar con esa imagen
5. Detener el modo fotográfico y limpiar los recursos

### <a name="common-set-up-for-photocapture"></a>Configuración común para fotocaptura

Para los tres usos, empiece con los primeros 3 pasos anteriores.

Inicio mediante la creación de un objeto *Fotocapture*

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

A continuación, almacene el objeto, establezca los parámetros e inicie el modo fotográfico.

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

Al final, también usará el mismo código de limpieza que se muestra aquí.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Después de estos pasos, puede elegir el tipo de foto que desea capturar.

### <a name="capture-a-photo-to-a-file"></a>Capturar una foto en un archivo

La operación más sencilla consiste en capturar una foto directamente en un archivo. La foto se puede guardar como JPG o PNG.

Si ha iniciado correctamente el modo fotográfico, tome una foto y almacénela en el disco

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Después de capturar la foto en el disco, salga del modo fotográfico y limpie los objetos

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Capturar una foto en un Texture2D

Al capturar datos en un Texture2D, el proceso es muy similar a la captura en disco.

Siga el proceso de configuración anterior.

En *OnPhotoModeStarted*, Capture un fotograma en la memoria.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

A continuación, se aplicará el resultado a una textura y se utilizará el código de limpieza común anterior.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capturar una foto e interactuar con los bytes sin formato

Para interactuar con los bytes sin formato de un marco de memoria, siga los mismos pasos de configuración descritos anteriormente y *OnPhotoModeStarted* como en la captura de una foto en un Texture2D. La diferencia está en *OnCapturedPhotoToMemory* , donde puede obtener los bytes sin formato e interactuar con ellos.

En este ejemplo, creará una *lista<Color>* que se podría procesar o aplicar posteriormente a una textura mediante *SetPixels ()*

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>Captura de vídeo

**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* funciona de manera muy similar a la *fotocaptura*. Las únicas dos diferencias son que debe especificar un valor de fotogramas por segundo (FPS) y solo puede guardar directamente en el disco como un archivo. MP4. Los pasos para usar *VideoCapture* son los siguientes:
1. Creación de un objeto de *VideoCapture*
2. Cree un objeto *CameraParameters* con los valores que desee.
3. Iniciar el modo de vídeo a través de *StartVideoModeAsync*
4. Iniciar grabación de vídeo
5. Detener grabación de vídeo
6. Detener el modo de vídeo y limpiar los recursos

Empiece por crear el objeto *VideoCapture* de *videocaptura m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

A continuación, configure los parámetros que desea para la grabación y el inicio.

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

Una vez iniciado, comience la grabación.

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

Una vez iniciada la grabación, puede actualizar la interfaz de usuario o los comportamientos para habilitar la detención. Aquí solo tiene que registrar.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

En un punto posterior, querrá detener la grabación. Esto puede deberse a un temporizador o a una entrada del usuario, por ejemplo.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Una vez que la grabación se ha detenido, detenga el modo de vídeo y limpie los recursos.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>de solución de problemas
* No hay ninguna solución disponible
    * Asegúrese de que la funcionalidad de la **cámara web** está especificada en el proyecto.

## <a name="see-also"></a>Consulta también
* [Cámara localizable](locatable-camera.md)
