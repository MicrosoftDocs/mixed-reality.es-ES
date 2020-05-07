---
title: Mira fijamente inrealmente
description: Explica cómo usar la entrada de fijamente en el modo inreal.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens, seguimiento ocular
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835633"
---
# <a name="gaze-input"></a><span data-ttu-id="f01b0-104">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="f01b0-104">Gaze Input</span></span>

<span data-ttu-id="f01b0-105">El complemento de Windows Mixed Reality no proporciona ninguna función especial para la entrada de mirada.</span><span class="sxs-lookup"><span data-stu-id="f01b0-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="f01b0-106">Todo funciona a través de la API no real estándar.</span><span class="sxs-lookup"><span data-stu-id="f01b0-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="f01b0-107">Cabezal mira API</span><span class="sxs-lookup"><span data-stu-id="f01b0-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="f01b0-108">Seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="f01b0-108">Eye tracking</span></span>

<span data-ttu-id="f01b0-109">Para usar la API de seguimiento ocular, los desarrolladores deben habilitar la funcionalidad de "entrada de Miración" en la configuración del proyecto de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f01b0-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="f01b0-110">Cuando se inicia la aplicación, el usuario verá la siguiente solicitud de consentimiento.</span><span class="sxs-lookup"><span data-stu-id="f01b0-110">When the application starts, user will see the following consent prompt</span></span>

![Permisos de entrada ocular](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="f01b0-112">Si el usuario da su permiso, la aplicación recibirá una entrada de mirada.</span><span class="sxs-lookup"><span data-stu-id="f01b0-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="f01b0-113">La API de seguimiento de ojos no real está documentada [aquí](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span><span class="sxs-lookup"><span data-stu-id="f01b0-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="f01b0-114">[Aquí](eye-tracking.md) se muestran los detalles técnicos del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="f01b0-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="f01b0-115">Tenga en cuenta que, en concreto, el seguimiento de la vista de HoloLens no es real con un solo rayo para ambos ojos.</span><span class="sxs-lookup"><span data-stu-id="f01b0-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="f01b0-116">HoloLens no proporciona seguimiento Stereoscopic ocular.</span><span class="sxs-lookup"><span data-stu-id="f01b0-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
