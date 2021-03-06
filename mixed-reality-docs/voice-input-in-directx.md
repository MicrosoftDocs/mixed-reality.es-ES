---
title: Entrada de voz en DirectX
description: Explica cómo implementar comandos de voz y el reconocimiento de frases y frases pequeñas en una aplicación DirectX para Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: tutorial, comando de voz, frase, reconocimiento, voz, DirectX, plataforma, Cortana, Windows Mixed Reality
ms.openlocfilehash: 2837a0fc42e8fdebb2e1facee118d20b5668cd43
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277973"
---
# <a name="voice-input-in-directx"></a>Entrada de voz en DirectX

En este artículo se explica cómo implementar [comandos de voz](voice-input.md) más pequeñas frases y el reconocimiento de oraciones en una aplicación DirectX para Windows Mixed Reality.

>[!NOTE]
>En los fragmentos de código de este artículo C++se usa/CX en lugar de C + C+++17 compatible con/WinRT, que se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, pero debe traducir el código.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Usar SpeechRecognizer para el reconocimiento de voz continuo

En esta sección se describe cómo usar el reconocimiento de voz continuo para habilitar comandos de voz en la aplicación. En este tutorial se usa el código del ejemplo [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) . Cuando se esté ejecutando el ejemplo, hable el nombre de uno de los comandos de color registrados para cambiar el color del cubo giratorio.

En primer lugar, cree una nueva instancia de *Windows:: media:: SpeechRecognition:: SpeechRecognizer* .

Desde *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Cree una lista de comandos de voz para que el reconocedor realice escuchas. En este caso, se crea un conjunto de comandos para cambiar el color de un holograma. Por comodidad, también creamos los datos que usaremos para los comandos más adelante.

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

Puede usar palabras fonéticas que podrían no estar en un diccionario para especificar comandos.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Para cargar la lista de comandos en la lista de restricciones del reconocedor de voz, use un objeto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .

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

Suscríbase al evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) en el [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del reconocedor de voz. Este evento notifica a la aplicación cuando se ha reconocido uno de sus comandos.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

El controlador de eventos *OnResultGenerated* recibe datos de evento en una instancia de [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Si la confianza es mayor que el umbral definido, la aplicación debe tener en cuenta que se produjo el evento. Guarde los datos del evento para poder usarlos en un bucle de actualización posterior.

Desde *HolographicVoiceInputSampleMain. cpp*:

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

En el código de ejemplo, se cambia el color del cubo de hologramas hilados según el comando del usuario.

Desde *HolographicVoiceInputSampleMain:: Update*:

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

## <a name="use-one-shot-recognition"></a>Usar reconocimiento de "One-Shot"

Puede configurar un reconocedor de voz para que escuche frases o oraciones que el usuario habla. En este caso, se aplica un *SpeechRecognitionTopicConstraint* que indica al reconocedor de voz qué tipo de entrada se espera. Este es un flujo de trabajo de aplicación para este escenario:
1. La aplicación crea el SpeechRecognizer, proporciona solicitudes de la interfaz de usuario e inicia la escucha de un comando hablado.
2. El usuario habla una frase o frase.
3. Se produce el reconocimiento de la voz del usuario y se devuelve un resultado a la aplicación. En este momento, la aplicación debe proporcionar un indicador de la interfaz de usuario para indicar que se ha producido el reconocimiento.
4. Según el nivel de confianza al que desee responder y el nivel de confianza del resultado del reconocimiento de voz, la aplicación puede procesar el resultado y responder según corresponda.

En esta sección se describe cómo crear un SpeechRecognizer, compilar la restricción y escuchar la entrada de voz.

El código siguiente compila la restricción de tema, que en este caso está optimizada para la búsqueda web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Si la compilación se realiza correctamente, podemos continuar con el reconocimiento de voz.

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

A continuación, el resultado se devuelve a la aplicación. Si el resultado es lo suficientemente seguro, podemos procesar el comando. En este ejemplo de código se procesan los resultados con una confianza al menos mediana.

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

Siempre que use el reconocimiento de voz, vea las excepciones que podrían indicar que el usuario ha desactivado el micrófono en la configuración de privacidad del sistema. Esto puede ocurrir durante la inicialización o el reconocimiento.

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
> Hay varios [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefinidos que puede usar para optimizar el reconocimiento de voz.

* Para optimizar el dictado, use el escenario de dictado.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* En el caso de las búsquedas Web de voz, use la siguiente restricción de escenario específica de la Web.

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* Use la restricción de formulario para rellenar los formularios. En este caso, es mejor aplicar su propia gramática que esté optimizada para rellenar el formulario.

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* Puede proporcionar su propia gramática en el formato SRGS.

## <a name="use-continuous-recognition"></a>Usar reconocimiento continuo

Para ver el escenario de dictado continuo, consulte el [ejemplo de código de voz de UWP de Windows 10](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).

## <a name="handle-quality-degradation"></a>Controlar la degradación de la calidad

A veces, las condiciones del entorno interfieren con el reconocimiento de voz. Por ejemplo, el salón podría ser demasiado ruidoso o el usuario podría hablar demasiado alto. Siempre que sea posible, la API de reconocimiento de voz proporciona información acerca de las condiciones que causaron la degradación de la calidad. Esta información se inserta en la aplicación a través de un evento de WinRT. En el ejemplo siguiente se muestra cómo suscribirse a este evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

En nuestro ejemplo de código, escribimos la información de las condiciones en la consola de depuración. Una aplicación podría querer proporcionar comentarios al usuario a través de la interfaz de usuario, la síntesis de voz y otro método. O bien, puede que tenga que comportarse de forma diferente cuando la voz se interrumpa por una reducción temporal de la calidad.

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

Si no usa clases Ref para crear la aplicación DirectX, debe cancelar la suscripción al evento antes de liberar o volver a crear el reconocedor de voz. HolographicSpeechPromptSample tiene una rutina para detener el reconocimiento y cancelar la suscripción a los eventos.

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Usar síntesis de voz para proporcionar mensajes sonoros

Los ejemplos de voz holográfica usan síntesis de voz para proporcionar instrucciones auditivas al usuario. En esta sección se muestra cómo crear una muestra de voz sintetizada y reproducirla a través de las API de audio HRTF.

Debe proporcionar sus propios mensajes de voz al solicitar la entrada de frases. Los mensajes también pueden ayudar a indicar cuándo se pueden hablar comandos de voz para un escenario de reconocimiento continuo. En el ejemplo siguiente se muestra cómo usar un sintetizador de voz para hacerlo. También puede usar un clip de voz grabado previamente, una interfaz de usuario visual u otro indicador de lo que debe decir, por ejemplo, en escenarios en los que el aviso no es dinámico.

En primer lugar, cree el objeto SpeechSynthesizer.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

También necesita una cadena que incluya el texto que se va a sintetizar.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

La voz se sintetiza de forma asincrónica a través de SynthesizeTextToStreamAsync. Aquí iniciamos una tarea asincrónica para sintetizar la voz.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

La síntesis de voz se envía como un flujo de bytes. Podemos usar esa secuencia de bytes para inicializar una voz de XAudio2. Para nuestros ejemplos de código Holographic, lo reproducimos como un efecto de audio HRTF.

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

Al igual que con el reconocimiento de voz, la síntesis de voz produce una excepción si algo va mal.

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

## <a name="see-also"></a>Vea también
* [Diseño de aplicaciones de voz](https://msdn.microsoft.com/library/dn596121.aspx)
* [Ejemplo de SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
