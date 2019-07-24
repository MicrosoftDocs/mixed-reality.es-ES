---
title: Entrada de voz en DirectX
description: Explica cómo implementar comandos de voz y el reconocimiento de frases y frases pequeñas en una aplicación DirectX para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: tutorial, comando de voz, frase, reconocimiento, voz, DirectX, plataforma, Cortana, Windows Mixed Reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548666"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="2a277-104">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="2a277-104">Voice input in DirectX</span></span>

<span data-ttu-id="2a277-105">En este tema se explica cómo implementar [comandos de voz](voice-input.md)y el reconocimiento de frases y frases pequeñas en una aplicación de DirectX para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2a277-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="2a277-106">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="2a277-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="2a277-107">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="2a277-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="2a277-108">Usar un SpeechRecognizer para el reconocimiento continuo de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="2a277-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="2a277-109">En esta sección, se describe cómo usar el reconocimiento de voz continuo para habilitar comandos de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2a277-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="2a277-110">En este tutorial se usa el código del ejemplo [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="2a277-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="2a277-111">Cuando se esté ejecutando el ejemplo, hable el nombre de uno de los comandos de color registrados para cambiar el color del cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="2a277-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="2a277-112">En primer lugar, cree una nueva instancia de **Windows:: media:: SpeechRecognition:: SpeechRecognizer** .</span><span class="sxs-lookup"><span data-stu-id="2a277-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="2a277-113">Desde *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="2a277-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="2a277-114">Deberá crear una lista de comandos de voz para que el reconocedor realice escuchas.</span><span class="sxs-lookup"><span data-stu-id="2a277-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="2a277-115">En este caso, se crea un conjunto de comandos para cambiar el color de un holograma.</span><span class="sxs-lookup"><span data-stu-id="2a277-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="2a277-116">Por comodidad, también creamos los datos que usaremos para los comandos más adelante.</span><span class="sxs-lookup"><span data-stu-id="2a277-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="2a277-117">Los comandos se pueden especificar usando palabras fonéticas que podrían no estar en un diccionario:</span><span class="sxs-lookup"><span data-stu-id="2a277-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="2a277-118">La lista de comandos se carga en la lista de restricciones para el reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="2a277-119">Esto se hace mediante el uso de un objeto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="2a277-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="2a277-120">Suscríbase al evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) en el [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="2a277-121">Este evento notifica a la aplicación cuando se ha reconocido uno de sus comandos.</span><span class="sxs-lookup"><span data-stu-id="2a277-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="2a277-122">El controlador de eventos **OnResultGenerated** recibe datos de evento en una instancia de [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="2a277-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="2a277-123">Si la confianza es mayor que el umbral definido, la aplicación debe tener en cuenta que se produjo el evento.</span><span class="sxs-lookup"><span data-stu-id="2a277-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="2a277-124">Guarde los datos del evento para poder usarlos en un bucle de actualización posterior.</span><span class="sxs-lookup"><span data-stu-id="2a277-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="2a277-125">Desde *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="2a277-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="2a277-126">Haga uso de los datos de la forma aplicable al escenario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2a277-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="2a277-127">En el código de ejemplo, se cambia el color del cubo de hologramas hilados según el comando del usuario.</span><span class="sxs-lookup"><span data-stu-id="2a277-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="2a277-128">Desde *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="2a277-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="2a277-129">Usar dictado para el reconocimiento de una sola toma de frases y oraciones de voz</span><span class="sxs-lookup"><span data-stu-id="2a277-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="2a277-130">Puede configurar un reconocedor de voz para que escuche frases o oraciones pronunciadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="2a277-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="2a277-131">En este caso, se aplica un SpeechRecognitionTopicConstraint que indica al reconocedor de voz qué tipo de entrada se espera.</span><span class="sxs-lookup"><span data-stu-id="2a277-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="2a277-132">El flujo de trabajo de la aplicación es el siguiente, para este tipo de caso de uso:</span><span class="sxs-lookup"><span data-stu-id="2a277-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="2a277-133">La aplicación crea el SpeechRecognizer, proporciona solicitudes de la interfaz de usuario e inicia la escucha de un comando que se va a decir inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="2a277-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="2a277-134">El usuario habla una frase o frase.</span><span class="sxs-lookup"><span data-stu-id="2a277-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="2a277-135">Se realiza el reconocimiento de la voz del usuario y se devuelve un resultado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2a277-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="2a277-136">En este momento, la aplicación debe proporcionar un mensaje de la interfaz de usuario que indique que se ha producido el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="2a277-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="2a277-137">Según el nivel de confianza al que desee responder y el nivel de confianza del resultado del reconocimiento de voz, la aplicación puede procesar el resultado y responder según corresponda.</span><span class="sxs-lookup"><span data-stu-id="2a277-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="2a277-138">En esta sección se describe cómo crear un SpeechRecognizer, compilar la restricción y escuchar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="2a277-139">El código siguiente compila la restricción de tema, que en este caso está optimizada para la búsqueda web.</span><span class="sxs-lookup"><span data-stu-id="2a277-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="2a277-140">Si la compilación se realiza correctamente, podemos continuar con el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="2a277-141">A continuación, el resultado se devuelve a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2a277-141">The result is then returned to the app.</span></span> <span data-ttu-id="2a277-142">Si tenemos confianza suficiente en el resultado, podemos procesar el comando.</span><span class="sxs-lookup"><span data-stu-id="2a277-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="2a277-143">En este ejemplo de código se procesan los resultados con una confianza al menos mediana.</span><span class="sxs-lookup"><span data-stu-id="2a277-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="2a277-144">Siempre que use el reconocimiento de voz, debe ver las excepciones que podrían indicar que el usuario ha desactivado el micrófono en la configuración de privacidad del sistema.</span><span class="sxs-lookup"><span data-stu-id="2a277-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="2a277-145">Esto puede ocurrir durante la inicialización o durante el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="2a277-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="2a277-146">**NOTA:** Hay varios [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefinidos disponibles para optimizar el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="2a277-147">Si desea optimizar el dictado, use el escenario de dictado:</span><span class="sxs-lookup"><span data-stu-id="2a277-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="2a277-148">Al utilizar la voz para realizar una búsqueda web, puede usar una restricción de escenario específica de la web como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="2a277-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="2a277-149">Use la restricción de formulario para rellenar los formularios.</span><span class="sxs-lookup"><span data-stu-id="2a277-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="2a277-150">En este caso, es mejor aplicar su propia gramática que está optimizada para rellenar el formulario.</span><span class="sxs-lookup"><span data-stu-id="2a277-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="2a277-151">Puede proporcionar su propia gramática con el formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="2a277-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="2a277-152">Usar el dictado de voz continuo y de forma libre</span><span class="sxs-lookup"><span data-stu-id="2a277-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="2a277-153">Vea el ejemplo de código de voz de UWP de Windows 10 para el escenario de dictado continuo [aquí.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="2a277-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="2a277-154">Controlar la degradación de la calidad</span><span class="sxs-lookup"><span data-stu-id="2a277-154">Handle degradation in quality</span></span>

<span data-ttu-id="2a277-155">En ocasiones, las condiciones del entorno pueden impedir el funcionamiento del reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="2a277-156">Por ejemplo, el salón podría ser demasiado ruidoso o el usuario podría hablar de un volumen demasiado alto.</span><span class="sxs-lookup"><span data-stu-id="2a277-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="2a277-157">La API de reconocimiento de voz proporciona información, siempre que sea posible, sobre las condiciones que han provocado una degradación de la calidad.</span><span class="sxs-lookup"><span data-stu-id="2a277-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="2a277-158">Esta información se inserta en la aplicación mediante un evento de WinRT.</span><span class="sxs-lookup"><span data-stu-id="2a277-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="2a277-159">Este es un ejemplo de cómo suscribirse a este evento.</span><span class="sxs-lookup"><span data-stu-id="2a277-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="2a277-160">En nuestro ejemplo de código, optamos por escribir la información de las condiciones en la consola de depuración.</span><span class="sxs-lookup"><span data-stu-id="2a277-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="2a277-161">Una aplicación podría querer proporcionar comentarios al usuario a través de la interfaz de usuario, la síntesis de voz, etc., o puede que tenga que comportarse de forma diferente cuando la voz se interrumpa debido a una reducción temporal de la calidad.</span><span class="sxs-lookup"><span data-stu-id="2a277-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="2a277-162">Si no usa clases Ref para crear la aplicación DirectX, debe cancelar la suscripción al evento antes de liberar o volver a crear el reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="2a277-163">HolographicSpeechPromptSample tiene una rutina para detener el reconocimiento y cancelar la suscripción a eventos como este:</span><span class="sxs-lookup"><span data-stu-id="2a277-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="2a277-164">Usar síntesis de voz para proporcionar mensajes de voz sonoros</span><span class="sxs-lookup"><span data-stu-id="2a277-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="2a277-165">Los ejemplos de voz holográfica usan síntesis de voz para proporcionar instrucciones auditivas al usuario.</span><span class="sxs-lookup"><span data-stu-id="2a277-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="2a277-166">En este tema se describe el proceso de creación de una muestra de voz sintetizada y su reproducción con las API de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="2a277-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="2a277-167">Debe proporcionar sus propios mensajes de voz al solicitar la entrada de la frase.</span><span class="sxs-lookup"><span data-stu-id="2a277-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="2a277-168">Esto también puede ser útil para indicar cuándo se pueden hablar comandos de voz, para un escenario de reconocimiento continuo.</span><span class="sxs-lookup"><span data-stu-id="2a277-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="2a277-169">Este es un ejemplo de cómo hacerlo con un sintetizador de voz. Tenga en cuenta que también puede usar un clip de voz grabado previamente, una interfaz de usuario visual u otro indicador de lo que debe decir, por ejemplo, en escenarios en los que el aviso no es dinámico.</span><span class="sxs-lookup"><span data-stu-id="2a277-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="2a277-170">En primer lugar, cree el objeto SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="2a277-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="2a277-171">También necesita una cadena con el texto que se va a sintetizar:</span><span class="sxs-lookup"><span data-stu-id="2a277-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="2a277-172">La voz se sintetiza de forma asincrónica mediante SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="2a277-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="2a277-173">En este caso, iniciamos una tarea asincrónica para sintetizar la voz.</span><span class="sxs-lookup"><span data-stu-id="2a277-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="2a277-174">La síntesis de voz se envía como un flujo de bytes.</span><span class="sxs-lookup"><span data-stu-id="2a277-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="2a277-175">Podemos inicializar una voz de XAudio2 mediante ese flujo de bytes. para nuestros ejemplos de código Holographic, lo reproducimos como un efecto de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="2a277-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="2a277-176">Al igual que con el reconocimiento de voz, la síntesis de voz producirá una excepción si algo va mal.</span><span class="sxs-lookup"><span data-stu-id="2a277-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2a277-177">Vea también</span><span class="sxs-lookup"><span data-stu-id="2a277-177">See also</span></span>
* [<span data-ttu-id="2a277-178">Diseño de aplicaciones de voz</span><span class="sxs-lookup"><span data-stu-id="2a277-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="2a277-179">Sonido espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="2a277-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="2a277-180">Ejemplo de SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="2a277-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
