---
title: Entrada de voz
description: Explica cómo usar la entrada de voz
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835331"
---
# <a name="voice-input"></a><span data-ttu-id="b38c8-104">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="b38c8-104">Voice Input</span></span>

<span data-ttu-id="b38c8-105">Para habilitar el reconocimiento de voz en HoloLens, el desarrollador debe habilitar "micrófono" en el editor desareal en configuración del proyecto > Platform > HoloLens > funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b38c8-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="b38c8-106">El dispositivo también debe tener habilitado el reconocimiento de voz en configuración > privacidad > voz y usar el idioma inglés.</span><span class="sxs-lookup"><span data-stu-id="b38c8-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="b38c8-108">Se recomienda habilitar también el reconocimiento de voz en línea para obtener la mejor calidad posible del servicio.</span><span class="sxs-lookup"><span data-stu-id="b38c8-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="b38c8-109">[Aquí](voice-input.md) encontrará detalles técnicos para el reconocimiento de voz en HoloLens</span><span class="sxs-lookup"><span data-stu-id="b38c8-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="b38c8-110">Después, el usuario verá un cuadro de diálogo que le permitirá habilitar el micrófono cuando se inicie la aplicación por primera vez.</span><span class="sxs-lookup"><span data-stu-id="b38c8-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="b38c8-111">Si un usuario selecciona Sí, la aplicación comenzará a obtener entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="b38c8-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="b38c8-112">La entrada de voz no requiere una API especial de Windows Mixed Reality y, en su lugar, se basa en la API de asignación de entrada de Engine 4 existente.</span><span class="sxs-lookup"><span data-stu-id="b38c8-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="b38c8-113">[Aquí](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) encontrará información detallada sobre cómo usar la API de entrada</span><span class="sxs-lookup"><span data-stu-id="b38c8-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="b38c8-114">Se han agregado las asignaciones de voz a la sección de enlaces de la entrada del motor, que se encuentra debajo de las asignaciones de acciones y ejes.</span><span class="sxs-lookup"><span data-stu-id="b38c8-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![Información de entrada del motor de UE4](images/unreal/engine-input.png)
 
<span data-ttu-id="b38c8-116">Este es un ejemplo de supervisión agregada para el mundo "salto".</span><span class="sxs-lookup"><span data-stu-id="b38c8-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="b38c8-117">Se puede usar cualquier palabra o frase en inglés.</span><span class="sxs-lookup"><span data-stu-id="b38c8-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="b38c8-118">Después de agregar una asignación de voz a través de la configuración del proyecto, un desarrollador puede usar la lógica no real estándar para controlar la entrada, como en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b38c8-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![Acción simple para voz](images/unreal/input-action-bp.png)
