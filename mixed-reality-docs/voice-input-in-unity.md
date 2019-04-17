---
title: Entrada de voz en Unity
description: Unity expone tres maneras de agregar la entrada de voz a su aplicación de Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, micrófono, dictado, voz
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605727"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="054c0-104">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="054c0-104">Voice input in Unity</span></span>

<span data-ttu-id="054c0-105">Unity expone tres maneras de agregar [entrada de voz](voice-input.md) a la aplicación de Unity.</span><span class="sxs-lookup"><span data-stu-id="054c0-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="054c0-106">Con el KeywordRecognizer (uno de los dos tipos de PhraseRecognizers), la aplicación se puede proporcionar una matriz de cadena de comandos para escuchar.</span><span class="sxs-lookup"><span data-stu-id="054c0-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="054c0-107">Con el GrammarRecognizer (el otro tipo de PhraseRecognizer), la aplicación se puede proporcionar un archivo SRGS define una gramática específicos para que escuche.</span><span class="sxs-lookup"><span data-stu-id="054c0-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="054c0-108">Con el DictationRecognizer, la aplicación puede escuchar cualquier palabra y proporcionar al usuario una nota u otra pantalla de su voz.</span><span class="sxs-lookup"><span data-stu-id="054c0-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="054c0-109">Solo el dictado o reconocimiento de frase se puede controlar a la vez.</span><span class="sxs-lookup"><span data-stu-id="054c0-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="054c0-110">Esto significa que si un GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no pueden activarse y viceversa.</span><span class="sxs-lookup"><span data-stu-id="054c0-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="054c0-111">Habilitación de la capacidad de voz</span><span class="sxs-lookup"><span data-stu-id="054c0-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="054c0-112">El **micrófono** se debe declarar la funcionalidad de una aplicación aprovechar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="054c0-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="054c0-113">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="054c0-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="054c0-114">Haga clic en la pestaña "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="054c0-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="054c0-115">En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad</span><span class="sxs-lookup"><span data-stu-id="054c0-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="054c0-116">Reconocimiento de frase</span><span class="sxs-lookup"><span data-stu-id="054c0-116">Phrase Recognition</span></span>

<span data-ttu-id="054c0-117">Para habilitar la aplicación realizar escuchas de específicos de frases habla por el usuario, a continuación, realizar alguna acción, deberá:</span><span class="sxs-lookup"><span data-stu-id="054c0-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="054c0-118">Especifique qué frases para que escuche para usar un KeywordRecognizer o GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="054c0-119">Controle el evento OnPhraseRecognized y tomar la acción que corresponde a la frase reconocida</span><span class="sxs-lookup"><span data-stu-id="054c0-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="054c0-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-120">KeywordRecognizer</span></span>

<span data-ttu-id="054c0-121">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="054c0-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="054c0-122">**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="054c0-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="054c0-123">Necesitaremos algunas instrucciones using al guardar algunas pulsaciones de teclas:</span><span class="sxs-lookup"><span data-stu-id="054c0-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="054c0-124">A continuación, vamos a agregar unos cuantos campos a la clase para almacenar el módulo de reconocimiento y la palabra clave -> diccionario de acción:</span><span class="sxs-lookup"><span data-stu-id="054c0-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="054c0-125">Ahora puede agregar una palabra clave al diccionario (por ejemplo, dentro de un método Start()).</span><span class="sxs-lookup"><span data-stu-id="054c0-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="054c0-126">Estamos agregando la palabra clave "activar" en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="054c0-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="054c0-127">Crear el módulo de reconocimiento de la palabra clave e indicarle lo que debemos reconocer:</span><span class="sxs-lookup"><span data-stu-id="054c0-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="054c0-128">Regístrese ahora para el evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="054c0-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="054c0-129">Es un controlador de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="054c0-129">An example handler is:</span></span>

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

<span data-ttu-id="054c0-130">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="054c0-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="054c0-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-131">GrammarRecognizer</span></span>

<span data-ttu-id="054c0-132">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="054c0-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="054c0-133">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="054c0-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="054c0-134">Se usa el GrammarRecognizer si está especificando la gramática de reconocimiento de SRGS.</span><span class="sxs-lookup"><span data-stu-id="054c0-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="054c0-135">Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más compleja, o si desea activar y desactivar los conjuntos de comandos la fácilmente.</span><span class="sxs-lookup"><span data-stu-id="054c0-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="054c0-136">Vea: [Crear mediante gramáticas XML de SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obtener información de formato de archivo.</span><span class="sxs-lookup"><span data-stu-id="054c0-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="054c0-137">Una vez que tiene la gramática de SRGS, y se encuentra en el proyecto en un [StreamingAssets carpeta](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="054c0-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="054c0-138">Cree un GrammarRecognizer y pasar la ruta de acceso al archivo de SRGS:</span><span class="sxs-lookup"><span data-stu-id="054c0-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="054c0-139">Regístrese ahora para el evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="054c0-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="054c0-140">Recibirá una devolución de llamada que contiene la información especificada en la gramática de SRGS que pueden controlar adecuadamente.</span><span class="sxs-lookup"><span data-stu-id="054c0-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="054c0-141">Se proporcionará la mayor parte de la información importante en la matriz semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="054c0-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="054c0-142">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="054c0-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="054c0-143">Dictado</span><span class="sxs-lookup"><span data-stu-id="054c0-143">Dictation</span></span>

<span data-ttu-id="054c0-144">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="054c0-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="054c0-145">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="054c0-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="054c0-146">Utilice el DictationRecognizer para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="054c0-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="054c0-147">Expone el DictationRecognizer [dictado](voice-input.md#dictation) funcionalidad y permite registrar y escuchar las hipótesis y una frase completa eventos, por lo que puede proporcionar comentarios para el usuario mientras habla y posteriormente.</span><span class="sxs-lookup"><span data-stu-id="054c0-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="054c0-148">Métodos Start() y Stop() habilitan y deshabilitar el reconocimiento de dictado respectivamente.</span><span class="sxs-lookup"><span data-stu-id="054c0-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="054c0-149">Una vez terminado el reconocedor, debe eliminarse mediante el método Dispose() para liberar los recursos que usa.</span><span class="sxs-lookup"><span data-stu-id="054c0-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="054c0-150">Lanzará estos recursos automáticamente durante la recolección de elementos con un costo de rendimiento adicionales si no se libera antes de eso.</span><span class="sxs-lookup"><span data-stu-id="054c0-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="054c0-151">Hay solo unos pocos pasos necesarios para empezar a trabajar con dictado:</span><span class="sxs-lookup"><span data-stu-id="054c0-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="054c0-152">Crear un nuevo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="054c0-153">Controlar eventos de dictado</span><span class="sxs-lookup"><span data-stu-id="054c0-153">Handle Dictation events</span></span>
3. <span data-ttu-id="054c0-154">Iniciar el DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="054c0-155">Habilitación de la capacidad de dictado</span><span class="sxs-lookup"><span data-stu-id="054c0-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="054c0-156">La capacidad de "Cliente de Internet", además de la funcionalidad de "Micrófono" se ha mencionado anteriormente, se debe declarar para que una aplicación aprovechar el dictado.</span><span class="sxs-lookup"><span data-stu-id="054c0-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="054c0-157">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a la página "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="054c0-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="054c0-158">Haga clic en la pestaña "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="054c0-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="054c0-159">En la sección "Funcionalidades de publicación configuración >", compruebe el **InternetClient** capacidad</span><span class="sxs-lookup"><span data-stu-id="054c0-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="054c0-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="054c0-160">DictationRecognizer</span></span>

<span data-ttu-id="054c0-161">Crear un DictationRecognizer así:</span><span class="sxs-lookup"><span data-stu-id="054c0-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="054c0-162">Hay cuatro eventos de dictado que puedan estar suscrito a y normalmente para implementar el comportamiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="054c0-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="054c0-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="054c0-163">DictationResult</span></span>
2. <span data-ttu-id="054c0-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="054c0-164">DictationComplete</span></span>
3. <span data-ttu-id="054c0-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="054c0-165">DictationHypothesis</span></span>
4. <span data-ttu-id="054c0-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="054c0-166">DictationError</span></span>

<span data-ttu-id="054c0-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="054c0-167">**DictationResult**</span></span>

<span data-ttu-id="054c0-168">Este evento se desencadena después de que el usuario pone en pausa, normalmente al final de una frase.</span><span class="sxs-lookup"><span data-stu-id="054c0-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="054c0-169">El completo reconoce la cadena se devuelve aquí.</span><span class="sxs-lookup"><span data-stu-id="054c0-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="054c0-170">En primer lugar, se suscribe al evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="054c0-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="054c0-171">A continuación, controlar la devolución de llamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="054c0-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="054c0-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="054c0-172">**DictationHypothesis**</span></span>

<span data-ttu-id="054c0-173">Este evento se desencadena continuamente mientras está hablando con el usuario.</span><span class="sxs-lookup"><span data-stu-id="054c0-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="054c0-174">Como el reconocimiento de escucha, proporciona el texto de lo que es oído hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="054c0-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="054c0-175">En primer lugar, se suscribe al evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="054c0-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="054c0-176">A continuación, controlar la devolución de llamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="054c0-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="054c0-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="054c0-177">**DictationComplete**</span></span>

<span data-ttu-id="054c0-178">Este evento se desencadena cuando se detiene el reconocedor, ya sea desde Stop() llama, un tiempo de espera que se producen o algún otro error.</span><span class="sxs-lookup"><span data-stu-id="054c0-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="054c0-179">En primer lugar, se suscribe al evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="054c0-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="054c0-180">A continuación, controlar la devolución de llamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="054c0-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="054c0-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="054c0-181">**DictationError**</span></span>

<span data-ttu-id="054c0-182">Este evento se desencadena cuando se produce un error.</span><span class="sxs-lookup"><span data-stu-id="054c0-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="054c0-183">En primer lugar, se suscribe al evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="054c0-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="054c0-184">A continuación, controlar la devolución de llamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="054c0-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="054c0-185">Una vez que se haya suscrito y controla los eventos de dictado que le interesen, inicie el reconocimiento de dictado para empezar a recibir eventos.</span><span class="sxs-lookup"><span data-stu-id="054c0-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="054c0-186">Si ya no desea mantener el DictationRecognizer alrededor, deberá cancelar la suscripción a los eventos y desechar la DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="054c0-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="054c0-187">**Sugerencias**</span><span class="sxs-lookup"><span data-stu-id="054c0-187">**Tips**</span></span>
* <span data-ttu-id="054c0-188">Métodos Start() y Stop() habilitan y deshabilitar el reconocimiento de dictado respectivamente.</span><span class="sxs-lookup"><span data-stu-id="054c0-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="054c0-189">Una vez terminado el reconocedor, deben eliminarse mediante el método Dispose() para liberar los recursos que usa.</span><span class="sxs-lookup"><span data-stu-id="054c0-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="054c0-190">Lanzará estos recursos automáticamente durante la recolección de elementos con un costo de rendimiento adicionales si no se libera antes de eso.</span><span class="sxs-lookup"><span data-stu-id="054c0-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="054c0-191">Se producen tiempos de espera tras un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="054c0-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="054c0-192">Puede buscar estos tiempos de espera en el evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="054c0-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="054c0-193">Hay dos tiempos de espera a tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="054c0-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="054c0-194">Si el reconocedor se inicia y no oye ningún sonido para los primeros cinco segundos, lo hará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="054c0-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="054c0-195">Si el reconocedor ha dado un resultado pero, a continuación, oye silencio durante veinte segundos, lo hará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="054c0-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="054c0-196">Usar el reconocimiento de frase y el dictado</span><span class="sxs-lookup"><span data-stu-id="054c0-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="054c0-197">Si desea usar el reconocimiento de frase y el dictado en la aplicación, deberá totalmente apagar uno antes de empezar a otro.</span><span class="sxs-lookup"><span data-stu-id="054c0-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="054c0-198">Si tiene varios ejecución KeywordRecognizers, puede apagar ellos todas a la vez con:</span><span class="sxs-lookup"><span data-stu-id="054c0-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="054c0-199">Para restaurar todos los reconocedores a su estado anterior, una vez se ha detenido el DictationRecognizer, puede llamar:</span><span class="sxs-lookup"><span data-stu-id="054c0-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="054c0-200">También se pudo iniciar un KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem así.</span><span class="sxs-lookup"><span data-stu-id="054c0-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="054c0-201">Uso de la aplicación auxiliar de micrófono</span><span class="sxs-lookup"><span data-stu-id="054c0-201">Using the microphone helper</span></span>

<span data-ttu-id="054c0-202">El Kit de herramientas de realidad mixta en GitHub contiene una clase auxiliar de micrófono para sugerir a los desarrolladores si no hay un micrófono utilizable en el sistema.</span><span class="sxs-lookup"><span data-stu-id="054c0-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="054c0-203">Un uso para ella es donde puede que desee comprobar si hay micrófono en el sistema antes de mostrar cualquier voz sugerencias de interacción en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="054c0-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="054c0-204">El script de aplicación auxiliar de micrófono puede encontrarse en el [carpeta de entrada, Scripts o utilidades](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="054c0-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="054c0-205">El repositorio de GitHub contiene también un [pequeño ejemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) que muestra cómo utilizar la aplicación auxiliar.</span><span class="sxs-lookup"><span data-stu-id="054c0-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="054c0-206">Entrada de voz en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="054c0-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="054c0-207">Puede encontrar los ejemplos de la entrada de voz en esta escena.</span><span class="sxs-lookup"><span data-stu-id="054c0-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="054c0-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="054c0-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
