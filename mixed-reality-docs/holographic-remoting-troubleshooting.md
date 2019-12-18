---
title: Solución de problemas y limitaciones de la comunicación remota holográfica
description: Pasos de solución de problemas para la comunicación remota holográfica en HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality, hologramas, Holographic Remoting, representación remota, representación en red, HoloLens, hologramas remotos, solución de problemas, ayuda
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181975"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="d1e82-104">Solución de problemas de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d1e82-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1e82-105">Esta guía es específica de Holographic Remoting en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d1e82-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="d1e82-106">No se encontraron bibliotecas mitigadas de Spectre.</span><span class="sxs-lookup"><span data-stu-id="d1e82-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="d1e82-107">Las aplicaciones de ejemplo de Holographic Remoting tienen habilitada la mitigación de Spectre (/Qspectre) en la configuración de versión.</span><span class="sxs-lookup"><span data-stu-id="d1e82-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="d1e82-108">Si obtiene un error irrecuperable del enlazador que indica que no se puede abrir ' vccorlib. lib ', asegúrese de que la carga de trabajo de Visual Studio incluye las bibliotecas mitigadas de Spectre.</span><span class="sxs-lookup"><span data-stu-id="d1e82-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="d1e82-109">Consulte https://aka.ms/Ofhn4c para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="d1e82-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="d1e82-110">Limitaciones</span><span class="sxs-lookup"><span data-stu-id="d1e82-110">Limitations</span></span>

<span data-ttu-id="d1e82-111">Las siguientes API **no** se admiten actualmente cuando se usa Holographic Remoting para HoloLens 2 y generarán un error ```ERROR_NOT_SUPPORTED``` a menos que se indique lo contrario:</span><span class="sxs-lookup"><span data-stu-id="d1e82-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="d1e82-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="d1e82-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="d1e82-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1e82-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="d1e82-114">Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="d1e82-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="d1e82-115">En versiones anteriores siempre produce un error.</span><span class="sxs-lookup"><span data-stu-id="d1e82-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="d1e82-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="d1e82-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="d1e82-117">No genera ningún error, pero no se cambiará el tamaño del destino de representación.</span><span class="sxs-lookup"><span data-stu-id="d1e82-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="d1e82-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="d1e82-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="d1e82-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="d1e82-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="d1e82-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="d1e82-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="d1e82-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="d1e82-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="d1e82-122">No genera ningún error, pero el búfer de profundidad no se realizará de forma remota.</span><span class="sxs-lookup"><span data-stu-id="d1e82-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="d1e82-123">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1e82-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="d1e82-124">Al consultar HolographicViewConfigurationKind. PhotoVideoCamera, siempre se devolverá un ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="d1e82-125">Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="d1e82-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="d1e82-126">En versiones anteriores siempre produce un error.</span><span class="sxs-lookup"><span data-stu-id="d1e82-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="d1e82-127">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="d1e82-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="d1e82-128">HolographicDisplay.GetDefault</span><span class="sxs-lookup"><span data-stu-id="d1e82-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="d1e82-129">Notificará un error si se llama antes de que se establezca una conexión.</span><span class="sxs-lookup"><span data-stu-id="d1e82-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="d1e82-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="d1e82-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="d1e82-131">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="d1e82-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="d1e82-132">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="d1e82-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="d1e82-133">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="d1e82-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="d1e82-134">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="d1e82-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="d1e82-135">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="d1e82-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="d1e82-136">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="d1e82-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="d1e82-137">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="d1e82-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="d1e82-138">Siempre devuelve ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="d1e82-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="d1e82-140">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="d1e82-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="d1e82-141">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="d1e82-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="d1e82-142">Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="d1e82-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="d1e82-143">En versiones anteriores, siempre devuelve ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="d1e82-144">SpatialAnchorExporter. RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="d1e82-145">Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="d1e82-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="d1e82-146">En versiones anteriores, la operación asincrónica siempre se completaba con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="d1e82-147">SpatialAnchorTransferManager. RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="d1e82-148">La operación asincrónica siempre se completa con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="d1e82-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="d1e82-150">La operación asincrónica siempre se completa con ```false```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="d1e82-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="d1e82-152">La operación asincrónica siempre se completa con ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="d1e82-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="d1e82-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="d1e82-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="d1e82-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="d1e82-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="d1e82-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="d1e82-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="d1e82-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="d1e82-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="d1e82-157">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="d1e82-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="d1e82-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="d1e82-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="d1e82-159">SpatialInteractionSource. Controller</span><span class="sxs-lookup"><span data-stu-id="d1e82-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="d1e82-160">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d1e82-160">See Also</span></span>
* [<span data-ttu-id="d1e82-161">Historial de versiones de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d1e82-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="d1e82-162">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d1e82-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="d1e82-163">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="d1e82-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="d1e82-164">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="d1e82-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="d1e82-165">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="d1e82-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
