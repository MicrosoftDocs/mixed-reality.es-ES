---
title: Cámara localizable en Unity
description: Uso de la cámara localizable de HoloLens en Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: fotos, vídeo, hololens, cámara, unity, localizable
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601768"
---
# <a name="locatable-camera-in-unity"></a>Cámara localizable en Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Habilitación de la capacidad de cámara de vídeo de fotos

Se debe declarar la funcionalidad de "cámara Web" para que una aplicación usar el [cámara](locatable-camera.md).
1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a la página "Editar > proyecto configuración > Player"
2. Haga clic en la pestaña "Windows Store"
3. En la sección "Funcionalidades de publicación configuración >", compruebe el **WebCam** y **micrófono** capacidades

Solo una única operación puede producirse con la cámara a la vez. Para determinar qué modo (fotos, vídeo o ninguno) la cámara está actualmente en, puede comprobar UnityEngine.XR.WSA.WebCam.Mode.

## <a name="photo-capture"></a>Captura de fotografías

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *PhotoCapture*

El *PhotoCapture* tipo le permite aprovechar aún fotografías con la cámara de vídeo de fotos. El patrón general para usar *PhotoCapture* tomar una foto es como sigue:
1. Crear un *PhotoCapture* objeto
2. Crear un *CameraParameters* objeto con la configuración que desee
3. Iniciar el modo de fotos a través de *StartPhotoModeAsync*
4. Tomar la fotografía deseada
    * (opcional) Interactuar con esa imagen
5. Detener el modo de fotos y limpiar los recursos

### <a name="common-set-up-for-photocapture"></a>Conjunto común de para PhotoCapture

Para todos los usos de tres, empezaremos con el mismo 3 primeros pasos anteriores

Comenzamos creando una *PhotoCapture* objeto

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

A continuación establecemos nuestro objeto de almacén, nuestros parámetros e iniciar el modo de fotos

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

Al final, también se utilizará la misma limpiar el código presentado aquí

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Después de estos pasos, puede elegir qué tipo de foto para capturar.

### <a name="capture-a-photo-to-a-file"></a>Captura una foto a un archivo

La operación más sencilla consiste en capturar una foto directamente en un archivo. La foto se puede guardar como un JPG o un archivo PNG.

Si se ha iniciado correctamente el modo de fotografías, ahora se tomamos una foto y almacenarlo en el disco

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

Después de capturar la foto en el disco, se salir del modo de foto y, a continuación, limpiar nuestros objetos

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

### <a name="capture-a-photo-to-a-texture2d"></a>Captura una foto a una Texture2D

Al capturar los datos a una Texture2D, el proceso es muy similar a la captura en el disco.

Se sigue el proceso anterior configurar.

En *OnPhotoModeStarted*, se capturará un fotograma a la memoria.

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

Después se aplican los resultados a una textura y usar común limpiar el código anterior.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Captura una foto y la interacción con los bytes sin formato

Para interactuar con los bytes sin formato de una memoria en el marco, se sigue el mismo conjunto de pasos anteriores y *OnPhotoModeStarted* como en captura una foto a una Texture2D. La diferencia radica en *OnCapturedPhotoToMemory* donde podemos obtener los bytes sin formato e interactuar con ellos.

En este ejemplo, crearemos un *lista<Color>*  que podría ser más procesados o aplica una textura mediante *SetPixels()*

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

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* funciones muy similares a *PhotoCapture*. Las dos diferencias son que debe especificar un valor de fotogramas por segundo (FPS) y sólo se puede guardar directamente en el disco como un archivo. mp4. Los pasos a seguir *VideoCapture* son los siguientes:
1. Crear un *VideoCapture* objeto
2. Crear un *CameraParameters* objeto con la configuración que desee
3. Iniciar modo de vídeo a través de *StartVideoModeAsync*
4. Iniciar grabación de vídeo
5. Detener la grabación de vídeo
6. Detener el modo de vídeo y limpiar los recursos

Empezaremos por crear nuestro *VideoCapture* objeto *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

A continuación, configuraremos los parámetros que queremos para la grabación y el inicio.

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

Una vez iniciado, empezaremos a la grabación

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

Una vez iniciada la grabación, se pudo actualizar la interfaz de usuario o los comportamientos para habilitar la detención. Aquí, simplemente inicie una sesión

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

En un momento posterior, queremos detener la grabación. Esto podría suceder en un temporizador o la intervención del usuario, por ejemplo.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Una vez que se ha detenido la grabación, se detendrá el modo de vídeo y limpiar nuestros recursos.

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

## <a name="troubleshooting"></a>Solución de problemas
* No hay soluciones están disponibles
    * Asegúrese del **WebCam** capacidad se especifica en el proyecto.

## <a name="see-also"></a>Vea también
* [Cámara localizable](locatable-camera.md)
