---
title: Objetos nativos de mixed Reality en Unity
description: Obtenga acceso a los objetos nativos holográficas subyacentes en Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, mixto en realidad, nativo, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942101"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Objetos nativos de mixed Reality en Unity

[Obtener un HolographicSpace](getting-a-holographicspace.md) es lo que rodea a cada aplicación se realiza antes de que comience a recibir datos de la cámara y la representación de realidad mixta. En Unity, el motor se encarga de esos pasos por usted, controlar objetos holográficas y actualiza internamente como parte de su bucle de representación.

Sin embargo, en escenarios avanzados es posible que deba obtener acceso a los objetos nativos subyacentes, como el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> actuales y <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> es lo que proporciona acceso a estos objetos nativos.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

El *XRDevice* tipo le permite obtener acceso a los objetos nativos subyacentes mediante la <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> método. ¿Qué devuelve GetNativePtr varía entre distintas plataformas. En la plataforma Universal de Windows, cuando el destino es Windows Mixed Reality XR SDK, XRDevice.GetNativePtr devuelve un puntero (IntPtr) a la siguiente estructura: 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
Se puede convertir a HolographicFrameNativeData mediante el método Marshal.PtrToStructure:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** es una matriz de IntPtr con una longitud igual a MaxNumberOfCameras calculan las referencias como UnmanagedType.ByValArray* 


### <a name="using-holographicframenativedata"></a>Uso de HolographicFrameNativeData

> [!NOTE]
> Cambiar el estado de los objetos nativos recibidos a través de HolographicFrameNativeData puede provocar un comportamiento impredecible y artefactos de representación, especialmente si también motivos de Unity sobre ese mismo estado.  Por ejemplo, no debe llamar a HolographicFrame.UpdateCurrentPrediction, o bien estará sincronizada con la postura que Windows está esperando, lo que reducirá la predicción de la postura que Unity se representa con ese marco [estabilidad holograma](hologram-stability.md).

Puede usar datos de HolographicFrameNativeData al acceso a las interfaces nativas se requiere para representar o depuración, en sus complementos nativos o C# código. 

Este es un ejemplo de cómo usar HolographicFrameNativeData para obtener la predicción del fotograma actual por vez photon. 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>Vea también
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Representación en DirectX](rendering-in-directx.md)
