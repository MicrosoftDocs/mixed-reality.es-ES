---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829949"
---
# <a name="voice-input"></a><span data-ttu-id="10591-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="10591-105">Voice input</span></span>

<span data-ttu-id="10591-106">Voice es una de las tres formas clave de entrada en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10591-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="10591-107">Permite comandos directamente de un holograma sin tener que usar [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="10591-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="10591-108">Simplemente [mira](gaze.md) un holograma y habla el comando.</span><span class="sxs-lookup"><span data-stu-id="10591-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="10591-109">La entrada de voz puede ser una forma natural de comunicar su intención.</span><span class="sxs-lookup"><span data-stu-id="10591-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="10591-110">La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.</span><span class="sxs-lookup"><span data-stu-id="10591-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="10591-111">La entrada de voz se basa en el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admite la voz en todas las demás aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="10591-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="10591-112">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="10591-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="10591-113"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="10591-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="10591-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="10591-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="10591-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="10591-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="10591-116"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="10591-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="10591-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="10591-117">Voice input</span></span></td>
        <td><span data-ttu-id="10591-118">✔️</span><span class="sxs-lookup"><span data-stu-id="10591-118">✔️</span></span></td>
        <td><span data-ttu-id="10591-119">✔️</span><span class="sxs-lookup"><span data-stu-id="10591-119">✔️</span></span></td>
        <td><span data-ttu-id="10591-120">✔️ (con micrófono)</span><span class="sxs-lookup"><span data-stu-id="10591-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="10591-121">Comando "seleccionar"</span><span class="sxs-lookup"><span data-stu-id="10591-121">The "select" command</span></span>

<span data-ttu-id="10591-122">Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo "Select".</span><span class="sxs-lookup"><span data-stu-id="10591-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="10591-123">Esto se comporta igual que una pulsación [aérea](gestures.md#air-tap) en HoloLens, presionando el botón seleccionar en el [clic de hololens](hardware-accessories.md#hololens-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="10591-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="10591-124">Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación.</span><span class="sxs-lookup"><span data-stu-id="10591-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="10591-125">"Select" está habilitado por un algoritmo de detección de palabras clave de baja energía, por lo que siempre está disponible para que lo indique en cualquier momento con un impacto mínimo en la duración de la batería, incluso con sus manos en el lateral.</span><span class="sxs-lookup"><span data-stu-id="10591-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="10591-126">[Próximamente](index.md#news-and-notes) se ofrecerá orientación específica para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="10591-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="10591-127">![Decir "seleccionar" para usar el comando de voz para la selección](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="10591-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="10591-128">*Decir "seleccionar" para usar el comando de voz para la selección*</span><span class="sxs-lookup"><span data-stu-id="10591-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="10591-129">Hola Cortana</span><span class="sxs-lookup"><span data-stu-id="10591-129">Hey Cortana</span></span>

<span data-ttu-id="10591-130">También puede decir "Hola Cortana" para abrir Cortana en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="10591-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="10591-131">No tiene que esperar a que parezca que siga preguntando su pregunta o le dé una instrucción; por ejemplo, intente decir "Hola a Cortana ¿cuál es el tiempo?".</span><span class="sxs-lookup"><span data-stu-id="10591-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="10591-132">como una sola oración.</span><span class="sxs-lookup"><span data-stu-id="10591-132">as a single sentence.</span></span> <span data-ttu-id="10591-133">Para obtener más información sobre Cortana y lo que puede hacer, simplemente pregúntele.</span><span class="sxs-lookup"><span data-stu-id="10591-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="10591-134">"Hola a Cortana ¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="10591-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="10591-135">y desplegarán una lista de comandos de trabajo y sugeridos.</span><span class="sxs-lookup"><span data-stu-id="10591-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="10591-136">Si ya está en la aplicación de Cortana, también puede hacer clic **en el**</span><span class="sxs-lookup"><span data-stu-id="10591-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="10591-137">en la barra lateral para desplegar el mismo menú.</span><span class="sxs-lookup"><span data-stu-id="10591-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="10591-138">**Comandos específicos de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="10591-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="10591-139">"¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="10591-139">"What can I say?"</span></span>
* <span data-ttu-id="10591-140">"Ir a Inicio" o "ir a Inicio"-en lugar de la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="10591-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="10591-141">"Launch <app>"</span><span class="sxs-lookup"><span data-stu-id="10591-141">"Launch <app>"</span></span>
* <span data-ttu-id="10591-142">"Moverse <app> aquí"</span><span class="sxs-lookup"><span data-stu-id="10591-142">"Move <app> here"</span></span>
* <span data-ttu-id="10591-143">"Tomar una imagen"</span><span class="sxs-lookup"><span data-stu-id="10591-143">"Take a picture"</span></span>
* <span data-ttu-id="10591-144">"Iniciar grabación"</span><span class="sxs-lookup"><span data-stu-id="10591-144">"Start recording"</span></span>
* <span data-ttu-id="10591-145">"Detener grabación"</span><span class="sxs-lookup"><span data-stu-id="10591-145">"Stop recording"</span></span>
* <span data-ttu-id="10591-146">"Aumentar el brillo"</span><span class="sxs-lookup"><span data-stu-id="10591-146">"Increase the brightness"</span></span>
* <span data-ttu-id="10591-147">"Reducir el brillo"</span><span class="sxs-lookup"><span data-stu-id="10591-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="10591-148">"Aumentar el volumen"</span><span class="sxs-lookup"><span data-stu-id="10591-148">"Increase the volume"</span></span>
* <span data-ttu-id="10591-149">"Reducir el volumen"</span><span class="sxs-lookup"><span data-stu-id="10591-149">"Decrease the volume"</span></span>
* <span data-ttu-id="10591-150">"Silenciar" o "dessilenciar"</span><span class="sxs-lookup"><span data-stu-id="10591-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="10591-151">"Apagar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="10591-151">"Shut down the device"</span></span>
* <span data-ttu-id="10591-152">"Reiniciar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="10591-152">"Restart the device"</span></span>
* <span data-ttu-id="10591-153">"Ir a suspensión"</span><span class="sxs-lookup"><span data-stu-id="10591-153">"Go to sleep"</span></span>
* <span data-ttu-id="10591-154">"¿Qué hora es?"</span><span class="sxs-lookup"><span data-stu-id="10591-154">"What time is it?"</span></span>
* <span data-ttu-id="10591-155">"¿Cuánta batería he dejado?"</span><span class="sxs-lookup"><span data-stu-id="10591-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="10591-156">"Llamada <contact>" (requiere Skype para HoloLens)</span><span class="sxs-lookup"><span data-stu-id="10591-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="10591-157">"Verlo, decirlo"</span><span class="sxs-lookup"><span data-stu-id="10591-157">"See It, Say It"</span></span>

<span data-ttu-id="10591-158">HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir.</span><span class="sxs-lookup"><span data-stu-id="10591-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="10591-159">Por ejemplo, al mirar una aplicación en 2D, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.</span><span class="sxs-lookup"><span data-stu-id="10591-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Al mirar una aplicación 2D o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.](images/microphone-600px.png)

<span data-ttu-id="10591-161">Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="10591-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="10591-162">Para reforzar esto, mientras se Gazing en un botón, verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de "presionar".</span><span class="sxs-lookup"><span data-stu-id="10591-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="10591-163">![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="10591-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="10591-164">*"Ver, por ejemplo," los comandos aparecen debajo de los botones*</span><span class="sxs-lookup"><span data-stu-id="10591-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="10591-165">Comandos de voz para la manipulación rápida de hologramas</span><span class="sxs-lookup"><span data-stu-id="10591-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="10591-166">También hay una serie de comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación.</span><span class="sxs-lookup"><span data-stu-id="10591-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="10591-167">Estos comandos de voz funcionan en aplicaciones 2D y en objetos 3D que se han colocado en el mundo.</span><span class="sxs-lookup"><span data-stu-id="10591-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="10591-168">**Comandos de manipulación de hologramas**</span><span class="sxs-lookup"><span data-stu-id="10591-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="10591-169">Me encuentro</span><span class="sxs-lookup"><span data-stu-id="10591-169">Face me</span></span>
* <span data-ttu-id="10591-170">Mayor | Enhance</span><span class="sxs-lookup"><span data-stu-id="10591-170">Bigger | Enhance</span></span>
* <span data-ttu-id="10591-171">Disminuye</span><span class="sxs-lookup"><span data-stu-id="10591-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="10591-172">Dictado</span><span class="sxs-lookup"><span data-stu-id="10591-172">Dictation</span></span>

<span data-ttu-id="10591-173">En lugar de escribir con grifos de [aire](gestures.md#air-tap), el dictado de voz puede ser más eficaz para escribir texto en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="10591-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="10591-174">Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="10591-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="10591-175">![El dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="10591-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="10591-176">*El dictado de voz comienza seleccionando el botón micrófono del teclado.*</span><span class="sxs-lookup"><span data-stu-id="10591-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="10591-177">Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir.</span><span class="sxs-lookup"><span data-stu-id="10591-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="10591-178">Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.</span><span class="sxs-lookup"><span data-stu-id="10591-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="10591-179">Comunicación</span><span class="sxs-lookup"><span data-stu-id="10591-179">Communication</span></span>

<span data-ttu-id="10591-180">En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que puede consumir la aplicación.</span><span class="sxs-lookup"><span data-stu-id="10591-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="10591-181">Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otras que se pueden usar para el audio del entorno ambiente. escenarios de captura (es decir, "videocámara").</span><span class="sxs-lookup"><span data-stu-id="10591-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="10591-182">La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono 16kHz 24bit de la voz del usuario</span><span class="sxs-lookup"><span data-stu-id="10591-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="10591-183">La categoría AudioCategory_Speech Stream está personalizada para el motor de voz HoloLens (Windows) y le proporciona un flujo mono 16kHz 24bit de la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="10591-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="10591-184">Los motores de voz de terceros pueden usar esta categoría si es necesario.</span><span class="sxs-lookup"><span data-stu-id="10591-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="10591-185">La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits de 48 bits.</span><span class="sxs-lookup"><span data-stu-id="10591-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="10591-186">Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10591-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="10591-187">Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.</span><span class="sxs-lookup"><span data-stu-id="10591-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="10591-188">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="10591-188">Troubleshooting</span></span>

<span data-ttu-id="10591-189">Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto.</span><span class="sxs-lookup"><span data-stu-id="10591-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="10591-190">En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.</span><span class="sxs-lookup"><span data-stu-id="10591-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="10591-191">En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD.</span><span class="sxs-lookup"><span data-stu-id="10591-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="10591-192">Antes de ese primer evento de cierre de sesión/en el momento de pasar a través de WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.</span><span class="sxs-lookup"><span data-stu-id="10591-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="10591-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="10591-193">See also</span></span>
* [<span data-ttu-id="10591-194">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="10591-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="10591-195">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="10591-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="10591-196">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="10591-196">MR Input 212: Voice</span></span>](holograms-212.md)
