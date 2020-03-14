---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada
ms.openlocfilehash: f2ae18d4063c7c4a63346a1202cacaa7fbbdf959
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375992"
---
# <a name="voice-input"></a><span data-ttu-id="7c7b4-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-105">Voice input</span></span>

![Entrada de voz](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="7c7b4-107">La voz es una de las formas clave de entrada en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="7c7b4-108">Permite comandos directamente de un holograma sin tener que usar [gestos de mano](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="7c7b4-109">La entrada de voz es una manera natural de comunicar tus intenciones.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="7c7b4-110">La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="7c7b4-111">La entrada de voz se basa en el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admite la voz en todas las demás _aplicaciones universales de Windows_.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="7c7b4-112">En HoloLens, el reconocimiento de voz siempre funcionará en el idioma de visualización de Windows configurado en configuración.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="7c7b4-113">Voz y miras</span><span class="sxs-lookup"><span data-stu-id="7c7b4-113">Voice and gaze</span></span>

<span data-ttu-id="7c7b4-114">Cuando se usan comandos de voz, se usa normalmente (encabezado o ojo) para hacer clic en el mecanismo de destino, ya sea con un cursor ("Select") o para canalizar implícitamente el comando a una aplicación que se está viendo.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="7c7b4-115">En este caso, es posible que no sea necesario que muestre ningún cursor de miras _("verlo, decirlo")_ .</span><span class="sxs-lookup"><span data-stu-id="7c7b4-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="7c7b4-116">Por supuesto, algunos comandos de voz no requieren un destino, como "ir a Inicio" o "Hola Cortana".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="7c7b4-117">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="7c7b4-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7c7b4-118"><strong>Ofrecen</strong></span><span class="sxs-lookup"><span data-stu-id="7c7b4-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7c7b4-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7c7b4-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7c7b4-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7c7b4-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7c7b4-121"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7c7b4-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7c7b4-122">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-122">Voice input</span></span></td>
        <td><span data-ttu-id="7c7b4-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7c7b4-123">✔️</span></span></td>
        <td><span data-ttu-id="7c7b4-124">✔️</span><span class="sxs-lookup"><span data-stu-id="7c7b4-124">✔️</span></span></td>
        <td><span data-ttu-id="7c7b4-125">✔️ (con micrófono)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="7c7b4-126">Comando "seleccionar"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-126">The "select" command</span></span>

<span data-ttu-id="7c7b4-127">**HoloLens (1ª generación)**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="7c7b4-128">Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo el comando de voz del sistema "Select".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="7c7b4-129">Esto se comporta igual que una [pulsación aérea](gaze-and-commit.md#composite-gestures) en HoloLens, presionando el botón seleccionar en el [clic de hololens](hardware-accessories.md#hololens-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="7c7b4-130">Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="7c7b4-131">"Select" está habilitado por un algoritmo de detección de palabras clave de baja energía, por lo que siempre está disponible para que lo indique en cualquier momento con un impacto mínimo en la duración de la batería, incluso con sus manos en el lateral.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="7c7b4-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="7c7b4-133">Para usar el comando "seleccionar" de voz en HoloLens 2, primero debe abrir el cursor de miración para usarlo como puntero.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="7c7b4-134">El comando para ponerlo al día es fácil de recordar (simplemente, por ejemplo, "Select").</span><span class="sxs-lookup"><span data-stu-id="7c7b4-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="7c7b4-135">Para salir del modo, simplemente vuelva a usar las manos, ya sea mediante el toque de aire, cerca de un botón con los dedos o usando el gesto del sistema.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="7c7b4-136">*Imagen: "seleccionar" para usar el comando de voz para la selección*</span><span class="sxs-lookup"><span data-stu-id="7c7b4-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Un usuario puede decir "seleccionar" para usar el comando de voz para una selección.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="7c7b4-138">Hola Cortana</span><span class="sxs-lookup"><span data-stu-id="7c7b4-138">Hey Cortana</span></span>

<span data-ttu-id="7c7b4-139">También puede decir "Hola Cortana" para abrir Cortana en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="7c7b4-140">No tiene que esperar a que parezca que siga preguntando a su pregunta o le dé una instrucción; por ejemplo, intente decir "Hola Cortana, ¿cuál es el tiempo?".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="7c7b4-141">como una sola oración.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-141">as a single sentence.</span></span> <span data-ttu-id="7c7b4-142">Para obtener más información sobre Cortana y lo que puede hacer, simplemente pregúntele.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="7c7b4-143">Por ejemplo, "Hola Cortana, ¿qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="7c7b4-144">y desplegarán una lista de comandos de trabajo y sugeridos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="7c7b4-145">Si ya está **en la aplicación** de Cortana, también puede hacer clic en el</span><span class="sxs-lookup"><span data-stu-id="7c7b4-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="7c7b4-146">en la barra lateral para desplegar el mismo menú.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="7c7b4-147">**Comandos específicos de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="7c7b4-148">"¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-148">"What can I say?"</span></span>
* <span data-ttu-id="7c7b4-149">"Ir a Inicio"-en lugar de a la [floración](system-gesture.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="7c7b4-150">"Iniciar <app>"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-150">"Launch <app>"</span></span>
* <span data-ttu-id="7c7b4-151">"Mueva <app> aquí"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-151">"Move <app> here"</span></span>
* <span data-ttu-id="7c7b4-152">"Tomar una imagen"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-152">"Take a picture"</span></span>
* <span data-ttu-id="7c7b4-153">"Iniciar grabación"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-153">"Start recording"</span></span>
* <span data-ttu-id="7c7b4-154">"Detener grabación"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-154">"Stop recording"</span></span>
* <span data-ttu-id="7c7b4-155">"Aumentar el brillo"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-155">"Increase the brightness"</span></span>
* <span data-ttu-id="7c7b4-156">"Reducir el brillo"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="7c7b4-157">"Aumentar el volumen"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-157">"Increase the volume"</span></span>
* <span data-ttu-id="7c7b4-158">"Reducir el volumen"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-158">"Decrease the volume"</span></span>
* <span data-ttu-id="7c7b4-159">"Silenciar" o "dessilenciar"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="7c7b4-160">"Apagar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-160">"Shut down the device"</span></span>
* <span data-ttu-id="7c7b4-161">"Reiniciar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-161">"Restart the device"</span></span>
* <span data-ttu-id="7c7b4-162">"Ir a suspensión"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-162">"Go to sleep"</span></span>
* <span data-ttu-id="7c7b4-163">"¿Qué hora es?"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-163">"What time is it?"</span></span>
* <span data-ttu-id="7c7b4-164">"¿Cuánta batería he dejado?"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="7c7b4-165">"Verlo, decirlo"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="7c7b4-166">HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="7c7b4-167">Por ejemplo, al examinar una ventana de la aplicación en HoloLens (1ª generación), un usuario puede decir el comando "ajustar" que se ve en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="7c7b4-168">*Imagen: un usuario puede decir el comando "ajustar" que ve en la barra de la aplicación para ajustar la posición de la aplicación*</span><span class="sxs-lookup"><span data-stu-id="7c7b4-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="7c7b4-169">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="7c7b4-170">![al mirar una ventana de la aplicación o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="7c7b4-171">Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="7c7b4-172">Para reforzar esto, mientras Gazing en un botón de HoloLens (1ª generación), verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de ella.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="7c7b4-173">Para mostrar la información sobre herramientas de voz en HoloLens 2, muestre el cursor de voz indicando "seleccionar" o "Qué puedo decir" (vea la imagen).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="7c7b4-174">*Imagen: "ver, por ejemplo," los comandos aparecen debajo de los botones*</span><span class="sxs-lookup"><span data-stu-id="7c7b4-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="7c7b4-176">Comandos de voz para la manipulación rápida de hologramas</span><span class="sxs-lookup"><span data-stu-id="7c7b4-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="7c7b4-177">Hay una serie de comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="7c7b4-178">Estos comandos de voz funcionan en las ventanas de la aplicación, así como en los objetos 3D que ha colocado en el mundo.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="7c7b4-179">**Comandos de manipulación de hologramas**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="7c7b4-180">Me encuentro</span><span class="sxs-lookup"><span data-stu-id="7c7b4-180">Face me</span></span>
* <span data-ttu-id="7c7b4-181">Mayor | Enhance</span><span class="sxs-lookup"><span data-stu-id="7c7b4-181">Bigger | Enhance</span></span>
* <span data-ttu-id="7c7b4-182">Disminuye</span><span class="sxs-lookup"><span data-stu-id="7c7b4-182">Smaller</span></span>

<span data-ttu-id="7c7b4-183">En HoloLens 2, también puede crear interacciones más naturales en combinación con la mirada, lo que proporciona implícitamente información contextual sobre lo que se está haciendo referencia.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="7c7b4-184">Por ejemplo, podría simplemente mirar un holograma y decir "colocarlo" y, a continuación, buscar _el_lugar en el que desea colocarlo y decir " _aquí_".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="7c7b4-185">O bien, podría ver una pieza holográfica en una máquina compleja y decir: "proporcione más información acerca de _esto_".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="7c7b4-186">Detección de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-186">Discovering voice commands</span></span>

<span data-ttu-id="7c7b4-187">Algunos comandos, como los comandos para la manipulación rápida anterior, se pueden ocultar.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="7c7b4-188">Para obtener información sobre los comandos que puede usar, mira fijamente a un objeto y, por ejemplo, "¿Qué puedo decir?".</span><span class="sxs-lookup"><span data-stu-id="7c7b4-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="7c7b4-189">Aparece una lista de posibles comandos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-189">A list of possible commands pops up.</span></span> <span data-ttu-id="7c7b4-190">También puede usar el cursor de mirar hacia abajo para buscar y mostrar la información sobre herramientas de voz de cada botón delante.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="7c7b4-191">Si desea una lista completa, simplemente indique "Mostrar todos los comandos" en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="7c7b4-192">Dictado</span><span class="sxs-lookup"><span data-stu-id="7c7b4-192">Dictation</span></span>

<span data-ttu-id="7c7b4-193">En lugar de escribir con [grifos de aire](gaze-and-commit.md#composite-gestures), el dictado de voz puede ser más eficaz para escribir texto en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="7c7b4-194">Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="7c7b4-195">![dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="7c7b4-196">*El dictado de voz comienza seleccionando el botón micrófono del teclado.*</span><span class="sxs-lookup"><span data-stu-id="7c7b4-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="7c7b4-197">Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="7c7b4-198">Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="7c7b4-199">Agregar comandos de voz a la aplicación</span><span class="sxs-lookup"><span data-stu-id="7c7b4-199">Adding voice commands to your app</span></span>

<span data-ttu-id="7c7b4-200">Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="7c7b4-201">La voz es una manera eficaz y cómoda de controlar el sistema y las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="7c7b4-202">Dado que los usuarios hablan con variantes regionales y acentos diversos, la opción adecuada de palabras clave de voz asegurará que los comandos de los usuarios se interpretan de forma inequívoca.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="7c7b4-203">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="7c7b4-203">Best practices</span></span>

<span data-ttu-id="7c7b4-204">A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="7c7b4-205">**Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="7c7b4-206">Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="7c7b4-207">Ejemplo: "reproducir vídeo" es mejor que "reproducir el vídeo seleccionado actualmente"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="7c7b4-208">**Usar vocabulario simple** : por ejemplo, "show Note" es mejor que "show letrero"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="7c7b4-209">**Asegúrate de que los comandos no sean destructivos**: haz que cualquier acción que se puede realizar mediante un comando de voz no sea destructiva, y se pueda deshacer fácilmente, en caso de que otra persona que esté hablando cerca del usuario pueda desencadenar accidentalmente un comando.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="7c7b4-210">**Evita los comandos que tengan un sonido similar**: evita registrar varios comandos de voz que suenen de forma parecida.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="7c7b4-211">Ejemplo: "Mostrar más" y "Mostrar tienda" puede ser un sonido muy similar.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="7c7b4-212">**Anula el registro de la aplicación cuando no esté en uso**: cuando la aplicación no está en un estado en el que un comando de voz determinado es válido, considera la posibilidad de anular el registro de modo que otros comandos no se confundan con ese.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="7c7b4-213">**Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="7c7b4-214">**Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="7c7b4-215">**Evita el uso de comandos del sistema**: los siguientes comandos de voz están reservados para el sistema.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="7c7b4-216">Las aplicaciones no deben utilizar estos comandos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="7c7b4-217">"Hola Cortana"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="7c7b4-218">"Seleccionar"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-218">"Select"</span></span>
   * <span data-ttu-id="7c7b4-219">"Ir a Inicio"</span><span class="sxs-lookup"><span data-stu-id="7c7b4-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="7c7b4-220">Ventajas de la entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-220">Advantages of voice input</span></span>

<span data-ttu-id="7c7b4-221">Las entradas de voz son una manera natural de comunicar nuestras intenciones.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="7c7b4-222">La voz es especialmente útil en los recorridos de la interfaz, ya que puede ayudar a los usuarios a **resaltar** varios pasos de una interfaz (un usuario podría decir "volver atrás" mientras mira una página web, en lugar de tener que subir y presionar el botón atrás en la aplicación).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="7c7b4-223">Esta pequeña hora de guardar tiene un **efecto emocional** eficaz sobre la percepción del usuario de la experiencia y les da una pequeña cantidad de mejorar enormemente.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="7c7b4-224">El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="7c7b4-225">En los dispositivos en los que es difícil escribir en un teclado, el **dictado de voz** puede ser una forma alternativa eficaz de escribir texto.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="7c7b4-226">Por último, en algunos casos en los que el **intervalo de precisión** de la mirada y el gesto es limitado, la voz puede ayudar a eliminar la ambigüedad de la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="7c7b4-227">**Cómo puede beneficiar al usuario la utilización de la voz**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="7c7b4-228">Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="7c7b4-229">Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="7c7b4-230">Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="7c7b4-231">Es aceptable socialmente: se adapta a las normas sociales en términos de comportamiento.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="7c7b4-232">Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="7c7b4-233">Desafíos de la entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-233">Challenges for voice input</span></span>

<span data-ttu-id="7c7b4-234">Aunque la entrada de voz es excelente para muchas aplicaciones diferentes, también enfrenta varios desafíos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="7c7b4-235">La comprensión de las ventajas y los desafíos de la entrada de voz permite a los desarrolladores de aplicaciones tomar decisiones más inteligentes sobre cómo y Cuándo usar la entrada de voz y crear una excelente experiencia para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="7c7b4-236">**Entrada de voz para el control de entrada continuo** El control específico es uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="7c7b4-237">Por ejemplo, un usuario podría querer cambiar su volumen en su aplicación de música.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="7c7b4-238">Puede simplemente decir "más alto", pero no está claro cuánto se supone que el sistema hace el volumen.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="7c7b4-239">El usuario podría decir: "hacer que sea un poco más alto", pero "un poco" es difícil de cuantificar.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="7c7b4-240">El movimiento o el escalado de los hologramas con la voz es igualmente difícil.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="7c7b4-241">**Confiabilidad de la detección de entrada de voz** Aunque los sistemas de entrada de voz son mejores y mejores, a veces pueden oír e interpretar de forma incorrecta un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="7c7b4-242">La clave es abordar este desafío en la aplicación proporcionando comentarios al usuario cuando el sistema está escuchando y lo que el sistema entendió para crear claridad sobre los posibles problemas al comprender correctamente el usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="7c7b4-243">**Entrada de voz en espacios compartidos** Es posible que la voz no sea socialmente aceptable en espacios que comparta con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="7c7b4-244">Estos son algunos ejemplos:</span><span class="sxs-lookup"><span data-stu-id="7c7b4-244">Here are a few examples:</span></span>
* <span data-ttu-id="7c7b4-245">Es posible que el usuario no quiera molestar a otros (por ejemplo, en una biblioteca tranquila o en una oficina compartida).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="7c7b4-246">Es posible que los usuarios no se vean tan complicados como hablar en el público.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="7c7b4-247">Un usuario puede sentirse incómodo dictar un mensaje personal o confidencial (incluidas las contraseñas) mientras que otros están escuchando</span><span class="sxs-lookup"><span data-stu-id="7c7b4-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="7c7b4-248">**Entrada de voz de palabras únicas o desconocidas** Las dificultades para la entrada de voz también se muestran cuando los usuarios están dictando palabras que pueden ser desconocidas para el sistema, como sobrenombres, determinadas palabras o abreviaturas de jergas.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="7c7b4-249">**Comandos de voz de aprendizaje** Aunque el objetivo final es conversar naturalmente con el sistema, a menudo las aplicaciones siguen confiando en comandos de voz específicos predefinidos.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="7c7b4-250">Un desafío asociado a un gran conjunto de comandos de voz es cómo enseñarlas sin sobrecargar al usuario y cómo ayudar al usuario a conservarlas.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="7c7b4-251">Estados de la respuesta a la voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-251">Voice feedback states</span></span>

<span data-ttu-id="7c7b4-252">Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="7c7b4-253">Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="7c7b4-254">A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="7c7b4-255">![1. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="7c7b4-256">**1. estado normal del cursor**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7c7b4-257">![2. Comunica los comentarios de voz y, a continuación, desaparece](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="7c7b4-258">**2. comunica comentarios de voz y luego desaparece**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7c7b4-259">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-259">![\*3.</span></span> <span data-ttu-id="7c7b4-260">Estado normal del cursor](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="7c7b4-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="7c7b4-261">**3. vuelve al estado normal del cursor**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="7c7b4-262">Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="7c7b4-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="7c7b4-263">Di **"Seleccionar"** mientras seleccionas como destino un botón (puedes usar esto en cualquier lugar para hacer clic en un botón).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="7c7b4-264">Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="7c7b4-265">Por ejemplo, al examinar una aplicación, un usuario puede decir el comando "Quitar" para quitar la aplicación (esto te ahorra el tiempo de hacer clic con la mano).</span><span class="sxs-lookup"><span data-stu-id="7c7b4-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="7c7b4-266">Puedes iniciar la escucha de Cortana diciendo **"Hola Cortana".**</span><span class="sxs-lookup"><span data-stu-id="7c7b4-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="7c7b4-267">Puedes preguntarle cosas ("Hola Cortana, cuál es la altura de la torre Eiffel"), decirle que abra una aplicación ("Hola Cortana, abre Netflix") o que abra el menú Inicio ("Hola Cortana, llévame al principio") y mucho más.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="7c7b4-268">Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="7c7b4-269">¿Qué puedo decir?</span><span class="sxs-lookup"><span data-stu-id="7c7b4-269">What can I say?</span></span>
* <span data-ttu-id="7c7b4-270">¿Cómo sé si el sistema me escuchó correctamente?</span><span class="sxs-lookup"><span data-stu-id="7c7b4-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="7c7b4-271">El sistema se equivoca todo el tiempo con mis comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="7c7b4-272">No reacciona cuando digo un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="7c7b4-273">Reacciona de forma equivocada cuando digo un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="7c7b4-274">¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?</span><span class="sxs-lookup"><span data-stu-id="7c7b4-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="7c7b4-275">¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?</span><span class="sxs-lookup"><span data-stu-id="7c7b4-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="7c7b4-276">Comunicación</span><span class="sxs-lookup"><span data-stu-id="7c7b4-276">Communication</span></span>

<span data-ttu-id="7c7b4-277">En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que puede consumir la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="7c7b4-278">Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otras que se pueden usar para el audio del entorno ambiente. escenarios de captura (es decir, "videocámara").</span><span class="sxs-lookup"><span data-stu-id="7c7b4-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="7c7b4-279">La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono 16kHz 24bit de la voz del usuario</span><span class="sxs-lookup"><span data-stu-id="7c7b4-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="7c7b4-280">La categoría AudioCategory_Speech Stream está personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia de 16kHz 24bit mono de la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="7c7b4-281">Los motores de voz de terceros pueden usar esta categoría si es necesario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="7c7b4-282">La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits de 48 bits.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="7c7b4-283">Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="7c7b4-284">Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="7c7b4-285">Lenguajes</span><span class="sxs-lookup"><span data-stu-id="7c7b4-285">Languages</span></span>

<span data-ttu-id="7c7b4-286">HoloLens 2 también admite idiomas adicionales.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="7c7b4-287">Tenga en cuenta que los comandos de voz siempre se ejecutarán en el idioma para mostrar del sistema aunque se instalen varios teclados o cuando las aplicaciones intenten crear un reconocedor de voz en otro idioma.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="7c7b4-288">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="7c7b4-288">Troubleshooting</span></span>

<span data-ttu-id="7c7b4-289">Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="7c7b4-290">En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="7c7b4-291">En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="7c7b4-292">Antes de ese primer evento de cierre de sesión/en el momento de pasar a través de WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7c7b4-293">Entrada de voz en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="7c7b4-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="7c7b4-294">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede asignar fácilmente comandos de voz en cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="7c7b4-295">Use el **Perfil de entrada de voz** de MRTK para definir sus palabras clave.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="7c7b4-296">Mediante la asignación del script **SpeechInputHandler** , puede hacer que cualquier objeto responda a las palabras clave definidas en el perfil de entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="7c7b4-297">SpeechInputHandler también proporciona una etiqueta de confirmación de voz para mejorar la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="7c7b4-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="7c7b4-298">Comando MRTK-Voice</span><span class="sxs-lookup"><span data-stu-id="7c7b4-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="7c7b4-299">Vea también</span><span class="sxs-lookup"><span data-stu-id="7c7b4-299">See also</span></span>
* [<span data-ttu-id="7c7b4-300">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="7c7b4-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7c7b4-301">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="7c7b4-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7c7b4-302">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="7c7b4-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="7c7b4-303">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="7c7b4-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="7c7b4-304">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="7c7b4-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
