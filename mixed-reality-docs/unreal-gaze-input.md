---
title: Mira fijamente inrealmente
description: Tutorial sobre la configuración de la entrada de fijamente para HoloLens y el motor no real
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada por cabeza, motor no real
ms.openlocfilehash: c77e33df2a1dfffdb5ea55e685d30af3fc2a22da
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330627"
---
# <a name="gaze-input"></a><span data-ttu-id="51b5c-104">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="51b5c-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="51b5c-105">Información general</span><span class="sxs-lookup"><span data-stu-id="51b5c-105">Overview</span></span>

<span data-ttu-id="51b5c-106">El [complemento de Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) no proporciona funciones integradas para la entrada de mirada, pero HoloLens 2 admite el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="51b5c-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="51b5c-107">Las características de seguimiento reales son proporcionadas por las API de seguimiento de visualización y **seguimiento** de los **cabezales** y incluyen:</span><span class="sxs-lookup"><span data-stu-id="51b5c-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="51b5c-108">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="51b5c-108">Device information</span></span>
- <span data-ttu-id="51b5c-109">Sensores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="51b5c-109">Tracking sensors</span></span>
- <span data-ttu-id="51b5c-110">Orientación y posición</span><span class="sxs-lookup"><span data-stu-id="51b5c-110">Orientation and position</span></span>
- <span data-ttu-id="51b5c-111">Recorte de paneles</span><span class="sxs-lookup"><span data-stu-id="51b5c-111">Clipping panes</span></span>
- <span data-ttu-id="51b5c-112">Mira la información de datos y seguimiento</span><span class="sxs-lookup"><span data-stu-id="51b5c-112">Gaze data and tracking information</span></span>

<span data-ttu-id="51b5c-113">Puede encontrar una lista completa de las características en la documentación de la pantalla y el [seguimiento](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) de los ojos [montados](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .</span><span class="sxs-lookup"><span data-stu-id="51b5c-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span> 

<span data-ttu-id="51b5c-114">Además de las API no reales, consulte la documentación sobre la [interacción basada en miras](eye-gaze-interaction.md) en la vista de hololens 2 y lea cómo funciona el [seguimiento ocular en hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="51b5c-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51b5c-115">El seguimiento ocular solo se admite en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="51b5c-115">Eye tracking is only supported on HoloLens 2.</span></span> 

## <a name="enabling-eye-tracking"></a><span data-ttu-id="51b5c-116">Habilitación del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="51b5c-116">Enabling eye tracking</span></span>
<span data-ttu-id="51b5c-117">La entrada de mirada debe estar habilitada en la configuración del proyecto de HoloLens antes de poder usar cualquiera de las API de inreal.</span><span class="sxs-lookup"><span data-stu-id="51b5c-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="51b5c-118">Cuando se inicie la aplicación, verá una solicitud de consentimiento que se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="51b5c-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="51b5c-119">Seleccione **sí** para establecer el permiso y obtener acceso a la entrada de mira.</span><span class="sxs-lookup"><span data-stu-id="51b5c-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="51b5c-120">Si necesita cambiar esta configuración en cualquier momento, se puede encontrar en la aplicación de **configuración** .</span><span class="sxs-lookup"><span data-stu-id="51b5c-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Permisos de entrada ocular](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="51b5c-122">El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos en lugar de los dos rayos necesarios para el seguimiento de Stereoscopic, que no se admite.</span><span class="sxs-lookup"><span data-stu-id="51b5c-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="51b5c-123">Esta es toda la configuración que necesitará para empezar a agregar entradas de fijamente a las aplicaciones de HoloLens 2 en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="51b5c-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="51b5c-124">Puede encontrar más información sobre la entrada y cómo afecta a los usuarios de realidad mixta en los vínculos siguientes.</span><span class="sxs-lookup"><span data-stu-id="51b5c-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="51b5c-125">Asegúrese de pensar en ellos al compilar experiencias interactivas.</span><span class="sxs-lookup"><span data-stu-id="51b5c-125">Be sure to think about these when building your interactive experiences.</span></span> 

## <a name="see-also"></a><span data-ttu-id="51b5c-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="51b5c-126">See also</span></span>
* [<span data-ttu-id="51b5c-127">Calibración</span><span class="sxs-lookup"><span data-stu-id="51b5c-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="51b5c-128">Comodidad</span><span class="sxs-lookup"><span data-stu-id="51b5c-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="51b5c-129">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="51b5c-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="51b5c-130">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="51b5c-130">Voice input</span></span>](voice-design.md)
