---
title: Entrada de voz
description: Entrada de voz es una entrada de núcleo para HoloLens y Windows Mixed Reality inmersivos. Voz puede usarse para los comandos, dictado, Cortana y mucho más.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voz, cortana, voz, de entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829949"
---
# <a name="voice-input"></a><span data-ttu-id="f757d-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="f757d-105">Voice input</span></span>

<span data-ttu-id="f757d-106">Voz es una de las tres formas de clave de entrada en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f757d-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="f757d-107">Permite un holograma de comandos directamente sin tener que usar [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="f757d-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="f757d-108">Puede simplemente [que mirar](gaze.md) en un holograma y diga su comando.</span><span class="sxs-lookup"><span data-stu-id="f757d-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="f757d-109">Entrada de voz puede ser una manera natural para comunicar su intención.</span><span class="sxs-lookup"><span data-stu-id="f757d-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="f757d-110">Voz es especialmente buena atravesar interfaces complejas, ya que permite a los usuarios Cortar a través de los menús anidados con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="f757d-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="f757d-111">Entrada de voz está basado el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admita la voz en todas las demás aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="f757d-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="f757d-112">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="f757d-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f757d-113"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="f757d-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f757d-114"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f757d-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f757d-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f757d-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f757d-116"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="f757d-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f757d-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="f757d-117">Voice input</span></span></td>
        <td><span data-ttu-id="f757d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f757d-118">✔️</span></span></td>
        <td><span data-ttu-id="f757d-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f757d-119">✔️</span></span></td>
        <td><span data-ttu-id="f757d-120">✔️ (con micrófono)</span><span class="sxs-lookup"><span data-stu-id="f757d-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="f757d-121">El comando "select"</span><span class="sxs-lookup"><span data-stu-id="f757d-121">The "select" command</span></span>

<span data-ttu-id="f757d-122">Incluso sin específicamente agregar compatibilidad con voz a su aplicación, los usuarios pueden activar hologramas simplemente al decir "select".</span><span class="sxs-lookup"><span data-stu-id="f757d-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="f757d-123">Este comportamiento es el mismo que un [en el aire](gestures.md#air-tap) en HoloLens, si se presiona el botón de selección en el [HoloLens clicker](hardware-accessories.md#hololens-clicker), o si se presiona el desencadenador en un [controlador de movimiento de Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="f757d-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="f757d-124">Oirá un sonido y aparece una información sobre herramientas con "select" como confirmación.</span><span class="sxs-lookup"><span data-stu-id="f757d-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="f757d-125">"Select" se habilita mediante un algoritmo de detección de la palabra clave de bajo consumo de energía para que siempre esté disponible para decir en cualquier momento con un impacto mínimo batería vida, incluso con las manos a su lado.</span><span class="sxs-lookup"><span data-stu-id="f757d-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="f757d-126">Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="f757d-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="f757d-127">![Diga "seleccionar" usar el comando de voz para la selección](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="f757d-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="f757d-128">*Diga "seleccionar" usar el comando de voz para la selección*</span><span class="sxs-lookup"><span data-stu-id="f757d-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="f757d-129">Hola Cortana</span><span class="sxs-lookup"><span data-stu-id="f757d-129">Hey Cortana</span></span>

<span data-ttu-id="f757d-130">También puede decir "Hola Cortana" para que aparezca de Cortana en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="f757d-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="f757d-131">No tendrá que esperar para que ella aparezca continuar le pide su pregunta u otorgándole una instrucción - por ejemplo, pruebe diciendo: "Hola Cortana ¿qué es el tiempo?"</span><span class="sxs-lookup"><span data-stu-id="f757d-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="f757d-132">como una frase única.</span><span class="sxs-lookup"><span data-stu-id="f757d-132">as a single sentence.</span></span> <span data-ttu-id="f757d-133">Para obtener más información acerca de Cortana y qué puede hacer, simplemente le solicito!</span><span class="sxs-lookup"><span data-stu-id="f757d-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="f757d-134">Diga "Hola Cortana qué decir?"</span><span class="sxs-lookup"><span data-stu-id="f757d-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="f757d-135">y le traemos una lista de comandos sugeridos y no laborables.</span><span class="sxs-lookup"><span data-stu-id="f757d-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="f757d-136">¿Si ya está en la aplicación de Cortana también puede hacer clic en el **?**</span><span class="sxs-lookup"><span data-stu-id="f757d-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="f757d-137">icono de la barra lateral para extraer el mismo menú.</span><span class="sxs-lookup"><span data-stu-id="f757d-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="f757d-138">**Comandos específicos de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f757d-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="f757d-139">"¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="f757d-139">"What can I say?"</span></span>
* <span data-ttu-id="f757d-140">"Go home" o "Ir a Inicio" - en lugar de [bloom](gestures.md#bloom) para llegar a [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="f757d-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="f757d-141">"Inicie <app>"</span><span class="sxs-lookup"><span data-stu-id="f757d-141">"Launch <app>"</span></span>
* <span data-ttu-id="f757d-142">"Mover <app> aquí"</span><span class="sxs-lookup"><span data-stu-id="f757d-142">"Move <app> here"</span></span>
* <span data-ttu-id="f757d-143">"Capturar una imagen"</span><span class="sxs-lookup"><span data-stu-id="f757d-143">"Take a picture"</span></span>
* <span data-ttu-id="f757d-144">"Iniciar grabación"</span><span class="sxs-lookup"><span data-stu-id="f757d-144">"Start recording"</span></span>
* <span data-ttu-id="f757d-145">"Detener la grabación"</span><span class="sxs-lookup"><span data-stu-id="f757d-145">"Stop recording"</span></span>
* <span data-ttu-id="f757d-146">"Aumentar el brillo"</span><span class="sxs-lookup"><span data-stu-id="f757d-146">"Increase the brightness"</span></span>
* <span data-ttu-id="f757d-147">"Reduce el brillo"</span><span class="sxs-lookup"><span data-stu-id="f757d-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="f757d-148">"Aumentar el volumen"</span><span class="sxs-lookup"><span data-stu-id="f757d-148">"Increase the volume"</span></span>
* <span data-ttu-id="f757d-149">"Reducir el volumen"</span><span class="sxs-lookup"><span data-stu-id="f757d-149">"Decrease the volume"</span></span>
* <span data-ttu-id="f757d-150">"Activar" o "Desactivar"</span><span class="sxs-lookup"><span data-stu-id="f757d-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="f757d-151">"Apagar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="f757d-151">"Shut down the device"</span></span>
* <span data-ttu-id="f757d-152">"Reinicie el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="f757d-152">"Restart the device"</span></span>
* <span data-ttu-id="f757d-153">"Ir al modo de suspensión"</span><span class="sxs-lookup"><span data-stu-id="f757d-153">"Go to sleep"</span></span>
* <span data-ttu-id="f757d-154">"¿A qué hora es?"</span><span class="sxs-lookup"><span data-stu-id="f757d-154">"What time is it?"</span></span>
* <span data-ttu-id="f757d-155">"La batería ¿cuánto me queda?"</span><span class="sxs-lookup"><span data-stu-id="f757d-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="f757d-156">"Llamar a <contact>" (requiere Skype para HoloLens)</span><span class="sxs-lookup"><span data-stu-id="f757d-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="f757d-157">"Lo ve, diga"</span><span class="sxs-lookup"><span data-stu-id="f757d-157">"See It, Say It"</span></span>

<span data-ttu-id="f757d-158">HoloLens tienen un modelo de "verlo, diga" para la entrada de voz, donde las etiquetas de los botones de indicar a los usuarios también puede decir qué comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="f757d-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="f757d-159">Por ejemplo, al examinar una aplicación 2D, un usuario puede decir el comando "Ajustar" que se verán en la barra de aplicaciones para ajustar la posición de la aplicación en el mundo.</span><span class="sxs-lookup"><span data-stu-id="f757d-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Al examinar una aplicación 2D u holograma, un usuario puede decir el comando "Ajustar" que se verán en la barra de aplicaciones para ajustar la posición de la aplicación en el mundo](images/microphone-600px.png)

<span data-ttu-id="f757d-161">Cuando las aplicaciones siguen esta regla, pueden comprender fácilmente a los usuarios qué decirles a controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="f757d-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="f757d-162">Para reforzar, mientras gazing en un botón, verá una información sobre herramientas "voz permanencia" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para comunicar para "presionar".</span><span class="sxs-lookup"><span data-stu-id="f757d-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="f757d-163">![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="f757d-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="f757d-164">*"Vea, diga" comandos aparecen debajo de los botones*</span><span class="sxs-lookup"><span data-stu-id="f757d-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="f757d-165">Comandos de voz para la manipulación rápida de holograma</span><span class="sxs-lookup"><span data-stu-id="f757d-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="f757d-166">También hay una serie de voz comandos que puede decir al gazing en un holograma para realizar rápidamente tareas de manipulación.</span><span class="sxs-lookup"><span data-stu-id="f757d-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="f757d-167">Estos comandos de voz funcionan en aplicaciones 2D, así como objetos 3D que se han realizado en el mundo.</span><span class="sxs-lookup"><span data-stu-id="f757d-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="f757d-168">**Comandos de manipulación de holograma**</span><span class="sxs-lookup"><span data-stu-id="f757d-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="f757d-169">Se enfrentan a mí</span><span class="sxs-lookup"><span data-stu-id="f757d-169">Face me</span></span>
* <span data-ttu-id="f757d-170">Mayor | Mejorar</span><span class="sxs-lookup"><span data-stu-id="f757d-170">Bigger | Enhance</span></span>
* <span data-ttu-id="f757d-171">Más pequeñas</span><span class="sxs-lookup"><span data-stu-id="f757d-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="f757d-172">Dictado</span><span class="sxs-lookup"><span data-stu-id="f757d-172">Dictation</span></span>

<span data-ttu-id="f757d-173">En lugar de escribir con [derivaciones del aire](gestures.md#air-tap), dictado de voz puede ser más eficaz para escribir texto en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="f757d-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="f757d-174">Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="f757d-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="f757d-175">![Dictado de voz comienza seleccionando el botón de micrófono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="f757d-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="f757d-176">*Dictado de voz comienza seleccionando el botón de micrófono en el teclado*</span><span class="sxs-lookup"><span data-stu-id="f757d-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="f757d-177">Siempre que el teclado holográfico está activo, puede cambiar al modo de dictado en lugar de escribir.</span><span class="sxs-lookup"><span data-stu-id="f757d-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="f757d-178">Seleccione el micrófono junto al cuadro de entrada de texto para empezar a trabajar.</span><span class="sxs-lookup"><span data-stu-id="f757d-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="f757d-179">Comunicación</span><span class="sxs-lookup"><span data-stu-id="f757d-179">Communication</span></span>

<span data-ttu-id="f757d-180">Para las aplicaciones que desean aprovechar las ventajas de la entrada de audio personalizada proporcionadas por HoloLens de opciones de procesamiento, es importante comprender los distintos [categorías de la secuencia de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) puede consumir la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f757d-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="f757d-181">Admite Windows 10 realiza varias categorías de flujo diferentes y HoloLens usa de tres de estas para permitir un procesamiento personalizado optimizar la calidad de audio del micrófono adaptada de voz, la comunicación y otros que se puede usar para el sonido de ambiente del entorno escenarios de captura (es decir, "cámaras de vídeo").</span><span class="sxs-lookup"><span data-stu-id="f757d-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="f757d-182">La categoría de la secuencia AudioCategory_Communications se personaliza para escenarios de calidad y la narración de llamada y proporciona al cliente con una secuencia de audio mono 24 de kHz 16 bits de la voz del usuario</span><span class="sxs-lookup"><span data-stu-id="f757d-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="f757d-183">La categoría de la secuencia AudioCategory_Speech personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia de mono 24 de kHz 16 bits de la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="f757d-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="f757d-184">Esta categoría se puede usar por 3rd motores de terceros de voz si es necesario.</span><span class="sxs-lookup"><span data-stu-id="f757d-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="f757d-185">La categoría de la secuencia AudioCategory_Other se personaliza para la grabación de audio de ambiente del entorno y proporciona al cliente con una secuencia de audio estéreo de 48 bits 24 kHz.</span><span class="sxs-lookup"><span data-stu-id="f757d-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="f757d-186">Todo este procesamiento de audio es lo que significa que mucho menos energía que si se realiza el procesamiento mismo de la CPU de HoloLens de drenaje de las características de aceleración de hardware.</span><span class="sxs-lookup"><span data-stu-id="f757d-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="f757d-187">Evite ejecutar otra entrada de audio de procesamiento de la CPU para maximizar la duración de la batería del sistema y aprovechar las ventajas de la compilación, descarga el procesamiento de entrada de audio.</span><span class="sxs-lookup"><span data-stu-id="f757d-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f757d-188">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="f757d-188">Troubleshooting</span></span>

<span data-ttu-id="f757d-189">Si tiene un "Hola Cortana" y los problemas con "select", intente mover a un espacio y más suave, al lado opuesto al origen de ruido o hablando más alto.</span><span class="sxs-lookup"><span data-stu-id="f757d-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="f757d-190">En este momento, todos los reconocimiento de voz en HoloLens se optimizan y optimizado específicamente para hablantes nativos de inglés de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="f757d-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="f757d-191">La versión de Windows Mixed Reality Developer Edition 2017, la lógica de administración de extremo de audio funcionará correctamente (de manera indefinida) después de iniciar sesión alejar y atrás en el escritorio del equipo después de la conexión HMD inicial.</span><span class="sxs-lookup"><span data-stu-id="f757d-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="f757d-192">Antes de ese primer inicio de sesión o en el evento después de pasar por WMR OOBE, el usuario podría experimentar diversos problemas de funcionalidad de audio comprendido entre sin audio sin audio cambiar dependiendo de cómo se ha configurado el sistema antes de conectar el HMD por primera vez.</span><span class="sxs-lookup"><span data-stu-id="f757d-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f757d-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="f757d-193">See also</span></span>
* [<span data-ttu-id="f757d-194">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="f757d-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="f757d-195">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="f757d-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="f757d-196">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="f757d-196">MR Input 212: Voice</span></span>](holograms-212.md)
