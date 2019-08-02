---
title: Solución de problemas y limitaciones de la comunicación remota holográfica
description: Pasos de solución de problemas para la comunicación remota holográfica en HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, hologramas, Holographic Remoting, representación remota, representación en red, HoloLens, hologramas remotos, solución de problemas, ayuda
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718149"
---
# <a name="holographic-remoting-troubleshooting"></a>Solución de problemas de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>No se encontraron bibliotecas mitigadas de Spectre.

Las aplicaciones de ejemplo de Holographic Remoting tienen habilitada la mitigación de Spectre (/Qspectre) en la configuración de versión.

Si obtiene un error irrecuperable del enlazador que indica que no se puede abrir ' vccorlib. lib ', asegúrese de que la carga de trabajo de Visual Studio incluye las bibliotecas mitigadas de Spectre. Consulte https://aka.ms/Ofhn4c para obtener más información.

# <a name="limitations"></a>Limitaciones

Las siguientes API **no** se admiten actualmente cuando se usa Holographic Remoting para HoloLens 2 y ```ERROR_NOT_SUPPORTED``` generarán un error a menos que se indique lo contrario:

[Windows.Graphics.Holographic](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) : no se produce un error, pero el búfer de profundidad no se realizará de forma remota.
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[Windows.Perception.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation. AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation. AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) : siempre devuelve ```nullptr```.
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter. GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) : siempre devuelve ```nullptr```.
* [SpatialAnchorExporter. RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) : la operación asincrónica siempre se completa ```SpatialPerceptionAccessStatus.DeniedBySystem```con.
* [SpatialAnchorTransferManager. RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) : la operación asincrónica siempre se completa ```SpatialPerceptionAccessStatus.DeniedBySystem```con.
* [SpatialAnchorTransferManager. TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) : la operación asincrónica siempre se completa ```false```con.
* [SpatialAnchorTransferManager. TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) : la operación asincrónica siempre se completa ```nullptr```con.

[Windows.UI.Input.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Vea también
* [Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Términos de licencia del software de Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)