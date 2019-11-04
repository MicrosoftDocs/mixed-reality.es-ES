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
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="178d8-104">Objetos nativos de realidad mixta en Unity</span><span class="sxs-lookup"><span data-stu-id="178d8-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="178d8-105">[Obtener un HolographicSpace](getting-a-holographicspace.md) es lo que hace cada aplicación de realidad mixta antes de empezar a recibir los datos de la cámara y los fotogramas de representación.</span><span class="sxs-lookup"><span data-stu-id="178d8-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="178d8-106">En Unity, el motor se encarga de esos pasos, ya que controla los objetos holográficas y las actualizaciones internamente como parte de su bucle de representación.</span><span class="sxs-lookup"><span data-stu-id="178d8-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="178d8-107">Sin embargo, en escenarios avanzados, puede que necesite obtener acceso a los objetos nativos subyacentes, como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> y <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuales.</span><span class="sxs-lookup"><span data-stu-id="178d8-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="178d8-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> es lo que proporciona acceso a estos objetos nativos.</span><span class="sxs-lookup"><span data-stu-id="178d8-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="178d8-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="178d8-109">XRDevice</span></span> 

<span data-ttu-id="178d8-110">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="178d8-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="178d8-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="178d8-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="178d8-112">El tipo *XRDevice* permite obtener acceso a los objetos nativos subyacentes mediante el método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="178d8-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="178d8-113">Lo que GetNativePtr devuelve varía entre distintas plataformas.</span><span class="sxs-lookup"><span data-stu-id="178d8-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="178d8-114">En el Plataforma universal de Windows, cuando el destino es el SDK de Windows Mixed Reality XR, XRDevice. GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente:</span><span class="sxs-lookup"><span data-stu-id="178d8-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="178d8-115">Puede convertirlo en HolographicFrameNativeData mediante el método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="178d8-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="178d8-116">***IHolographicCameraPtr** es una matriz de referencias de IntPtr calculadas como UnmanagedType. ByValArray con una longitud igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="178d8-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="178d8-117">Anular serialización de punteros nativos</span><span class="sxs-lookup"><span data-stu-id="178d8-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="178d8-118">Si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) , puede construir un objeto administrado a partir de un puntero nativo mediante el método `FromNativePtr()`:</span><span class="sxs-lookup"><span data-stu-id="178d8-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="178d8-119">De lo contrario, use `Marshal.GetObjectForIUnknown()` y convierta al tipo deseado:</span><span class="sxs-lookup"><span data-stu-id="178d8-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="178d8-120">Convertir entre sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="178d8-120">Converting between coordinate systems</span></span>

<span data-ttu-id="178d8-121">Unity usa un sistema de coordenadas de la mano izquierda, mientras que las API de percepción de Windows usan sistemas de coordenadas a la derecha.</span><span class="sxs-lookup"><span data-stu-id="178d8-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="178d8-122">Para realizar la conversión entre estas dos convenciones, puede usar las siguientes aplicaciones auxiliares:</span><span class="sxs-lookup"><span data-stu-id="178d8-122">To convert between these two conventions, you can use the following helpers:</span></span>

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

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="178d8-123">Uso de datos nativos de HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="178d8-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="178d8-124">Cambiar el estado de los objetos nativos recibidos a través de HolographicFrameNativeData puede producir artefactos de representación y comportamiento imprevisibles, especialmente si Unity también tiene por objeto el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="178d8-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="178d8-125">Por ejemplo, no debe llamar a HolographicFrame. UpdateCurrentPrediction o, de lo contrario, la predicción de supuestos que Unity representa con ese marco no estará sincronizada con la que espera Windows, lo que reducirá la [estabilidad del holograma](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="178d8-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="178d8-126">Puede usar datos de HolographicFrameNativeData cuando se necesita acceso a interfaces nativas para la representación o la depuración, en los complementos o C# el código nativo.</span><span class="sxs-lookup"><span data-stu-id="178d8-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="178d8-127">Este es un ejemplo de cómo se puede usar HolographicFrameNativeData para obtener la predicción del fotograma actual para la hora de Photon.</span><span class="sxs-lookup"><span data-stu-id="178d8-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="178d8-128">Consulta también</span><span class="sxs-lookup"><span data-stu-id="178d8-128">See Also</span></span>
* [<span data-ttu-id="178d8-129">Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="178d8-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="178d8-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="178d8-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="178d8-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="178d8-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="178d8-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="178d8-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="178d8-133">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="178d8-133">Rendering in DirectX</span></span>](rendering-in-directx.md)
