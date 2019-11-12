---
title: Historial de versiones de Holographic Remoting
description: Historial de versiones de Holographic Remoting en HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 9ff6a5f7594eb67dd4c1c8690812ab724cac9012
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926647"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="94427-104">Historial de versiones de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="94427-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94427-105">Esta guía es específica de Holographic Remoting en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="94427-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="94427-106">Versión 2.0.14 (26 de octubre de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="94427-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="94427-107">Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).</span><span class="sxs-lookup"><span data-stu-id="94427-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="94427-108">Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.</span><span class="sxs-lookup"><span data-stu-id="94427-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="94427-109">Problema de subprocesos corregido al usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="94427-109">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="94427-110">Versión 2.0.12 (18 de octubre de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="94427-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="94427-111">Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="94427-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="94427-112">Versión 2.0.10 (10 de octubre de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="94427-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="94427-113">Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR.</span><span class="sxs-lookup"><span data-stu-id="94427-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="94427-114">Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="94427-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="94427-115">Versión 2.0.9 (19 de septiembre de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="94427-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="94427-116">Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="94427-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="94427-117">Agregada nueva ```IPlayerContext2``` de interfaz (implementada por ```PlayerContext```) que proporciona los siguientes miembros:</span><span class="sxs-lookup"><span data-stu-id="94427-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="94427-118">Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="94427-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="94427-119">Se agregó ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="94427-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="94427-120">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="94427-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="94427-121">Versión 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="94427-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="94427-122">Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.</span><span class="sxs-lookup"><span data-stu-id="94427-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="94427-123">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="94427-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="94427-124">Versión 2.0.7 (26 de julio de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="94427-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="94427-125">Primera versión pública de Holographic Remoting para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="94427-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="94427-126">Consulta también</span><span class="sxs-lookup"><span data-stu-id="94427-126">See Also</span></span>
* [<span data-ttu-id="94427-127">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="94427-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="94427-128">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="94427-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="94427-129">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="94427-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="94427-130">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="94427-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="94427-131">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="94427-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
