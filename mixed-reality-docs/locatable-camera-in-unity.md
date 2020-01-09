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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="bc05e-104">Cámara localizable en Unity</span><span class="sxs-lookup"><span data-stu-id="bc05e-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="bc05e-105">Habilitación de la funcionalidad de la cámara de vídeo fotográfico</span><span class="sxs-lookup"><span data-stu-id="bc05e-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="bc05e-106">La funcionalidad "WebCam" se debe declarar para que una aplicación use la [cámara](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="bc05e-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="bc05e-107">En el editor de Unity, vaya a la página "Editar > configuración del proyecto > reproductor" para ir a la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="bc05e-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="bc05e-108">Haga clic en la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="bc05e-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="bc05e-109">En la sección "configuración de publicación > funcionalidades", compruebe las funcionalidades de la **cámara web** y el **micrófono**</span><span class="sxs-lookup"><span data-stu-id="bc05e-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="bc05e-110">Solo se puede realizar una operación con la cámara a la vez.</span><span class="sxs-lookup"><span data-stu-id="bc05e-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="bc05e-111">Para determinar qué modo (fotografía, vídeo o ninguno) tiene actualmente la cámara, puede comprobar UnityEngine. XR. WSA. WebCam. Mode.</span><span class="sxs-lookup"><span data-stu-id="bc05e-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="bc05e-112">Captura de foto</span><span class="sxs-lookup"><span data-stu-id="bc05e-112">Photo Capture</span></span>

<span data-ttu-id="bc05e-113">**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="bc05e-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="bc05e-114">**Tipo:** *fotocapture*</span><span class="sxs-lookup"><span data-stu-id="bc05e-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="bc05e-115">El tipo de *fotocaptura* le permite tomar fotografías con la cámara de vídeo fotográfico.</span><span class="sxs-lookup"><span data-stu-id="bc05e-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="bc05e-116">El patrón general para usar *fotocapture* para tomar una foto es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="bc05e-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="bc05e-117">Creación de un objeto *Fotocapture*</span><span class="sxs-lookup"><span data-stu-id="bc05e-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="bc05e-118">Cree un objeto *CameraParameters* con los valores que desee.</span><span class="sxs-lookup"><span data-stu-id="bc05e-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="bc05e-119">Iniciar el modo fotográfico a través de *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="bc05e-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="bc05e-120">Tomar la foto deseada</span><span class="sxs-lookup"><span data-stu-id="bc05e-120">Take the desired photo</span></span>
    * <span data-ttu-id="bc05e-121">opta Interactuar con esa imagen</span><span class="sxs-lookup"><span data-stu-id="bc05e-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="bc05e-122">Detener el modo fotográfico y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="bc05e-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="bc05e-123">Configuración común para fotocaptura</span><span class="sxs-lookup"><span data-stu-id="bc05e-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="bc05e-124">Para los tres usos, empiece con los primeros 3 pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="bc05e-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="bc05e-125">Inicio mediante la creación de un objeto *Fotocapture*</span><span class="sxs-lookup"><span data-stu-id="bc05e-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="bc05e-126">A continuación, almacene el objeto, establezca los parámetros e inicie el modo fotográfico.</span><span class="sxs-lookup"><span data-stu-id="bc05e-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="bc05e-127">Al final, también usará el mismo código de limpieza que se muestra aquí.</span><span class="sxs-lookup"><span data-stu-id="bc05e-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="bc05e-128">Después de estos pasos, puede elegir el tipo de foto que desea capturar.</span><span class="sxs-lookup"><span data-stu-id="bc05e-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="bc05e-129">Capturar una foto en un archivo</span><span class="sxs-lookup"><span data-stu-id="bc05e-129">Capture a Photo to a File</span></span>

<span data-ttu-id="bc05e-130">La operación más sencilla consiste en capturar una foto directamente en un archivo.</span><span class="sxs-lookup"><span data-stu-id="bc05e-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="bc05e-131">La foto se puede guardar como JPG o PNG.</span><span class="sxs-lookup"><span data-stu-id="bc05e-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="bc05e-132">Si ha iniciado correctamente el modo fotográfico, tome una foto y almacénela en el disco</span><span class="sxs-lookup"><span data-stu-id="bc05e-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="bc05e-133">Después de capturar la foto en el disco, salga del modo fotográfico y limpie los objetos</span><span class="sxs-lookup"><span data-stu-id="bc05e-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="bc05e-134">Capturar una foto en un Texture2D</span><span class="sxs-lookup"><span data-stu-id="bc05e-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="bc05e-135">Al capturar datos en un Texture2D, el proceso es muy similar a la captura en disco.</span><span class="sxs-lookup"><span data-stu-id="bc05e-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="bc05e-136">Siga el proceso de configuración anterior.</span><span class="sxs-lookup"><span data-stu-id="bc05e-136">Follow the set up process above.</span></span>

<span data-ttu-id="bc05e-137">En *OnPhotoModeStarted*, Capture un fotograma en la memoria.</span><span class="sxs-lookup"><span data-stu-id="bc05e-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="bc05e-138">A continuación, se aplicará el resultado a una textura y se utilizará el código de limpieza común anterior.</span><span class="sxs-lookup"><span data-stu-id="bc05e-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="bc05e-139">Capturar una foto e interactuar con los bytes sin formato</span><span class="sxs-lookup"><span data-stu-id="bc05e-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="bc05e-140">Para interactuar con los bytes sin formato de un marco de memoria, siga los mismos pasos de configuración descritos anteriormente y *OnPhotoModeStarted* como en la captura de una foto en un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="bc05e-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="bc05e-141">La diferencia está en *OnCapturedPhotoToMemory* , donde puede obtener los bytes sin formato e interactuar con ellos.</span><span class="sxs-lookup"><span data-stu-id="bc05e-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="bc05e-142">En este ejemplo, creará una *lista<Color>* que se podría procesar o aplicar posteriormente a una textura mediante *SetPixels ()*</span><span class="sxs-lookup"><span data-stu-id="bc05e-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="bc05e-143">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="bc05e-143">Video Capture</span></span>

<span data-ttu-id="bc05e-144">**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="bc05e-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="bc05e-145">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="bc05e-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="bc05e-146">*VideoCapture* funciona de manera muy similar a la *fotocaptura*.</span><span class="sxs-lookup"><span data-stu-id="bc05e-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="bc05e-147">Las únicas dos diferencias son que debe especificar un valor de fotogramas por segundo (FPS) y solo puede guardar directamente en el disco como un archivo. MP4.</span><span class="sxs-lookup"><span data-stu-id="bc05e-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="bc05e-148">Los pasos para usar *VideoCapture* son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="bc05e-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="bc05e-149">Creación de un objeto de *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="bc05e-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="bc05e-150">Cree un objeto *CameraParameters* con los valores que desee.</span><span class="sxs-lookup"><span data-stu-id="bc05e-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="bc05e-151">Iniciar el modo de vídeo a través de *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="bc05e-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="bc05e-152">Iniciar grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="bc05e-152">Start recording video</span></span>
5. <span data-ttu-id="bc05e-153">Detener grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="bc05e-153">Stop recording video</span></span>
6. <span data-ttu-id="bc05e-154">Detener el modo de vídeo y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="bc05e-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="bc05e-155">Empiece por crear el objeto *VideoCapture* de *videocaptura m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="bc05e-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="bc05e-156">A continuación, configure los parámetros que desea para la grabación y el inicio.</span><span class="sxs-lookup"><span data-stu-id="bc05e-156">Next, set up the parameters you will want for the recording and start.</span></span>

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

<span data-ttu-id="bc05e-157">Una vez iniciado, comience la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc05e-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="bc05e-158">Una vez iniciada la grabación, puede actualizar la interfaz de usuario o los comportamientos para habilitar la detención.</span><span class="sxs-lookup"><span data-stu-id="bc05e-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="bc05e-159">Aquí solo tiene que registrar.</span><span class="sxs-lookup"><span data-stu-id="bc05e-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="bc05e-160">En un punto posterior, querrá detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc05e-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="bc05e-161">Esto puede deberse a un temporizador o a una entrada del usuario, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="bc05e-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="bc05e-162">Una vez que la grabación se ha detenido, detenga el modo de vídeo y limpie los recursos.</span><span class="sxs-lookup"><span data-stu-id="bc05e-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="bc05e-163">de solución de problemas</span><span class="sxs-lookup"><span data-stu-id="bc05e-163">Troubleshooting</span></span>
* <span data-ttu-id="bc05e-164">No hay ninguna solución disponible</span><span class="sxs-lookup"><span data-stu-id="bc05e-164">No resolutions are available</span></span>
    * <span data-ttu-id="bc05e-165">Asegúrese de que la funcionalidad de la **cámara web** está especificada en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bc05e-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc05e-166">Consulta también</span><span class="sxs-lookup"><span data-stu-id="bc05e-166">See Also</span></span>
* [<span data-ttu-id="bc05e-167">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="bc05e-167">Locatable camera</span></span>](locatable-camera.md)
