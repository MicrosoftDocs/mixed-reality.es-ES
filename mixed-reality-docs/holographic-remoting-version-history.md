---
title: Historial de versiones de Holographic Remoting
description: Historial de versiones de Holographic Remoting en HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 5ba3aaa8874dea4418114b331d3d99fc977e982c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278203"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="fa0c9-104">Historial de versiones de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="fa0c9-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa0c9-105">Esta guía es específica de Holographic Remoting en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="fa0c9-106">Versión 2.1.0 (11 de marzo de 2020)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="fa0c9-107">Transporte de red conmutada para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) a través de UDP.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="fa0c9-108">Conexiones seguras use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) ahora.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="fa0c9-109">Tenga en cuenta que el [reproductor de comunicación remota holográfica](holographic-remoting-player.md) todavía es compatible con todas las versiones anteriores de Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="fa0c9-110">Para beneficiarse del nuevo transporte de red, el reproductor de comunicación remota holográfica y la aplicación remota en cuestión deben usar la versión 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="fa0c9-111">Compatibilidad agregada para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="fa0c9-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="fa0c9-112">Versión 2.0.20 (2 de febrero de 2020)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="fa0c9-113">Se corrigieron varios errores que provocan bloqueos.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-113">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="fa0c9-114">Versión 2.0.18 (17 de diciembre de 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="fa0c9-115">Compatibilidad agregada para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span><span class="sxs-lookup"><span data-stu-id="fa0c9-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="fa0c9-116">Se corrigieron varios errores que provocan bloqueos.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="fa0c9-117">Se corrigió un error en el que se necesitaba una devolución de llamada HolographicSpace. CameraAdded para que un HolographicCamera se aceptara y se mostrara como una cámara agregada en el HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="fa0c9-118">Versión 2.0.16 (11 de noviembre de 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="fa0c9-119">Se corrigió el interbloqueo en el seguimiento del código QR.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="fa0c9-120">Excepción de unhandeled corregida debido a una espera de bloqueo en el subproceso principal.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="fa0c9-121">Versión 2.0.14 (26 de octubre de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="fa0c9-122">Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).</span><span class="sxs-lookup"><span data-stu-id="fa0c9-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="fa0c9-123">Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="fa0c9-124">Problema de subprocesos corregido al usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="fa0c9-125">Versión 2.0.12 (18 de octubre de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="fa0c9-126">Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="fa0c9-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="fa0c9-127">Versión 2.0.10 (10 de octubre de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="fa0c9-128">Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="fa0c9-129">Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="fa0c9-130">Versión 2.0.9 (19 de septiembre de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="fa0c9-131">Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="fa0c9-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="fa0c9-132">Agregada nueva ```IPlayerContext2``` de interfaz (implementada por ```PlayerContext```) que proporciona los siguientes miembros:</span><span class="sxs-lookup"><span data-stu-id="fa0c9-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="fa0c9-133">Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="fa0c9-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="fa0c9-134">Se agregó ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="fa0c9-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="fa0c9-135">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="fa0c9-135">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="fa0c9-136">Versión 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="fa0c9-137">Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="fa0c9-138">Mejoras en la estabilidad y confiabilidad</span><span class="sxs-lookup"><span data-stu-id="fa0c9-138">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="fa0c9-139">Versión 2.0.7 (26 de julio de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="fa0c9-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="fa0c9-140">Primera versión pública de Holographic Remoting para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa0c9-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa0c9-141">Consulta también</span><span class="sxs-lookup"><span data-stu-id="fa0c9-141">See Also</span></span>
* [<span data-ttu-id="fa0c9-142">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="fa0c9-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="fa0c9-143">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="fa0c9-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="fa0c9-144">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="fa0c9-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="fa0c9-145">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="fa0c9-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="fa0c9-146">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="fa0c9-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
