---
title: Historial de versiones de Holographic Remoting
description: Historial de versiones de Holographic Remoting en HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181965"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="4b807-104">Historial de versiones de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4b807-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b807-105">Esta guía es específica de Holographic Remoting en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4b807-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="4b807-106">Versión 2.0.18.0 (17 de diciembre de 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="4b807-107">Compatibilidad agregada para HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="4b807-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="4b807-108">Se corrigieron varios errores que provocan bloqueos.</span><span class="sxs-lookup"><span data-stu-id="4b807-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="4b807-109">Se corrigió un error en el que se necesitaba una devolución de llamada HolographicSpace. CameraAdded para que un HolographicCamera se aceptara y se mostrara como una cámara agregada en el HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="4b807-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="4b807-110">Versión 2.0.16 (11 de noviembre de 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="4b807-111">Se corrigió el interbloqueo en el seguimiento del código QR.</span><span class="sxs-lookup"><span data-stu-id="4b807-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="4b807-112">Excepción de unhandeled corregida debido a una espera de bloqueo en el subproceso principal.</span><span class="sxs-lookup"><span data-stu-id="4b807-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="4b807-113">Versión 2.0.14 (26 de octubre de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="4b807-114">Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).</span><span class="sxs-lookup"><span data-stu-id="4b807-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="4b807-115">Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.</span><span class="sxs-lookup"><span data-stu-id="4b807-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="4b807-116">Problema de subprocesos corregido al usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="4b807-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="4b807-117">Versión 2.0.12 (18 de octubre de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="4b807-118">Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="4b807-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="4b807-119">Versión 2.0.10 (10 de octubre de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="4b807-120">Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR.</span><span class="sxs-lookup"><span data-stu-id="4b807-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="4b807-121">Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4b807-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="4b807-122">Versión 2.0.9 (19 de septiembre de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="4b807-123">Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="4b807-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="4b807-124">Agregada nueva ```IPlayerContext2``` de interfaz (implementada por ```PlayerContext```) que proporciona los siguientes miembros:</span><span class="sxs-lookup"><span data-stu-id="4b807-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="4b807-125">Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="4b807-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="4b807-126">Se agregó ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="4b807-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="4b807-127">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="4b807-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="4b807-128">Versión 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="4b807-129">Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.</span><span class="sxs-lookup"><span data-stu-id="4b807-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="4b807-130">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="4b807-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="4b807-131">Versión 2.0.7 (26 de julio de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="4b807-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="4b807-132">Primera versión pública de Holographic Remoting para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4b807-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b807-133">Consulta también</span><span class="sxs-lookup"><span data-stu-id="4b807-133">See Also</span></span>
* [<span data-ttu-id="4b807-134">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="4b807-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4b807-135">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4b807-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="4b807-136">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="4b807-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="4b807-137">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="4b807-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4b807-138">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="4b807-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
