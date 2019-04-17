---
title: Uso de WebVR en Microsoft Edge con Windows Mixed Reality
description: Información general de uso y desarrollo de WebVR en Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 vídeo 360 vídeos, fotografías 360, 360 fotos, contenido 360, envolvente, web immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605691"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="5ce6e-104">Uso de WebVR en Microsoft Edge con Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5ce6e-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="5ce6e-105">Creación de contenido de WebVR para Windows Mixed reality inmersivos</span><span class="sxs-lookup"><span data-stu-id="5ce6e-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="5ce6e-106">WebVR 1.1 está disponible en el Windows 10 Fall Creators Update a partir de Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="5ce6e-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="5ce6e-107">Los desarrolladores ahora pueden usar esta API para crear experiencias envolventes de realidad virtual en la web.</span><span class="sxs-lookup"><span data-stu-id="5ce6e-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="5ce6e-108">La API de WebVR proporciona datos de la postura HMD a la página que se puede usar para representar un escena WebGL estéreo el HMD.</span><span class="sxs-lookup"><span data-stu-id="5ce6e-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="5ce6e-109">Obtener más información sobre la compatibilidad con la API está disponible en el [página de estado de la plataforma de Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="5ce6e-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="5ce6e-110">El área expuesta de API WebVR está presente en todo momento dentro de Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="5ce6e-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="5ce6e-111">Sin embargo, una llamada a getVRDisplays() solo devolverá un auricular si está conectado auriculares o se ha activado el simulador.</span><span class="sxs-lookup"><span data-stu-id="5ce6e-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="5ce6e-112">Visualización de contenido de WebVR en inmersivos Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5ce6e-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="5ce6e-113">Puede encontrar instrucciones para tener acceso al contenido de WebVR en los auriculares envolventes en la [guía entusiastas](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="5ce6e-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ce6e-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="5ce6e-114">See Also</span></span>
* [<span data-ttu-id="5ce6e-115">Información de WebVR</span><span class="sxs-lookup"><span data-stu-id="5ce6e-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="5ce6e-116">Especificación de WebVR</span><span class="sxs-lookup"><span data-stu-id="5ce6e-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="5ce6e-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="5ce6e-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="5ce6e-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="5ce6e-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="5ce6e-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [Gamepad extensiones](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="5ce6e-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="5ce6e-120">Control que pierde el contexto en WebGL</span><span class="sxs-lookup"><span data-stu-id="5ce6e-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="5ce6e-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="5ce6e-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="5ce6e-122">glTF</span><span class="sxs-lookup"><span data-stu-id="5ce6e-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="5ce6e-123">Uso de Babylon.js para habilitar WebVR</span><span class="sxs-lookup"><span data-stu-id="5ce6e-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

