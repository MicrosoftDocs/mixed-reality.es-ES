---
title: Entrada de voz en Unity
description: Unity expone tres maneras de agregar una entrada de voz a la aplicación Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, micrófono, dictado, voz
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548683"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="3b1de-104">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="3b1de-104">Voice input in Unity</span></span>

<span data-ttu-id="3b1de-105">Unity expone tres maneras de agregar una [entrada de voz](voice-input.md) a la aplicación de Unity.</span><span class="sxs-lookup"><span data-stu-id="3b1de-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="3b1de-106">Con KeywordRecognizer (uno de los dos tipos de PhraseRecognizers), se puede proporcionar a la aplicación una matriz de comandos de cadena para realizar escuchas.</span><span class="sxs-lookup"><span data-stu-id="3b1de-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="3b1de-107">Con GrammarRecognizer (el otro tipo de PhraseRecognizer), se puede proporcionar a la aplicación un archivo SRGS que defina una gramática específica para realizar escuchas.</span><span class="sxs-lookup"><span data-stu-id="3b1de-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="3b1de-108">Con el DictationRecognizer, la aplicación puede escuchar cualquier palabra y proporcionar al usuario una nota u otra presentación de la voz.</span><span class="sxs-lookup"><span data-stu-id="3b1de-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="3b1de-109">Solo se puede controlar el reconocimiento de dictado o de frase a la vez.</span><span class="sxs-lookup"><span data-stu-id="3b1de-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="3b1de-110">Esto significa que, si GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no puede estar activo y viceversa.</span><span class="sxs-lookup"><span data-stu-id="3b1de-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="3b1de-111">Habilitación de la funcionalidad de Voice</span><span class="sxs-lookup"><span data-stu-id="3b1de-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="3b1de-112">La capacidad del **micrófono** se debe declarar para que una aplicación aproveche la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="3b1de-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="3b1de-113">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="3b1de-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="3b1de-114">Haga clic en la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="3b1de-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="3b1de-115">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="3b1de-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="3b1de-116">Reconocimiento de frases</span><span class="sxs-lookup"><span data-stu-id="3b1de-116">Phrase Recognition</span></span>

<span data-ttu-id="3b1de-117">Para permitir que la aplicación escuche frases específicas que habla el usuario, realice alguna acción; debe:</span><span class="sxs-lookup"><span data-stu-id="3b1de-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="3b1de-118">Especificar las frases que se van a escuchar con KeywordRecognizer o GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="3b1de-119">Controle el evento OnPhraseRecognized y tome las medidas correspondientes a la frase reconocida</span><span class="sxs-lookup"><span data-stu-id="3b1de-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="3b1de-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-120">KeywordRecognizer</span></span>

<span data-ttu-id="3b1de-121">**Espacio de nombres**: *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="3b1de-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="3b1de-122">**Distintos** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="3b1de-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="3b1de-123">Necesitamos algunas instrucciones Using para guardar algunas pulsaciones de teclas:</span><span class="sxs-lookup"><span data-stu-id="3b1de-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="3b1de-124">A continuación, vamos a agregar algunos campos a la clase para almacenar el reconocedor y la palabra clave > Diccionario de acciones:</span><span class="sxs-lookup"><span data-stu-id="3b1de-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="3b1de-125">Ahora, agregue una palabra clave al diccionario (por ejemplo, dentro de un método Start ()).</span><span class="sxs-lookup"><span data-stu-id="3b1de-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="3b1de-126">Estamos agregando la palabra clave "activar" en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="3b1de-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="3b1de-127">Cree el reconocedor de palabras clave e indíquele lo que desea reconocer:</span><span class="sxs-lookup"><span data-stu-id="3b1de-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="3b1de-128">Regístrese ahora para el evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="3b1de-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="3b1de-129">Un controlador de ejemplo es:</span><span class="sxs-lookup"><span data-stu-id="3b1de-129">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="3b1de-130">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="3b1de-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="3b1de-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-131">GrammarRecognizer</span></span>

<span data-ttu-id="3b1de-132">**System.IO** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="3b1de-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="3b1de-133">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="3b1de-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="3b1de-134">El GrammarRecognizer se usa si se especifica la gramática de reconocimiento mediante SRGS.</span><span class="sxs-lookup"><span data-stu-id="3b1de-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="3b1de-135">Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más complejas o si desea activar o desactivar fácilmente conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="3b1de-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="3b1de-136">Vea: [Cree gramáticas con XML de SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obtener información sobre el formato de archivo.</span><span class="sxs-lookup"><span data-stu-id="3b1de-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="3b1de-137">Una vez que tenga la gramática de SRGS y esté en el proyecto en una [carpeta StreamingAssets](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="3b1de-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="3b1de-138">Cree un GrammarRecognizer y pásele la ruta de acceso al archivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="3b1de-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="3b1de-139">Regístrese ahora para el evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="3b1de-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="3b1de-140">Obtendrá una devolución de llamada que contiene la información especificada en la gramática de SRGS que puede controlar de forma adecuada.</span><span class="sxs-lookup"><span data-stu-id="3b1de-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="3b1de-141">La mayor parte de la información importante se proporcionará en la matriz semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="3b1de-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="3b1de-142">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="3b1de-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="3b1de-143">Dictado</span><span class="sxs-lookup"><span data-stu-id="3b1de-143">Dictation</span></span>

<span data-ttu-id="3b1de-144">**System.IO** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="3b1de-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="3b1de-145">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="3b1de-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="3b1de-146">Use DictationRecognizer para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="3b1de-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="3b1de-147">DictationRecognizer expone la funcionalidad de [dictado](voice-input.md#dictation) y admite el registro y la escucha de eventos de hipótesis y frases completadas, de forma que puede enviar comentarios al usuario mientras hablan y después.</span><span class="sxs-lookup"><span data-stu-id="3b1de-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="3b1de-148">Los métodos Start () y STOP () respectivamente habilitan y deshabilitan el reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="3b1de-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="3b1de-149">Una vez que se realiza con el reconocedor, se debe desechar mediante el método Dispose () para liberar los recursos que utiliza.</span><span class="sxs-lookup"><span data-stu-id="3b1de-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="3b1de-150">Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se publican antes.</span><span class="sxs-lookup"><span data-stu-id="3b1de-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="3b1de-151">Solo se necesitan algunos pasos para empezar a trabajar con el dictado:</span><span class="sxs-lookup"><span data-stu-id="3b1de-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="3b1de-152">Crear un nuevo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="3b1de-153">Controlar los eventos de dictado</span><span class="sxs-lookup"><span data-stu-id="3b1de-153">Handle Dictation events</span></span>
3. <span data-ttu-id="3b1de-154">Inicio de DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="3b1de-155">Habilitar la funcionalidad para el dictado</span><span class="sxs-lookup"><span data-stu-id="3b1de-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="3b1de-156">La capacidad de "cliente de Internet", además de la capacidad de "micrófono" mencionada anteriormente, se debe declarar para que una aplicación aproveche el dictado.</span><span class="sxs-lookup"><span data-stu-id="3b1de-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="3b1de-157">En el editor de Unity, vaya a la página "Editar > configuración del proyecto > reproductor" para ir a la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="3b1de-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="3b1de-158">Haga clic en la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="3b1de-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="3b1de-159">En la sección "configuración de publicación > funcionalidades", Compruebe la funcionalidad de **InternetClient** .</span><span class="sxs-lookup"><span data-stu-id="3b1de-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="3b1de-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="3b1de-160">DictationRecognizer</span></span>

<span data-ttu-id="3b1de-161">Cree un DictationRecognizer como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="3b1de-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="3b1de-162">Hay cuatro eventos de dictado a los que se puede suscribir y controlar para implementar el comportamiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="3b1de-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="3b1de-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="3b1de-163">DictationResult</span></span>
2. <span data-ttu-id="3b1de-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="3b1de-164">DictationComplete</span></span>
3. <span data-ttu-id="3b1de-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="3b1de-165">DictationHypothesis</span></span>
4. <span data-ttu-id="3b1de-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="3b1de-166">DictationError</span></span>

<span data-ttu-id="3b1de-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="3b1de-167">**DictationResult**</span></span>

<span data-ttu-id="3b1de-168">Este evento se desencadena después de que el usuario se pausa, normalmente al final de una frase.</span><span class="sxs-lookup"><span data-stu-id="3b1de-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="3b1de-169">Aquí se devuelve la cadena completa reconocida.</span><span class="sxs-lookup"><span data-stu-id="3b1de-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="3b1de-170">En primer lugar, suscríbase al evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="3b1de-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="3b1de-171">A continuación, controle la devolución de llamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="3b1de-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="3b1de-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="3b1de-172">**DictationHypothesis**</span></span>

<span data-ttu-id="3b1de-173">Este evento se desencadena continuamente mientras el usuario está hablando.</span><span class="sxs-lookup"><span data-stu-id="3b1de-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="3b1de-174">A medida que el reconocedor realiza escuchas, proporciona texto de lo que se oye hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="3b1de-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="3b1de-175">En primer lugar, suscríbase al evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="3b1de-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="3b1de-176">A continuación, controle la devolución de llamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="3b1de-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="3b1de-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="3b1de-177">**DictationComplete**</span></span>

<span data-ttu-id="3b1de-178">Este evento se desencadena cuando se detiene el reconocedor, ya sea de detención (), se ha producido un tiempo de espera o de algún otro error.</span><span class="sxs-lookup"><span data-stu-id="3b1de-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="3b1de-179">En primer lugar, suscríbase al evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="3b1de-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="3b1de-180">A continuación, controle la devolución de llamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="3b1de-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="3b1de-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="3b1de-181">**DictationError**</span></span>

<span data-ttu-id="3b1de-182">Este evento se desencadena cuando se produce un error.</span><span class="sxs-lookup"><span data-stu-id="3b1de-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="3b1de-183">En primer lugar, suscríbase al evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="3b1de-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="3b1de-184">A continuación, controle la devolución de llamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="3b1de-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="3b1de-185">Una vez que haya suscrito y controlado los eventos de dictado que le interesan, inicie el reconocedor de dictado para comenzar a recibir eventos.</span><span class="sxs-lookup"><span data-stu-id="3b1de-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="3b1de-186">Si ya no desea mantener el DictationRecognizer en torno, debe cancelar la suscripción a los eventos y eliminar el DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="3b1de-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="3b1de-187">**Útiles**</span><span class="sxs-lookup"><span data-stu-id="3b1de-187">**Tips**</span></span>
* <span data-ttu-id="3b1de-188">Los métodos Start () y STOP () respectivamente habilitan y deshabilitan el reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="3b1de-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="3b1de-189">Una vez que se realiza con el reconocedor, se debe desechar mediante el método Dispose () para liberar los recursos que utiliza.</span><span class="sxs-lookup"><span data-stu-id="3b1de-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="3b1de-190">Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se publican antes.</span><span class="sxs-lookup"><span data-stu-id="3b1de-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="3b1de-191">Los tiempos de espera se producen después de un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="3b1de-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="3b1de-192">Puede buscar estos tiempos de espera en el evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="3b1de-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="3b1de-193">Hay dos tiempos de espera que se deben tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="3b1de-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="3b1de-194">Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="3b1de-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="3b1de-195">Si el reconocedor ha dado un resultado pero oye el silencio durante veinte segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="3b1de-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="3b1de-196">Usar el reconocimiento de frases y el dictado</span><span class="sxs-lookup"><span data-stu-id="3b1de-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="3b1de-197">Si desea usar tanto el reconocimiento de frases como el dictado en la aplicación, deberá apagarlo completamente antes de poder iniciar el otro.</span><span class="sxs-lookup"><span data-stu-id="3b1de-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="3b1de-198">Si tiene varios KeywordRecognizers en ejecución, puede cerrarlos todos a la vez con:</span><span class="sxs-lookup"><span data-stu-id="3b1de-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="3b1de-199">Para restaurar todos los reconocedores a su estado anterior, una vez detenido el DictationRecognizer, puede llamar a:</span><span class="sxs-lookup"><span data-stu-id="3b1de-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="3b1de-200">También puede iniciar una KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem también.</span><span class="sxs-lookup"><span data-stu-id="3b1de-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="3b1de-201">Uso de la aplicación auxiliar de micrófono</span><span class="sxs-lookup"><span data-stu-id="3b1de-201">Using the microphone helper</span></span>

<span data-ttu-id="3b1de-202">El kit de herramientas de realidad mixta en GitHub contiene una clase auxiliar de micrófono para sugerir a los desarrolladores si hay un micrófono utilizable en el sistema.</span><span class="sxs-lookup"><span data-stu-id="3b1de-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="3b1de-203">Un uso para este es el lugar en el que desea comprobar si hay un micrófono en el sistema antes de mostrar las sugerencias de interacción de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b1de-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="3b1de-204">El script de la aplicación auxiliar de micrófono se puede encontrar en la [carpeta INPUT/scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="3b1de-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="3b1de-205">El repositorio de GitHub también contiene un [pequeño ejemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) en el que se muestra cómo usar el ayudante.</span><span class="sxs-lookup"><span data-stu-id="3b1de-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="3b1de-206">Entrada de voz en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="3b1de-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="3b1de-207">Puede encontrar ejemplos de la entrada de voz en esta escena.</span><span class="sxs-lookup"><span data-stu-id="3b1de-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="3b1de-208">HoloToolkit-Examples/INPUT/Scenes/SpeechInputSource. Unity</span><span class="sxs-lookup"><span data-stu-id="3b1de-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
