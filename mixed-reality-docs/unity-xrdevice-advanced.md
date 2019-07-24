---
title: Objetos nativos de realidad mixta en Unity
description: Obtenga acceso a los objetos nativos holográficas subyacentes en Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942101"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="da3b8-104">Objetos nativos de realidad mixta en Unity</span><span class="sxs-lookup"><span data-stu-id="da3b8-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="da3b8-105">[Obtener un HolographicSpace](getting-a-holographicspace.md) es lo que hace cada aplicación de realidad mixta antes de empezar a recibir los datos de la cámara y los fotogramas de representación.</span><span class="sxs-lookup"><span data-stu-id="da3b8-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="da3b8-106">En Unity, el motor se encarga de esos pasos, ya que controla los objetos holográficas y las actualizaciones internamente como parte de su bucle de representación.</span><span class="sxs-lookup"><span data-stu-id="da3b8-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="da3b8-107">Sin embargo, en escenarios avanzados, puede que necesite obtener acceso a los objetos nativos subyacentes, como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> y <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuales.</span><span class="sxs-lookup"><span data-stu-id="da3b8-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="da3b8-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> es lo que proporciona acceso a estos objetos nativos.</span><span class="sxs-lookup"><span data-stu-id="da3b8-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="da3b8-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="da3b8-109">XRDevice</span></span> 

<span data-ttu-id="da3b8-110">**System.IO** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="da3b8-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="da3b8-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="da3b8-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="da3b8-112">El tipo *XRDevice* permite obtener acceso a los objetos nativos subyacentes mediante el método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="da3b8-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="da3b8-113">Lo que GetNativePtr devuelve varía entre distintas plataformas.</span><span class="sxs-lookup"><span data-stu-id="da3b8-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="da3b8-114">En el Plataforma universal de Windows, cuando el destino es el SDK de Windows Mixed Reality XR, XRDevice. GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente:</span><span class="sxs-lookup"><span data-stu-id="da3b8-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="da3b8-115">Puede convertirlo en HolographicFrameNativeData mediante el método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="da3b8-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="da3b8-116">***IHolographicCameraPtr** es una matriz de referencias de IntPtr calculadas como UnmanagedType. ByValArray con una longitud igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="da3b8-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="da3b8-117">Usar HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="da3b8-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="da3b8-118">Cambiar el estado de los objetos nativos recibidos a través de HolographicFrameNativeData puede producir artefactos de representación y comportamiento imprevisibles, especialmente si Unity también tiene por objeto el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="da3b8-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="da3b8-119">Por ejemplo, no debe llamar a HolographicFrame. UpdateCurrentPrediction o, de lo contrario, la predicción de supuestos que Unity representa con ese marco no estará sincronizada con la que espera Windows, lo que reducirá la [estabilidad del holograma](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="da3b8-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="da3b8-120">Puede usar datos de HolographicFrameNativeData cuando se necesita acceso a interfaces nativas para la representación o la depuración, en los complementos o C# el código nativo.</span><span class="sxs-lookup"><span data-stu-id="da3b8-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="da3b8-121">Este es un ejemplo de cómo se puede usar HolographicFrameNativeData para obtener la predicción del fotograma actual para la hora de Photon.</span><span class="sxs-lookup"><span data-stu-id="da3b8-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="da3b8-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="da3b8-122">See Also</span></span>
* <span data-ttu-id="da3b8-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="da3b8-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="da3b8-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="da3b8-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="da3b8-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="da3b8-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="da3b8-126">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="da3b8-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
