---
title: Entrada de voz en DirectX
description: Explica cómo implementar comandos de voz y reconocimiento de frases y oraciones pequeño en una aplicación de DirectX para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: tutorial, los comandos de voz, frase, reconocimiento, voz, directx, plataforma, cortana, realidad mixta de windows
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605784"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="18c07-104">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="18c07-104">Voice input in DirectX</span></span>

<span data-ttu-id="18c07-105">En este tema se explica cómo implementar [comandos de voz](voice-input.md)y el reconocimiento de frases y oraciones pequeño en una aplicación de DirectX para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="18c07-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="18c07-106">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="18c07-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="18c07-107">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="18c07-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="18c07-108">Usar un SpeechRecognizer para el reconocimiento de continua de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="18c07-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="18c07-109">En esta sección, se describe cómo usar el reconocimiento de voz continua para habilitar los comandos de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="18c07-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="18c07-110">Este tutorial usa código desde el [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) ejemplo.</span><span class="sxs-lookup"><span data-stu-id="18c07-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="18c07-111">Cuando se ejecuta el ejemplo, diga el nombre de uno de los comandos registrados de color para cambiar el color del cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="18c07-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="18c07-112">En primer lugar, cree un nuevo **Windows::Media::SpeechRecognition::SpeechRecognizer** instancia.</span><span class="sxs-lookup"><span data-stu-id="18c07-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="18c07-113">Desde *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="18c07-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="18c07-114">Deberá crear una lista de comandos de voz para el reconocedor escuchar.</span><span class="sxs-lookup"><span data-stu-id="18c07-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="18c07-115">En este caso, creamos un conjunto de comandos para cambiar el color de un holograma.</span><span class="sxs-lookup"><span data-stu-id="18c07-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="18c07-116">Por motivos de comodidad, también creamos los datos que vamos a usar para los comandos más adelante.</span><span class="sxs-lookup"><span data-stu-id="18c07-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="18c07-117">Los comandos se pueden especificar mediante fonéticas palabras que no esté en un diccionario:</span><span class="sxs-lookup"><span data-stu-id="18c07-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="18c07-118">La lista de comandos se carga en la lista de restricciones para el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="18c07-119">Esto se realiza mediante un [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="18c07-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="18c07-120">Suscribirse a la [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) eventos en el reconocimiento de voz [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="18c07-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="18c07-121">Este evento notifica a la aplicación cuando uno de los comandos se le ha reconocido.</span><span class="sxs-lookup"><span data-stu-id="18c07-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="18c07-122">Su **OnResultGenerated** controlador de eventos recibe datos de evento en un [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instancia.</span><span class="sxs-lookup"><span data-stu-id="18c07-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="18c07-123">Si es mayor que el umbral que se ha definido la confianza, la aplicación debe tener en cuenta que se produjo el evento.</span><span class="sxs-lookup"><span data-stu-id="18c07-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="18c07-124">Guardar los datos del evento para que puede hacer uso de ella en un bucle de actualización posterior.</span><span class="sxs-lookup"><span data-stu-id="18c07-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="18c07-125">Desde *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="18c07-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="18c07-126">Asegúrese de utilizar los datos pero aplicables a su escenario de aplicación.</span><span class="sxs-lookup"><span data-stu-id="18c07-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="18c07-127">En nuestro ejemplo de código, cambiamos el color del cubo girando holograma según el comando del usuario.</span><span class="sxs-lookup"><span data-stu-id="18c07-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="18c07-128">Desde *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="18c07-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="18c07-129">Use el dictado para el reconocimiento de voz y de las frases Monoestable</span><span class="sxs-lookup"><span data-stu-id="18c07-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="18c07-130">Puede configurar un reconocedor de voz para realizar escuchas para las frases u oraciones habladas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="18c07-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="18c07-131">En este caso, aplicamos un SpeechRecognitionTopicConstraint que indica que el reconocedor de voz a qué tipo de entrada que puede esperar.</span><span class="sxs-lookup"><span data-stu-id="18c07-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="18c07-132">El flujo de trabajo de aplicación es como sigue, para este tipo de caso de uso:</span><span class="sxs-lookup"><span data-stu-id="18c07-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="18c07-133">La aplicación crea SpeechRecognizer, proporciona indicaciones de la interfaz de usuario y empieza a escuchar para que un comando que se hablará inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="18c07-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="18c07-134">El usuario pronuncia una palabra o frase.</span><span class="sxs-lookup"><span data-stu-id="18c07-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="18c07-135">Se realiza el reconocimiento de voz del usuario, y se devuelve un resultado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="18c07-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="18c07-136">En este momento, la aplicación debe proporcionar un símbolo del sistema de la interfaz de usuario que indica que se ha producido el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="18c07-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="18c07-137">Según el nivel de confianza que desea responder a y el nivel de confianza del resultado de reconocimiento de voz, la aplicación puede procesar el resultado y responder según corresponda.</span><span class="sxs-lookup"><span data-stu-id="18c07-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="18c07-138">En esta sección se describe cómo crear un SpeechRecognizer, compile la restricción y escuchar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="18c07-139">El siguiente código compila la restricción de tema, que en este caso, está optimizada para la búsqueda Web.</span><span class="sxs-lookup"><span data-stu-id="18c07-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="18c07-140">Si la compilación se realiza correctamente, podemos continuar con el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="18c07-141">A continuación, se devuelve el resultado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="18c07-141">The result is then returned to the app.</span></span> <span data-ttu-id="18c07-142">Si estamos bastante seguros en el resultado, se puede procesar el comando.</span><span class="sxs-lookup"><span data-stu-id="18c07-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="18c07-143">Este ejemplo de código procesa los resultados con confianza menos en medio.</span><span class="sxs-lookup"><span data-stu-id="18c07-143">This code example processes results with at least Medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="18c07-144">Siempre que use el reconocimiento de voz, debe supervisar para las excepciones que podrían indicar que el usuario ha desactivado el micrófono en la configuración de privacidad del sistema.</span><span class="sxs-lookup"><span data-stu-id="18c07-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="18c07-145">Esto puede ocurrir durante la inicialización o durante el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="18c07-145">This can happen during initialization, or during recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

<span data-ttu-id="18c07-146">**NOTA:** Hay varios predefinidos [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponibles para optimizar el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="18c07-147">Si desea optimizar el dictado, use el escenario del dictado:</span><span class="sxs-lookup"><span data-stu-id="18c07-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="18c07-148">Cuando usa la voz para realizar una búsqueda Web, puede usar una restricción de escenario Web específicos como sigue:</span><span class="sxs-lookup"><span data-stu-id="18c07-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="18c07-149">Utilice la restricción de formulario para rellenar los formularios.</span><span class="sxs-lookup"><span data-stu-id="18c07-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="18c07-150">En este caso, es mejor aplicar su propia gramática que está optimizado para rellenar el formulario.</span><span class="sxs-lookup"><span data-stu-id="18c07-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="18c07-151">Puede proporcionar su propia gramática con el formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="18c07-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="18c07-152">Use el dictado de voz continua, de forma libre</span><span class="sxs-lookup"><span data-stu-id="18c07-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="18c07-153">Vea el ejemplo de código de voz de Windows 10 UWP para el escenario del dictado continuo [aquí.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="18c07-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="18c07-154">Controlar la degradación de la calidad</span><span class="sxs-lookup"><span data-stu-id="18c07-154">Handle degradation in quality</span></span>

<span data-ttu-id="18c07-155">Las condiciones del entorno a veces pueden impedir que el reconocimiento de voz de trabajo.</span><span class="sxs-lookup"><span data-stu-id="18c07-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="18c07-156">Por ejemplo, la sala podría ser produce demasiado ruidosa o el usuario podría comunicar en un volumen demasiado alto.</span><span class="sxs-lookup"><span data-stu-id="18c07-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="18c07-157">El reconocimiento de voz API proporciona información, siempre que sea posible, acerca de las condiciones que han causado una degradación en calidad.</span><span class="sxs-lookup"><span data-stu-id="18c07-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="18c07-158">Esta información se envía a la aplicación con un evento de WinRT.</span><span class="sxs-lookup"><span data-stu-id="18c07-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="18c07-159">Este es un ejemplo de cómo suscribirse a este evento.</span><span class="sxs-lookup"><span data-stu-id="18c07-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="18c07-160">En nuestro ejemplo de código, hemos elegido escribir la información de las condiciones en la consola de depuración.</span><span class="sxs-lookup"><span data-stu-id="18c07-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="18c07-161">Una aplicación podría ser aconsejable proporcionar comentarios al usuario a través de la interfaz de usuario y síntesis de voz, o que necesite para comportarse de manera diferente cuando se interrumpe la voz con una reducción temporal en la calidad.</span><span class="sxs-lookup"><span data-stu-id="18c07-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="18c07-162">Si no utiliza las clases ref para crear su aplicación de DirectX, debe cancelar la suscripción desde el evento antes de liberar o volver a crear el reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="18c07-163">El HolographicSpeechPromptSample tiene una rutina para detener el reconocimiento y cancelar la suscripción a eventos de este modo:</span><span class="sxs-lookup"><span data-stu-id="18c07-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="18c07-164">Uso de síntesis de voz para proporcionar indicaciones sonoras de voz</span><span class="sxs-lookup"><span data-stu-id="18c07-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="18c07-165">Los ejemplos de voz holográfica utilizan síntesis de voz para proporcionar instrucciones audibles al usuario.</span><span class="sxs-lookup"><span data-stu-id="18c07-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="18c07-166">En este tema le guía a través del proceso de creación de una muestra de voz sintetizada y reproducirlo mediante las API de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="18c07-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="18c07-167">Debe proporcionar que su propia voz pide al solicitar la entrada de la frase.</span><span class="sxs-lookup"><span data-stu-id="18c07-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="18c07-168">Esto también puede ser útil para indicar cuando se pueden hablar comandos de voz, para un escenario de reconocimiento continua.</span><span class="sxs-lookup"><span data-stu-id="18c07-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="18c07-169">Este es un ejemplo de cómo hacerlo con un sintetizador de voz; Tenga en cuenta que también podría usar un mensaje de voz pregrabados, una interfaz de usuario visual u otro indicador de lo que dicen, por ejemplo, en escenarios donde el símbolo del sistema no es dinámico.</span><span class="sxs-lookup"><span data-stu-id="18c07-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="18c07-170">En primer lugar, cree el objeto SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="18c07-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="18c07-171">También necesita una cadena con el texto para sintetizarlo:</span><span class="sxs-lookup"><span data-stu-id="18c07-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="18c07-172">Voz se sintetiza asincrónicamente mediante SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="18c07-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="18c07-173">En este caso, se ponga en marcha una tarea asincrónica para la síntesis de voz.</span><span class="sxs-lookup"><span data-stu-id="18c07-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="18c07-174">La síntesis de voz se envía como una secuencia de bytes.</span><span class="sxs-lookup"><span data-stu-id="18c07-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="18c07-175">Se puede inicializar una voz XAudio2 a través de esa secuencia de bytes; para nuestros ejemplos de código holográfica, nos reproducirlo como un efecto de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="18c07-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="18c07-176">Como con reconocimiento de voz de síntesis de voz producirá una excepción si algo va mal.</span><span class="sxs-lookup"><span data-stu-id="18c07-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="18c07-177">Vea también</span><span class="sxs-lookup"><span data-stu-id="18c07-177">See also</span></span>
* [<span data-ttu-id="18c07-178">Diseño de aplicaciones de voz</span><span class="sxs-lookup"><span data-stu-id="18c07-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="18c07-179">Sonido espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="18c07-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="18c07-180">Ejemplo de SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="18c07-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
