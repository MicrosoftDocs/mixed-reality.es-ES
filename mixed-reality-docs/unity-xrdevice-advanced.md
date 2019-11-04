---
title: Objetos nativos de realidad mixta en Unity
description: Obtenga acceso a los objetos nativos holográficas subyacentes en Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437337"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Objetos nativos de realidad mixta en Unity

[Obtener un HolographicSpace](getting-a-holographicspace.md) es lo que hace cada aplicación de realidad mixta antes de empezar a recibir los datos de la cámara y los fotogramas de representación. En Unity, el motor se encarga de esos pasos, ya que controla los objetos holográficas y las actualizaciones internamente como parte de su bucle de representación.

Sin embargo, en escenarios avanzados, puede que necesite obtener acceso a los objetos nativos subyacentes, como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> y <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuales. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> es lo que proporciona acceso a estos objetos nativos.

## <a name="xrdevice"></a>XRDevice 

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

El tipo *XRDevice* permite obtener acceso a los objetos nativos subyacentes mediante el método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Lo que GetNativePtr devuelve varía entre distintas plataformas. En el Plataforma universal de Windows, cuando el destino es el SDK de Windows Mixed Reality XR, XRDevice. GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente: 

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
Puede convertirlo en HolographicFrameNativeData mediante el método Marshal. PtrToStructure:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** es una matriz de referencias de IntPtr calculadas como UnmanagedType. ByValArray con una longitud igual a MaxNumberOfCameras* 

### <a name="unmarshaling-native-pointers"></a>Anular serialización de punteros nativos

Si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) , puede construir un objeto administrado a partir de un puntero nativo mediante el método `FromNativePtr()`:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

De lo contrario, use `Marshal.GetObjectForIUnknown()` y convierta al tipo deseado:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>Convertir entre sistemas de coordenadas

Unity usa un sistema de coordenadas de la mano izquierda, mientras que las API de percepción de Windows usan sistemas de coordenadas a la derecha. Para realizar la conversión entre estas dos convenciones, puede usar las siguientes aplicaciones auxiliares:

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>Uso de datos nativos de HolographicFrame

> [!NOTE]
> Cambiar el estado de los objetos nativos recibidos a través de HolographicFrameNativeData puede producir artefactos de representación y comportamiento imprevisibles, especialmente si Unity también tiene por objeto el mismo estado.  Por ejemplo, no debe llamar a HolographicFrame. UpdateCurrentPrediction o, de lo contrario, la predicción de supuestos que Unity representa con ese marco no estará sincronizada con la que espera Windows, lo que reducirá la [estabilidad del holograma](hologram-stability.md).

Puede usar datos de HolographicFrameNativeData cuando se necesita acceso a interfaces nativas para la representación o la depuración, en los complementos o C# el código nativo. 

Este es un ejemplo de cómo se puede usar HolographicFrameNativeData para obtener la predicción del fotograma actual para la hora de Photon. 
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

## <a name="see-also"></a>Consulta también
* [Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Representación en DirectX](rendering-in-directx.md)
