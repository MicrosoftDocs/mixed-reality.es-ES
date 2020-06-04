---
title: Entrada de voz
description: Tutorial sobre la configuración y el uso de la entrada de voz en HoloLens 2 e inreal Engine
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, inreal, inreal Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconocimiento de voz, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330637"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="588ad-104">Entrada de voz en inreal</span><span class="sxs-lookup"><span data-stu-id="588ad-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="588ad-105">Información general</span><span class="sxs-lookup"><span data-stu-id="588ad-105">Overview</span></span>
<span data-ttu-id="588ad-106">La entrada de voz le permite interactuar con un holograma sin tener que usar gestos de mano y es compatible con HoloLens (1ª generación) y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="588ad-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="588ad-107">Está basado en el mismo motor que admite la voz en todas las demás aplicaciones universales de Windows y puede Agregar una sensación natural a la manera de interactuar en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="588ad-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="588ad-108">Las características de voz admitidas incluyen:</span><span class="sxs-lookup"><span data-stu-id="588ad-108">Supported voice features include:</span></span>
- <span data-ttu-id="588ad-109">[Comando SELECT](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="588ad-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="588ad-110">Hola, Cortana</span><span class="sxs-lookup"><span data-stu-id="588ad-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="588ad-111">"Verlo, decirlo" para la interacción de botón y etiqueta</span><span class="sxs-lookup"><span data-stu-id="588ad-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="588ad-112">Dictado</span><span class="sxs-lookup"><span data-stu-id="588ad-112">Dictation</span></span>

<span data-ttu-id="588ad-113">Para obtener más información, consulte la documentación principal de [entrada de voz](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="588ad-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="588ad-114">Habilitación del reconocimiento de voz</span><span class="sxs-lookup"><span data-stu-id="588ad-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="588ad-115">Para habilitar el reconocimiento de voz en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="588ad-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="588ad-116">Seleccione **configuración del proyecto > plataforma > HoloLens > funcionalidades** y habilite el **micrófono**.</span><span class="sxs-lookup"><span data-stu-id="588ad-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="588ad-117">Habilitado recogniztion de voz en **configuración > privacidad > voz** y seleccione **Inglés**.</span><span class="sxs-lookup"><span data-stu-id="588ad-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="588ad-118">El reconocimiento de voz siempre funciona en el idioma de visualización de Windows configurado en la aplicación de **configuración** .</span><span class="sxs-lookup"><span data-stu-id="588ad-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="588ad-119">Se recomienda habilitar también el reconocimiento de **voz en línea** para obtener la mejor calidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="588ad-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="588ad-121">Se mostrará un cuadro de diálogo cuando se inicie la aplicación por primera vez para preguntar si desea habilitar el micrófono.</span><span class="sxs-lookup"><span data-stu-id="588ad-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="588ad-122">Si selecciona **sí** , se iniciará la entrada de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="588ad-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="588ad-123">La entrada de voz no requiere ninguna API especial de Windows Mixed Reality; se basa en la API de asignación de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) de Engine 4 inreal Engine existente.</span><span class="sxs-lookup"><span data-stu-id="588ad-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="588ad-124">Agregar asignaciones de voz</span><span class="sxs-lookup"><span data-stu-id="588ad-124">Adding Speech Mappings</span></span>
<span data-ttu-id="588ad-125">La conexión de voz a la acción es un paso importante cuando se usa la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="588ad-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="588ad-126">Estas asignaciones supervisan las palabras clave de la aplicación para la voz que un usuario podría decir y, a continuación, activa una acción vinculada.</span><span class="sxs-lookup"><span data-stu-id="588ad-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="588ad-127">Puede buscar las asignaciones de voz:</span><span class="sxs-lookup"><span data-stu-id="588ad-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="588ad-128">Seleccione **editar > configuración del proyecto**, desplácese hasta la sección **motor** y haga clic en **entrada**.</span><span class="sxs-lookup"><span data-stu-id="588ad-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="588ad-129">Para agregar una nueva asignación de voz para un comando de salto:</span><span class="sxs-lookup"><span data-stu-id="588ad-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="588ad-130">Haga clic en el **+** icono situado junto a **elementos** de la matriz y rellene los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="588ad-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="588ad-131">**jumpWord** para **el nombre de acción**</span><span class="sxs-lookup"><span data-stu-id="588ad-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="588ad-132">**saltar** la **palabra clave de voz**</span><span class="sxs-lookup"><span data-stu-id="588ad-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="588ad-133">Cualquier palabra o frase en inglés (s) se puede usar como palabra clave.</span><span class="sxs-lookup"><span data-stu-id="588ad-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Información de entrada del motor de UE4](images/unreal/engine-input.png)

<span data-ttu-id="588ad-135">Las asignaciones de voz se pueden usar como componentes de entrada como asignaciones de acción o de eje o como nodos de plano en el gráfico de eventos.</span><span class="sxs-lookup"><span data-stu-id="588ad-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="588ad-136">Por ejemplo, puede vincular el comando de salto para imprimir dos registros diferentes en función de Cuándo se pronuncia la palabra:</span><span class="sxs-lookup"><span data-stu-id="588ad-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="588ad-137">Haga doble clic en un plano para abrirlo en el **gráfico de eventos**.</span><span class="sxs-lookup"><span data-stu-id="588ad-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="588ad-138">**Haga clic con el botón derecho** y busque el nombre de la **acción** de la asignación de voz (en este caso, **jumpWord**) y presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="588ad-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="588ad-139">Esto agrega un nodo de **acción de entrada** al gráfico.</span><span class="sxs-lookup"><span data-stu-id="588ad-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="588ad-140">Arrastre y coloque el anclaje **presionado** en el nodo de la **cadena de impresión** , tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="588ad-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="588ad-141">Puede dejar el PIN **liberado** vacío, no ejecutará nada para las asignaciones de voz.</span><span class="sxs-lookup"><span data-stu-id="588ad-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Acción simple para voz](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="588ad-143">Juegue a la aplicación, por ejemplo, la palabra **Jump** y vea que la consola imprime los registros.</span><span class="sxs-lookup"><span data-stu-id="588ad-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="588ad-144">Esta es toda la configuración que necesitará para empezar a agregar entradas de voz a las aplicaciones de HoloLens en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="588ad-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="588ad-145">Puede encontrar más información sobre la voz e interactividad en los vínculos siguientes y asegúrese de pensar en la experiencia que está creando para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="588ad-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="588ad-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="588ad-146">See also</span></span>
* [<span data-ttu-id="588ad-147">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="588ad-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="588ad-148">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="588ad-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="588ad-149">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="588ad-149">MR Input 212: Voice</span></span>](holograms-212.md)
