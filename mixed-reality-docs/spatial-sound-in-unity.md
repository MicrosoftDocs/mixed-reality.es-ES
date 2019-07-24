---
title: Sonido espacial en Unity
description: Reproducir un sonido espacial procedente de un punto 3D específico dentro de la escena de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549079"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="46b20-104">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-104">Spatial sound in Unity</span></span>

<span data-ttu-id="46b20-105">En este tema se describe cómo usar el sonido espacial en los proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="46b20-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="46b20-106">Trata los archivos de complemento necesarios, así como los componentes y propiedades de Unity que permiten el sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="46b20-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="46b20-107">Habilitación del sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="46b20-108">El sonido espacial, en Unity, se habilita mediante un complemento de spatializer de audio.</span><span class="sxs-lookup"><span data-stu-id="46b20-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="46b20-109">Los archivos de complemento se agrupan directamente en Unity, por lo que habilitar el sonido espacial es tan sencillo como **editar > configuración del proyecto > audio** y cambiar el **complemento Spatializer** en el inspector al **Spatializer MS HRTF**.</span><span class="sxs-lookup"><span data-stu-id="46b20-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="46b20-110">Dado que Microsoft spatializer solo admite 48000Hz actualmente, también debe establecer la velocidad de muestra del sistema en 48000 para evitar un error de HRTF en el caso excepcional de que el dispositivo de salida del sistema no esté establecido en 48000 ya:</span><span class="sxs-lookup"><span data-stu-id="46b20-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="46b20-111">![Inspector para AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="46b20-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="46b20-112">*Inspector para AudioManager*</span><span class="sxs-lookup"><span data-stu-id="46b20-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="46b20-113">El proyecto de Unity ya está configurado para usar el sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="46b20-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="46b20-114">Si no usa un equipo con Windows 10 para el desarrollo, no obtendrá sonido espacial en el editor ni en el dispositivo (incluso si usa el SDK de Windows 10).</span><span class="sxs-lookup"><span data-stu-id="46b20-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="46b20-115">Uso de sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="46b20-116">El sonido espacial se usa en el proyecto de Unity ajustando tres opciones en los componentes de origen de audio.</span><span class="sxs-lookup"><span data-stu-id="46b20-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="46b20-117">En los pasos siguientes se configurarán los componentes de origen de audio para el sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="46b20-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="46b20-118">En el panel **jerarquía** , seleccione el objeto de juego que tiene un **origen de audio**conectado.</span><span class="sxs-lookup"><span data-stu-id="46b20-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="46b20-119">En el panel **Inspector** , en el componente **origen de audio**</span><span class="sxs-lookup"><span data-stu-id="46b20-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="46b20-120">Active la opción **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="46b20-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="46b20-121">Establezca **Blend espacial** en **3D** (valor numérico 1).</span><span class="sxs-lookup"><span data-stu-id="46b20-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="46b20-122">Para obtener los mejores resultados, expanda la **opción Configuración de sonido 3D** y establezca el **volumen rolloff** en **rolloff personalizado**.</span><span class="sxs-lookup"><span data-stu-id="46b20-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="46b20-123">![Panel de inspector en Unity que muestra el origen de audio](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="46b20-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="46b20-124">*Panel de inspector en Unity que muestra el origen de audio*</span><span class="sxs-lookup"><span data-stu-id="46b20-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="46b20-125">Sus sonidos ahora existen en el entorno del proyecto.</span><span class="sxs-lookup"><span data-stu-id="46b20-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="46b20-126">Se recomienda encarecidamente que se familiarice con las [directrices de diseño de sonido espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="46b20-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="46b20-127">Estas instrucciones ayudan a integrar el audio sin problemas en el proyecto y a sumergir aún más a los usuarios en la experiencia que ha creado.</span><span class="sxs-lookup"><span data-stu-id="46b20-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="46b20-128">Establecer la configuración de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="46b20-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="46b20-129">El complemento de sonido espacial de Microsoft proporciona un parámetro adicional que se puede establecer en cada origen de audio para permitir un control adicional de la simulación de audio.</span><span class="sxs-lookup"><span data-stu-id="46b20-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="46b20-130">Este parámetro es el tamaño del salón simulado.</span><span class="sxs-lookup"><span data-stu-id="46b20-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="46b20-131">Tamaño de sala</span><span class="sxs-lookup"><span data-stu-id="46b20-131">Room Size</span></span>

<span data-ttu-id="46b20-132">El tamaño de la habitación que simula el sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="46b20-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="46b20-133">Los tamaños aproximados de los salones son; pequeña (una oficina a una pequeña sala de conferencias), mediana (una gran sala de conferencias) y grande (un auditorio).</span><span class="sxs-lookup"><span data-stu-id="46b20-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="46b20-134">También puede especificar un tamaño de sala de ninguno para simular un entorno exterior.</span><span class="sxs-lookup"><span data-stu-id="46b20-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="46b20-135">El tamaño predeterminado de la sala es pequeño.</span><span class="sxs-lookup"><span data-stu-id="46b20-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="46b20-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="46b20-136">Example</span></span>

<span data-ttu-id="46b20-137">MixedRealityToolkit para Unity proporciona una clase estática que facilita el establecimiento de la configuración de sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="46b20-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="46b20-138">Esta clase se puede encontrar en la [carpeta MixedRealityToolkit\SpatialSound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) y se puede llamar desde cualquier script del proyecto.</span><span class="sxs-lookup"><span data-stu-id="46b20-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="46b20-139">Se recomienda establecer estos parámetros en cada componente de origen de audio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="46b20-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="46b20-140">En el ejemplo siguiente se muestra cómo seleccionar el tamaño de la sala mediana para un origen de audio conectado.</span><span class="sxs-lookup"><span data-stu-id="46b20-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="46b20-141">Acceso directo a los parámetros desde Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="46b20-142">Si no desea usar las excelentes herramientas de audio de MixedRealityToolkit, aquí se indica cómo cambiar los parámetros de HRTF.</span><span class="sxs-lookup"><span data-stu-id="46b20-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="46b20-143">Puede copiarlo y pegarlo en un script denominado *SetHRTF.CS* que quiera asociar a cada AUDIOSOURCE de HRTF.</span><span class="sxs-lookup"><span data-stu-id="46b20-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="46b20-144">Permite cambiar los parámetros importantes a HRTF.</span><span class="sxs-lookup"><span data-stu-id="46b20-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="46b20-145">Sonido espacial en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="46b20-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="46b20-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest. Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="46b20-147">Los ejemplos siguientes del kit de herramientas de realidad mixta son ejemplos de efectos de audio generales que muestran formas de hacer que sus experiencias sean más envolventes mediante el uso de sonido.</span><span class="sxs-lookup"><span data-stu-id="46b20-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="46b20-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest. Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="46b20-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest. Unity</span><span class="sxs-lookup"><span data-stu-id="46b20-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="46b20-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="46b20-150">See also</span></span>
* [<span data-ttu-id="46b20-151">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="46b20-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="46b20-152">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="46b20-152">Spatial sound design</span></span>](spatial-sound-design.md)
