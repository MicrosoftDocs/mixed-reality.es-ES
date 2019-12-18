---
title: Entrada de voz en DirectX
description: Explica cómo implementar comandos de voz y el reconocimiento de frases y frases pequeñas en una aplicación DirectX para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: tutorial, comando de voz, frase, reconocimiento, voz, DirectX, plataforma, Cortana, Windows Mixed Reality
ms.openlocfilehash: c0a7ca85c24147e607603e733c9d191c64cbd927
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181825"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="c8c9a-104">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="c8c9a-104">Voice input in DirectX</span></span>

<span data-ttu-id="c8c9a-105">En este artículo se explica cómo implementar [comandos de voz](voice-input.md) más pequeñas frases y el reconocimiento de oraciones en una aplicación DirectX para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-105">This article explains how to implement [voice commands](voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="c8c9a-106">En los fragmentos de código de este artículo C++se usa/CX en lugar de C + C+++17 compatible con/WinRT, que se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="c8c9a-106">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c8c9a-107">Los conceptos son equivalentes para C++un proyecto de/WinRT, pero debe traducir el código.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-107">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="c8c9a-108">Usar SpeechRecognizer para el reconocimiento de voz continuo</span><span class="sxs-lookup"><span data-stu-id="c8c9a-108">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="c8c9a-109">En esta sección se describe cómo usar el reconocimiento de voz continuo para habilitar comandos de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-109">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="c8c9a-110">En este tutorial se usa el código del ejemplo [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="c8c9a-110">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="c8c9a-111">Cuando se esté ejecutando el ejemplo, hable el nombre de uno de los comandos de color registrados para cambiar el color del cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="c8c9a-112">En primer lugar, cree una nueva instancia de *Windows:: media:: SpeechRecognition:: SpeechRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="c8c9a-112">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="c8c9a-113">Desde *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="c8c9a-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="c8c9a-114">Cree una lista de comandos de voz para que el reconocedor realice escuchas.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-114">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="c8c9a-115">En este caso, se crea un conjunto de comandos para cambiar el color de un holograma.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="c8c9a-116">Por comodidad, también creamos los datos que usaremos para los comandos más adelante.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-116">For convenience, we also create the data that we'll use for the commands later.</span></span>

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

<span data-ttu-id="c8c9a-117">Puede usar palabras fonéticas que podrían no estar en un diccionario para especificar comandos.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-117">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="c8c9a-118">Para cargar la lista de comandos en la lista de restricciones del reconocedor de voz, use un objeto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="c8c9a-118">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="c8c9a-119">Suscríbase al evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) en el [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-119">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="c8c9a-120">Este evento notifica a la aplicación cuando se ha reconocido uno de sus comandos.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-120">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="c8c9a-121">El controlador de eventos *OnResultGenerated* recibe datos de evento en una instancia de [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="c8c9a-121">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="c8c9a-122">Si la confianza es mayor que el umbral definido, la aplicación debe tener en cuenta que se produjo el evento.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-122">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="c8c9a-123">Guarde los datos del evento para poder usarlos en un bucle de actualización posterior.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-123">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="c8c9a-124">Desde *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="c8c9a-124">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="c8c9a-125">En el código de ejemplo, se cambia el color del cubo de hologramas hilados según el comando del usuario.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-125">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="c8c9a-126">Desde *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="c8c9a-126">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-one-shot-recognition"></a><span data-ttu-id="c8c9a-127">Usar reconocimiento de "One-Shot"</span><span class="sxs-lookup"><span data-stu-id="c8c9a-127">Use "one-shot" recognition</span></span>

<span data-ttu-id="c8c9a-128">Puede configurar un reconocedor de voz para que escuche frases o oraciones que el usuario habla.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-128">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="c8c9a-129">En este caso, se aplica un *SpeechRecognitionTopicConstraint* que indica al reconocedor de voz qué tipo de entrada se espera.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-129">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="c8c9a-130">Este es un flujo de trabajo de aplicación para este escenario:</span><span class="sxs-lookup"><span data-stu-id="c8c9a-130">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="c8c9a-131">La aplicación crea el SpeechRecognizer, proporciona solicitudes de la interfaz de usuario e inicia la escucha de un comando hablado.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-131">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="c8c9a-132">El usuario habla una frase o frase.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-132">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="c8c9a-133">Se produce el reconocimiento de la voz del usuario y se devuelve un resultado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-133">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="c8c9a-134">En este momento, la aplicación debe proporcionar un indicador de la interfaz de usuario para indicar que se ha producido el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-134">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="c8c9a-135">Según el nivel de confianza al que desee responder y el nivel de confianza del resultado del reconocimiento de voz, la aplicación puede procesar el resultado y responder según corresponda.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-135">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="c8c9a-136">En esta sección se describe cómo crear un SpeechRecognizer, compilar la restricción y escuchar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-136">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="c8c9a-137">El código siguiente compila la restricción de tema, que en este caso está optimizada para la búsqueda web.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-137">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="c8c9a-138">Si la compilación se realiza correctamente, podemos continuar con el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-138">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="c8c9a-139">A continuación, el resultado se devuelve a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-139">The result is then returned to the app.</span></span> <span data-ttu-id="c8c9a-140">Si el resultado es lo suficientemente seguro, podemos procesar el comando.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-140">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="c8c9a-141">En este ejemplo de código se procesan los resultados con una confianza al menos mediana.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-141">This code example processes results with at least medium confidence.</span></span>

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

<span data-ttu-id="c8c9a-142">Siempre que use el reconocimiento de voz, vea las excepciones que podrían indicar que el usuario ha desactivado el micrófono en la configuración de privacidad del sistema.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-142">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="c8c9a-143">Esto puede ocurrir durante la inicialización o el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-143">This can happen during initialization or recognition.</span></span>

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

> [!NOTE]
> <span data-ttu-id="c8c9a-144">Hay varios [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefinidos que puede usar para optimizar el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-144">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="c8c9a-145">Para optimizar el dictado, use el escenario de dictado.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-145">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="c8c9a-146">En el caso de las búsquedas Web de voz, use la siguiente restricción de escenario específica de la Web.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-146">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="c8c9a-147">Use la restricción de formulario para rellenar los formularios.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-147">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="c8c9a-148">En este caso, es mejor aplicar su propia gramática que esté optimizada para rellenar el formulario.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-148">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="c8c9a-149">Puede proporcionar su propia gramática en el formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-149">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="c8c9a-150">Usar reconocimiento continuo</span><span class="sxs-lookup"><span data-stu-id="c8c9a-150">Use continuous recognition</span></span>

<span data-ttu-id="c8c9a-151">Para ver el escenario de dictado continuo, consulte el [ejemplo de código de voz de UWP de Windows 10](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="c8c9a-151">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="c8c9a-152">Controlar la degradación de la calidad</span><span class="sxs-lookup"><span data-stu-id="c8c9a-152">Handle quality degradation</span></span>

<span data-ttu-id="c8c9a-153">A veces, las condiciones del entorno interfieren con el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-153">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="c8c9a-154">Por ejemplo, el salón podría ser demasiado ruidoso o el usuario podría hablar demasiado alto.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-154">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="c8c9a-155">Siempre que sea posible, la API de reconocimiento de voz proporciona información acerca de las condiciones que causaron la degradación de la calidad.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-155">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="c8c9a-156">Esta información se inserta en la aplicación a través de un evento de WinRT.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-156">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="c8c9a-157">En el ejemplo siguiente se muestra cómo suscribirse a este evento.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-157">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="c8c9a-158">En nuestro ejemplo de código, escribimos la información de las condiciones en la consola de depuración.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-158">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="c8c9a-159">Una aplicación podría querer proporcionar comentarios al usuario a través de la interfaz de usuario, la síntesis de voz y otro método.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-159">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="c8c9a-160">O bien, puede que tenga que comportarse de forma diferente cuando la voz se interrumpa por una reducción temporal de la calidad.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-160">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="c8c9a-161">Si no usa clases Ref para crear la aplicación DirectX, debe cancelar la suscripción al evento antes de liberar o volver a crear el reconocedor de voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-161">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="c8c9a-162">HolographicSpeechPromptSample tiene una rutina para detener el reconocimiento y cancelar la suscripción a los eventos.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-162">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="c8c9a-163">Usar síntesis de voz para proporcionar mensajes sonoros</span><span class="sxs-lookup"><span data-stu-id="c8c9a-163">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="c8c9a-164">Los ejemplos de voz holográfica usan síntesis de voz para proporcionar instrucciones auditivas al usuario.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-164">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="c8c9a-165">En esta sección se muestra cómo crear una muestra de voz sintetizada y reproducirla a través de las API de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-165">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="c8c9a-166">Debe proporcionar sus propios mensajes de voz al solicitar la entrada de frases.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-166">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="c8c9a-167">Los mensajes también pueden ayudar a indicar cuándo se pueden hablar comandos de voz para un escenario de reconocimiento continuo.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-167">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="c8c9a-168">En el ejemplo siguiente se muestra cómo usar un sintetizador de voz para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-168">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="c8c9a-169">También puede usar un clip de voz grabado previamente, una interfaz de usuario visual u otro indicador de lo que debe decir, por ejemplo, en escenarios en los que el aviso no es dinámico.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-169">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="c8c9a-170">En primer lugar, cree el objeto SpeechSynthesizer.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-170">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="c8c9a-171">También necesita una cadena que incluya el texto que se va a sintetizar.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-171">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="c8c9a-172">La voz se sintetiza de forma asincrónica a través de SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-172">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="c8c9a-173">Aquí iniciamos una tarea asincrónica para sintetizar la voz.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-173">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="c8c9a-174">La síntesis de voz se envía como un flujo de bytes.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="c8c9a-175">Podemos usar esa secuencia de bytes para inicializar una voz de XAudio2.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-175">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="c8c9a-176">Para nuestros ejemplos de código Holographic, lo reproducimos como un efecto de audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-176">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="c8c9a-177">Al igual que con el reconocimiento de voz, la síntesis de voz produce una excepción si algo va mal.</span><span class="sxs-lookup"><span data-stu-id="c8c9a-177">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8c9a-178">Consulta también</span><span class="sxs-lookup"><span data-stu-id="c8c9a-178">See also</span></span>
* [<span data-ttu-id="c8c9a-179">Diseño de aplicaciones de voz</span><span class="sxs-lookup"><span data-stu-id="c8c9a-179">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="c8c9a-180">Ejemplo de SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="c8c9a-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
