---
title: Sonido espacial en Unity
description: Reproducir sonido espacial procede de un punto 3D específico dentro de la escena de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, espacial de sonido, HRTF, tamaño de la sala
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597517"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="b2f9f-104">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-104">Spatial sound in Unity</span></span>

<span data-ttu-id="b2f9f-105">Este tema describe cómo usar sonido espacial en los proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="b2f9f-106">Trata los archivos de complemento, así como los componentes de Unity y propiedades que permiten sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="b2f9f-107">Habilitar el sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="b2f9f-108">Sonido espacial, en Unity, se habilita mediante un complemento de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="b2f9f-109">Los archivos del complemento se agrupan directamente en Unity para habilitar el sonido espacial es tan fácil como va a **Editar > configuración del proyecto > Audio** y cambiando el **espacial complemento** en el Inspector de la  **MS HRTF espacial**.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="b2f9f-110">Puesto que el efecto de espacio de Microsoft solo admite actualmente 48000Hz, también se debe establecer la frecuencia de muestreo del sistema como 48000 para evitar un error HRTF en el caso excepcional de que el dispositivo de salida del sistema ya no se establece en 48000:</span><span class="sxs-lookup"><span data-stu-id="b2f9f-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="b2f9f-111">![Inspector de AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="b2f9f-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="b2f9f-112">*Inspector de AudioManager*</span><span class="sxs-lookup"><span data-stu-id="b2f9f-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="b2f9f-113">El proyecto de Unity ahora está configurado para usar un sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="b2f9f-114">Si no está utilizando un equipo con Windows 10 para el desarrollo, no obtendrá espacial sonido en el editor ni en el dispositivo (incluso si está usando el SDK de Windows 10).</span><span class="sxs-lookup"><span data-stu-id="b2f9f-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="b2f9f-115">Uso de sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="b2f9f-116">Sonido espacial se usa en su proyecto Unity mediante el ajuste de configuración de tres de los componentes de origen de Audio.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="b2f9f-117">Los pasos siguientes configurará los componentes de origen de Audio de sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="b2f9f-118">En el **jerarquía** del panel, seleccione el objeto de juego que tenga adjunta **origen Audio**.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="b2f9f-119">En el **Inspector** panel, en el **origen Audio** componente</span><span class="sxs-lookup"><span data-stu-id="b2f9f-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="b2f9f-120">Compruebe el **Spatialize** opción.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="b2f9f-121">Establecer **Blend espacial** a **3D** (valor numérico 1).</span><span class="sxs-lookup"><span data-stu-id="b2f9f-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="b2f9f-122">Para obtener mejores resultados, expanda **configuración sonido 3D** y establecer **atenuación de volumen** a **personalizado atenuación**.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="b2f9f-123">![Panel del inspector de Unity que muestra el origen de Audio](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="b2f9f-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="b2f9f-124">*Panel del inspector de Unity que muestra el origen de Audio*</span><span class="sxs-lookup"><span data-stu-id="b2f9f-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="b2f9f-125">Ahora los sonidos de forma realista existen dentro del entorno del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="b2f9f-126">Se recomienda encarecidamente que se familiarice con la [instrucciones de diseño de sonido espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="b2f9f-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="b2f9f-127">Estas directrices ayudar a integrar el audio a la perfección en su proyecto y Sumergir aún más los usuarios en la experiencia que ha creado.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="b2f9f-128">Configuración de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="b2f9f-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="b2f9f-129">El complemento de Microsoft Spatial Sound proporciona un parámetro adicional que se puede establecer en una por cada origen de Audio, para permitir que un control adicional de la simulación de audio.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="b2f9f-130">Este parámetro es el tamaño de la sala simulado.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="b2f9f-131">Tamaño de la sala</span><span class="sxs-lookup"><span data-stu-id="b2f9f-131">Room Size</span></span>

<span data-ttu-id="b2f9f-132">El tamaño de la sala simulada mediante sonido espacial.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="b2f9f-133">El tamaño aproximado de las salas es: pequeño (una oficina en una sala de conferencias pequeño), mediano (una sala de conferencias de gran tamaño) y grande (un auditorio).</span><span class="sxs-lookup"><span data-stu-id="b2f9f-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="b2f9f-134">También puede especificar un tamaño de la sala None para simular un entorno al aire libre.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="b2f9f-135">El tamaño del espacio predeterminado es pequeño.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="b2f9f-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b2f9f-136">Example</span></span>

<span data-ttu-id="b2f9f-137">El MixedRealityToolkit para Unity proporciona una clase estática que hace que la configuración de sonido espacial fácil.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="b2f9f-138">Esta clase puede encontrarse en el [MixedRealityToolkit\SpatialSound carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) y se puede llamar desde cualquier secuencia de comandos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="b2f9f-139">Se recomienda establecer estos parámetros en cada componente de origen de Audio en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="b2f9f-140">El ejemplo siguiente muestra si selecciona el tamaño del espacio medio para un origen de Audio asociado.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="b2f9f-141">Acceso directo a los parámetros de Unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="b2f9f-142">Si no desea utilizar las excelentes herramientas de Audio en el MixedRealityToolkit, mostramos cómo cambiaría la HRTF parámetros.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="b2f9f-143">Se puede copiar y pegar esto en un script denominado *SetHRTF.cs* que desea asociar a cada AudioSource HRTF.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="b2f9f-144">Permite cambiar los parámetros importantes para la HRTF.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="b2f9f-145">Sonido espacial en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b2f9f-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="b2f9f-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="b2f9f-147">Los siguientes ejemplos desde el Kit de herramientas de realidad mixta son ejemplos de efecto de audio general que demuestran formas de hacer sus experiencias más envolventes mediante el uso de sonido.</span><span class="sxs-lookup"><span data-stu-id="b2f9f-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="b2f9f-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="b2f9f-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="b2f9f-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="b2f9f-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="b2f9f-150">See also</span></span>
* [<span data-ttu-id="b2f9f-151">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="b2f9f-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b2f9f-152">Diseño espacial de sonido</span><span class="sxs-lookup"><span data-stu-id="b2f9f-152">Spatial sound design</span></span>](spatial-sound-design.md)
