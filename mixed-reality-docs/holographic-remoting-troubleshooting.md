---
title: Solución de problemas y limitaciones de la comunicación remota holográfica
description: Pasos de solución de problemas para la comunicación remota holográfica en HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, Holographic Remoting, representación remota, representación en red, HoloLens, hologramas remotos, solución de problemas, ayuda
ms.openlocfilehash: 593b242326b83d4596d22a7e1a39ef18c26bc67a
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300507"
---
# <a name="holographic-remoting-troubleshooting"></a>Solución de problemas de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>No se encontraron bibliotecas mitigadas de Spectre.

Las aplicaciones de ejemplo de Holographic Remoting tienen habilitada la mitigación de Spectre (/Qspectre) en la configuración de versión.

Si obtiene un error irrecuperable del enlazador que indica que no se puede abrir ' vccorlib. lib ', asegúrese de que la carga de trabajo de Visual Studio incluye las bibliotecas mitigadas de Spectre. Consulte https://aka.ms/Ofhn4c para obtener más información.

## <a name="speech"></a>Voz

El reproductor de comunicación remota holográfica es compatible con una superposición de diagnósticos que se puede habilitar diciendo ```Enable Diagnostics``` y deshabilitando ```Disable Diagnostics``` . Si tiene problemas con estos comandos de voz, también puede iniciar el reproductor de acceso remoto holográfica a través de un explorador Web usando ```ms-holographic-remoting:?stats``` como dirección URL.

## <a name="h265-video-codec-not-available"></a>Códec de vídeo de H265 no disponible

Debe instalar las extensiones de [vídeo de HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) al usar el códec de vídeo H265 en la aplicación remota. Si surgen problemas en los que el códec está instalado pero no se pueden usar, consulte la guía de [solución de problemas](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) .

## <a name="limitations"></a>Limitaciones

Las siguientes API **no** se admiten actualmente cuando se usa Holographic Remoting para HoloLens 2 y generarán un ```ERROR_NOT_SUPPORTED``` error a menos que se indique lo contrario:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - En versiones anteriores siempre produce un error.
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - En versiones anteriores, no se produce un error, pero no se cambia el tamaño del destino de representación.
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - No genera ningún error, pero el búfer de profundidad no se realizará de forma remota.
  - Compatible a partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Al consultar HolographicViewConfigurationKind. PhotoVideoCamera, siempre se devolverá un ```nullptr``` .
  - Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - En versiones anteriores siempre produce un error.
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Notificará un error si se llama antes de que se establezca una conexión.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - En versiones anteriores, siempre devuelve ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - En versiones anteriores, siempre devuelve ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - En versiones anteriores, la operación asincrónica siempre se completaba con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager. RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - La operación asincrónica siempre se completa con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - La operación asincrónica siempre se completa con ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - La operación asincrónica siempre se completa con ```nullptr``` .

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Consulte también
* [Historial de versiones de Holographic Remoting](holographic-remoting-version-history.md)
* [Escritura de una aplicación remota de control remoto de holografías](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
