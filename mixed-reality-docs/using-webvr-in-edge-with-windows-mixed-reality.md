---
title: Uso de WebVR en Microsoft Edge con Windows Mixed Reality
description: Información general sobre el uso y desarrollo para WebVR en Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, webxr, Web Mr, WebAr, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 photos, 360 Content, Web inmersivo, immersiveweb, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437204"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="d337b-104">Uso de WebVR en Microsoft Edge con Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d337b-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="d337b-105">Creación de contenido de WebVR para auriculares con Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d337b-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="d337b-106">WebVR 1,1 está disponible en Microsoft Edge a partir de Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="d337b-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="d337b-107">Los desarrolladores ahora pueden usar esta API para crear experiencias de VR envolventes en la Web.</span><span class="sxs-lookup"><span data-stu-id="d337b-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="d337b-108">La API WebVR proporciona datos de representación de HMD a la página que se puede usar para volver a presentar una escena WebGL de estéreo a la HMD.</span><span class="sxs-lookup"><span data-stu-id="d337b-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="d337b-109">Los detalles sobre la compatibilidad con la API están disponibles en la [Página estado de la plataforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="d337b-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="d337b-110">El área expuesta de la API de WebVR está presente en todo momento dentro de Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="d337b-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="d337b-111">Sin embargo, una llamada a getVRDisplays () solo devolverá un auricular Si se enchufa un casco o si se ha activado el simulador.</span><span class="sxs-lookup"><span data-stu-id="d337b-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="d337b-112">Visualización del contenido de WebVR en auriculares Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d337b-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="d337b-113">Las instrucciones para obtener acceso al contenido de WebVR en los auriculares que se encuentran en el casco se pueden encontrar en la [Guía del entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="d337b-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="d337b-114">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d337b-114">See Also</span></span>
* [<span data-ttu-id="d337b-115">Información de WebVR</span><span class="sxs-lookup"><span data-stu-id="d337b-115">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="d337b-116">Especificación de WebVR</span><span class="sxs-lookup"><span data-stu-id="d337b-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="d337b-117">[API de WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d337b-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="d337b-118">[API de WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d337b-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="d337b-119">[API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [extensiones de controlador](https://w3c.github.io/gamepad/extensions.html) para juegos</span><span class="sxs-lookup"><span data-stu-id="d337b-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="d337b-120">Controlar el contexto perdido en WebGL</span><span class="sxs-lookup"><span data-stu-id="d337b-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="d337b-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="d337b-121">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="d337b-122">glTF</span><span class="sxs-lookup"><span data-stu-id="d337b-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="d337b-123">Uso de Babylon. js para habilitar WebVR</span><span class="sxs-lookup"><span data-stu-id="d337b-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

