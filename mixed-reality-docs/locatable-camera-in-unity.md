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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="1c8a8-104">Cámara localizable en Unity</span><span class="sxs-lookup"><span data-stu-id="1c8a8-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="1c8a8-105">Habilitación de la capacidad de cámara de vídeo de fotos</span><span class="sxs-lookup"><span data-stu-id="1c8a8-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="1c8a8-106">Se debe declarar la funcionalidad de "cámara Web" para que una aplicación usar el [cámara](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="1c8a8-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="1c8a8-107">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a la página "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="1c8a8-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="1c8a8-108">Haga clic en la pestaña "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="1c8a8-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="1c8a8-109">En la sección "Funcionalidades de publicación configuración >", compruebe el **WebCam** y **micrófono** capacidades</span><span class="sxs-lookup"><span data-stu-id="1c8a8-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="1c8a8-110">Solo una única operación puede producirse con la cámara a la vez.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="1c8a8-111">Para determinar qué modo (fotos, vídeo o ninguno) la cámara está actualmente en, puede comprobar UnityEngine.XR.WSA.WebCam.Mode.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="1c8a8-112">Captura de fotografías</span><span class="sxs-lookup"><span data-stu-id="1c8a8-112">Photo Capture</span></span>

<span data-ttu-id="1c8a8-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="1c8a8-114">**Tipo:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="1c8a8-115">El *PhotoCapture* tipo le permite aprovechar aún fotografías con la cámara de vídeo de fotos.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="1c8a8-116">El patrón general para usar *PhotoCapture* tomar una foto es como sigue:</span><span class="sxs-lookup"><span data-stu-id="1c8a8-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="1c8a8-117">Crear un *PhotoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="1c8a8-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="1c8a8-118">Crear un *CameraParameters* objeto con la configuración que desee</span><span class="sxs-lookup"><span data-stu-id="1c8a8-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="1c8a8-119">Iniciar el modo de fotos a través de *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="1c8a8-120">Tomar la fotografía deseada</span><span class="sxs-lookup"><span data-stu-id="1c8a8-120">Take the desired photo</span></span>
    * <span data-ttu-id="1c8a8-121">(opcional) Interactuar con esa imagen</span><span class="sxs-lookup"><span data-stu-id="1c8a8-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="1c8a8-122">Detener el modo de fotos y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="1c8a8-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="1c8a8-123">Conjunto común de para PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="1c8a8-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="1c8a8-124">Para todos los usos de tres, empezaremos con el mismo 3 primeros pasos anteriores</span><span class="sxs-lookup"><span data-stu-id="1c8a8-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="1c8a8-125">Comenzamos creando una *PhotoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="1c8a8-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="1c8a8-126">A continuación establecemos nuestro objeto de almacén, nuestros parámetros e iniciar el modo de fotos</span><span class="sxs-lookup"><span data-stu-id="1c8a8-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="1c8a8-127">Al final, también se utilizará la misma limpiar el código presentado aquí</span><span class="sxs-lookup"><span data-stu-id="1c8a8-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="1c8a8-128">Después de estos pasos, puede elegir qué tipo de foto para capturar.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="1c8a8-129">Captura una foto a un archivo</span><span class="sxs-lookup"><span data-stu-id="1c8a8-129">Capture a Photo to a File</span></span>

<span data-ttu-id="1c8a8-130">La operación más sencilla consiste en capturar una foto directamente en un archivo.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="1c8a8-131">La foto se puede guardar como un JPG o un archivo PNG.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="1c8a8-132">Si se ha iniciado correctamente el modo de fotografías, ahora se tomamos una foto y almacenarlo en el disco</span><span class="sxs-lookup"><span data-stu-id="1c8a8-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="1c8a8-133">Después de capturar la foto en el disco, se salir del modo de foto y, a continuación, limpiar nuestros objetos</span><span class="sxs-lookup"><span data-stu-id="1c8a8-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="1c8a8-134">Captura una foto a una Texture2D</span><span class="sxs-lookup"><span data-stu-id="1c8a8-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="1c8a8-135">Al capturar los datos a una Texture2D, el proceso es muy similar a la captura en el disco.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="1c8a8-136">Se sigue el proceso anterior configurar.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-136">We will follow the set up process above.</span></span>

<span data-ttu-id="1c8a8-137">En *OnPhotoModeStarted*, se capturará un fotograma a la memoria.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="1c8a8-138">Después se aplican los resultados a una textura y usar común limpiar el código anterior.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="1c8a8-139">Captura una foto y la interacción con los bytes sin formato</span><span class="sxs-lookup"><span data-stu-id="1c8a8-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="1c8a8-140">Para interactuar con los bytes sin formato de una memoria en el marco, se sigue el mismo conjunto de pasos anteriores y *OnPhotoModeStarted* como en captura una foto a una Texture2D.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="1c8a8-141">La diferencia radica en *OnCapturedPhotoToMemory* donde podemos obtener los bytes sin formato e interactuar con ellos.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="1c8a8-142">En este ejemplo, crearemos un *lista<Color>*  que podría ser más procesados o aplica una textura mediante *SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="1c8a8-143">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="1c8a8-143">Video Capture</span></span>

<span data-ttu-id="1c8a8-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="1c8a8-145">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="1c8a8-146">*VideoCapture* funciones muy similares a *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="1c8a8-147">Las dos diferencias son que debe especificar un valor de fotogramas por segundo (FPS) y sólo se puede guardar directamente en el disco como un archivo. mp4.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="1c8a8-148">Los pasos a seguir *VideoCapture* son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="1c8a8-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="1c8a8-149">Crear un *VideoCapture* objeto</span><span class="sxs-lookup"><span data-stu-id="1c8a8-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="1c8a8-150">Crear un *CameraParameters* objeto con la configuración que desee</span><span class="sxs-lookup"><span data-stu-id="1c8a8-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="1c8a8-151">Iniciar modo de vídeo a través de *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="1c8a8-152">Iniciar grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="1c8a8-152">Start recording video</span></span>
5. <span data-ttu-id="1c8a8-153">Detener la grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="1c8a8-153">Stop recording video</span></span>
6. <span data-ttu-id="1c8a8-154">Detener el modo de vídeo y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="1c8a8-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="1c8a8-155">Empezaremos por crear nuestro *VideoCapture* objeto *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="1c8a8-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="1c8a8-156">A continuación, configuraremos los parámetros que queremos para la grabación y el inicio.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="1c8a8-157">Una vez iniciado, empezaremos a la grabación</span><span class="sxs-lookup"><span data-stu-id="1c8a8-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="1c8a8-158">Una vez iniciada la grabación, se pudo actualizar la interfaz de usuario o los comportamientos para habilitar la detención.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="1c8a8-159">Aquí, simplemente inicie una sesión</span><span class="sxs-lookup"><span data-stu-id="1c8a8-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="1c8a8-160">En un momento posterior, queremos detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="1c8a8-161">Esto podría suceder en un temporizador o la intervención del usuario, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="1c8a8-162">Una vez que se ha detenido la grabación, se detendrá el modo de vídeo y limpiar nuestros recursos.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="1c8a8-163">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="1c8a8-163">Troubleshooting</span></span>
* <span data-ttu-id="1c8a8-164">No hay soluciones están disponibles</span><span class="sxs-lookup"><span data-stu-id="1c8a8-164">No resolutions are available</span></span>
    * <span data-ttu-id="1c8a8-165">Asegúrese del **WebCam** capacidad se especifica en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1c8a8-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c8a8-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="1c8a8-166">See Also</span></span>
* [<span data-ttu-id="1c8a8-167">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="1c8a8-167">Locatable camera</span></span>](locatable-camera.md)
