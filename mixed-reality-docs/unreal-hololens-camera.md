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
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="47cb4-104">Cámara de HoloLens en Unreal</span><span class="sxs-lookup"><span data-stu-id="47cb4-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="47cb4-105">Captura de realidad mixta de la tercera cámara</span><span class="sxs-lookup"><span data-stu-id="47cb4-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="47cb4-106">La Captura de realidad mixta (MRC) de la tercera cámara se puede usar para representar una captura de realidad mixta desde la perspectiva de la cámara en el visor de HoloLens, en lugar de la perspectiva de las texturas del ojo.</span><span class="sxs-lookup"><span data-stu-id="47cb4-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="47cb4-107">Esto mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.</span><span class="sxs-lookup"><span data-stu-id="47cb4-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="47cb4-108">Para participar con MRC de tercera cámara, llama a SetEnabledMixedRealityCamera y ResizeMixedRealityCamera con las dimensiones de vídeo deseadas.</span><span class="sxs-lookup"><span data-stu-id="47cb4-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![Tercera cámara](images/unreal-camera-3rd.PNG)

<span data-ttu-id="47cb4-110">Después, graba un vídeo de MRC en el portal de dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="47cb4-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="47cb4-111">Cámara de foto y vídeo</span><span class="sxs-lookup"><span data-stu-id="47cb4-111">PV Camera</span></span>

<span data-ttu-id="47cb4-112">También se puede recuperar la textura de la cámara web en el juego en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="47cb4-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="47cb4-113">Para obtener la textura de la cámara web en HoloLens, asegúrate de que la funcionalidad "Webcam" esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades).</span><span class="sxs-lookup"><span data-stu-id="47cb4-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="47cb4-114">Para activar la cámara web en tiempo de ejecución, usa función StartCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="47cb4-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="47cb4-115">Detén la captura con la función StopCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="47cb4-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Inicio y detención de la cámara](images/unreal-camera-startstop.PNG)

<span data-ttu-id="47cb4-117">Para representar la imagen de la cámara, crea primero una instancia de material dinámico basada en un material del proyecto.</span><span class="sxs-lookup"><span data-stu-id="47cb4-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="47cb4-118">En este caso, basada en un material denominado PVCamMat.</span><span class="sxs-lookup"><span data-stu-id="47cb4-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="47cb4-119">Define este valor en una variable con el tipo Material Instance Dynamic Object Reference (Referencia de objeto dinámico de instancia de material).</span><span class="sxs-lookup"><span data-stu-id="47cb4-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="47cb4-120">A continuación, establece el material del objeto en la escena que representará la fuente de la cámara en esta nueva instancia de material dinámico e inicia un temporizador que se usará para enlazar la imagen de la cámara con el material.</span><span class="sxs-lookup"><span data-stu-id="47cb4-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![Representación de la cámara](images/unreal-camera-render.PNG)

<span data-ttu-id="47cb4-122">Crea una nueva función para este temporizador, en este caso, MaterialTimer, y llama a GetARCameraImage para obtener la textura de la cámara web.</span><span class="sxs-lookup"><span data-stu-id="47cb4-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="47cb4-123">Si esta textura es válida, define un parámetro de textura en el sombreador para esta imagen.</span><span class="sxs-lookup"><span data-stu-id="47cb4-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="47cb4-124">De lo contrario, vuelve a iniciar el temporizador de materiales.</span><span class="sxs-lookup"><span data-stu-id="47cb4-124">Otherwise, start the material timer again.</span></span> 

![Textura de cámara](images/unreal-camera-texture.PNG)

<span data-ttu-id="47cb4-126">El material debe tener un parámetro que coincida con el nombre de SetTextureParameterValue enlazado con una entrada de color para mostrar correctamente la imagen de la cámara.</span><span class="sxs-lookup"><span data-stu-id="47cb4-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![Textura de cámara](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="47cb4-128">Consulta también</span><span class="sxs-lookup"><span data-stu-id="47cb4-128">See also</span></span>
* [<span data-ttu-id="47cb4-129">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="47cb4-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="47cb4-130">Captura de realidad mixta para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="47cb4-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
