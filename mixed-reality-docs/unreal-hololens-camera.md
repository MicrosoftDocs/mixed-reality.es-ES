---
title: Cámara de foto y vídeo HoloLens en Unreal
description: Guía para usar la cámara de foto y vídeo HoloLens en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451340"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="1501e-104">Cámara de foto y vídeo HoloLens en Unreal</span><span class="sxs-lookup"><span data-stu-id="1501e-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="1501e-105">HoloLens tiene una cámara de foto y vídeo (PV) que se usa para la Captura de realidad mixta (MRC) y que una aplicación puede usar para acceder a los objetos visuales del mundo real.</span><span class="sxs-lookup"><span data-stu-id="1501e-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="1501e-106">Representación de la cámara PV para MRC</span><span class="sxs-lookup"><span data-stu-id="1501e-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="1501e-107">Se requiere **Unreal Engine 4.25** o versión posterior.</span><span class="sxs-lookup"><span data-stu-id="1501e-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="1501e-108">El sistema y las grabadoras de MRC personalizadas crean capturas de realidad mixta mediante la combinación de la cámara PV con hologramas representados por la aplicación inmersiva.</span><span class="sxs-lookup"><span data-stu-id="1501e-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="1501e-109">De forma predeterminada, la captura de realidad mixta usa la salida holográfica del ojo derecho.</span><span class="sxs-lookup"><span data-stu-id="1501e-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="1501e-110">Si una aplicación inmersiva elige la [representación de la cámara PV](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), se usará en su lugar.</span><span class="sxs-lookup"><span data-stu-id="1501e-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="1501e-111">Esto mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.</span><span class="sxs-lookup"><span data-stu-id="1501e-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="1501e-112">Para participar en la representación de la cámara PV:</span><span class="sxs-lookup"><span data-stu-id="1501e-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="1501e-113">Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="1501e-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="1501e-114">Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.</span><span class="sxs-lookup"><span data-stu-id="1501e-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Tercera cámara](images/unreal-camera-3rd.PNG)

<span data-ttu-id="1501e-116">Unreal controlará las solicitudes de MRC para representarlas desde la perspectiva de la cámara PV.</span><span class="sxs-lookup"><span data-stu-id="1501e-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="1501e-117">Solo cuando se desencadena la [Captura de realidad mixta](mixed-reality-capture.md), se pedirá a la aplicación que represente desde la perspectiva de la cámara de foto y vídeo.</span><span class="sxs-lookup"><span data-stu-id="1501e-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="1501e-118">Uso de la cámara PV</span><span class="sxs-lookup"><span data-stu-id="1501e-118">Using the PV Camera</span></span>

<span data-ttu-id="1501e-119">La textura de la cámara web se puede recuperar en el juego en tiempo de ejecución, pero debe habilitarse en la opción del editor **Editar > Configuración del proyecto**:</span><span class="sxs-lookup"><span data-stu-id="1501e-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="1501e-120">Vaya a **Plataformas > HoloLens > Capacidades** y marca **Cámara Web**.</span><span class="sxs-lookup"><span data-stu-id="1501e-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="1501e-121">Use la función **StartCameraCapture** para usar la cámara web en tiempo de ejecución y la función **StopCameraCapture** para detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="1501e-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Inicio y detención de la cámara](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="1501e-123">Representación de una imagen</span><span class="sxs-lookup"><span data-stu-id="1501e-123">Rendering an image</span></span>
<span data-ttu-id="1501e-124">Para representar la imagen de la cámara:</span><span class="sxs-lookup"><span data-stu-id="1501e-124">To render the camera image:</span></span>
1. <span data-ttu-id="1501e-125">Cree una instancia de material dinámico basada en un material del proyecto, que se denomine **PVCamMat** en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="1501e-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="1501e-126">Establezca la instancia de material dinámico en una variable de **referencia de objeto dinámico de instancia de material**.</span><span class="sxs-lookup"><span data-stu-id="1501e-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="1501e-127">Establezca el material del objeto en la escena que representará la fuente de la cámara para esta nueva instancia de material dinámico.</span><span class="sxs-lookup"><span data-stu-id="1501e-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="1501e-128">Inicie un temporizador que se usará para enlazar la imagen de la cámara al material.</span><span class="sxs-lookup"><span data-stu-id="1501e-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Representación de la cámara](images/unreal-camera-render.PNG)

4. <span data-ttu-id="1501e-130">Cree una nueva función para este temporizador, en este caso **MaterialTimer**, y llame a **GetARCameraImage** para obtener la textura de la cámara web.</span><span class="sxs-lookup"><span data-stu-id="1501e-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="1501e-131">Si esta textura es válida, defina un parámetro de textura en el sombreador para esta imagen.</span><span class="sxs-lookup"><span data-stu-id="1501e-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="1501e-132">De lo contrario, vuelve a iniciar el temporizador de materiales.</span><span class="sxs-lookup"><span data-stu-id="1501e-132">Otherwise, start the material timer again.</span></span> 

![Textura de cámara](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="1501e-134">Asegúrese de que el material tiene un parámetro que coincide con el nombre de **SetTextureParameterValue** que está enlazado a una entrada de color.</span><span class="sxs-lookup"><span data-stu-id="1501e-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="1501e-135">Sin esto, la imagen de la cámara no puede mostrarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="1501e-135">Without this, the camera image can't be properly displayed.</span></span>

![Textura de cámara](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="1501e-137">Consulta también</span><span class="sxs-lookup"><span data-stu-id="1501e-137">See also</span></span>
* [<span data-ttu-id="1501e-138">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="1501e-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="1501e-139">Captura de realidad mixta para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="1501e-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
