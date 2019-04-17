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
# <a name="voice-input-in-directx"></a>Entrada de voz en DirectX

En este tema se explica cómo implementar [comandos de voz](voice-input.md)y el reconocimiento de frases y oraciones pequeño en una aplicación de DirectX para Windows Mixed Reality.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Usar un SpeechRecognizer para el reconocimiento de continua de los comandos de voz

En esta sección, se describe cómo usar el reconocimiento de voz continua para habilitar los comandos de voz en la aplicación. Este tutorial usa código desde el [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) ejemplo. Cuando se ejecuta el ejemplo, diga el nombre de uno de los comandos registrados de color para cambiar el color del cubo giratorio.

En primer lugar, cree un nuevo **Windows::Media::SpeechRecognition::SpeechRecognizer** instancia.

Desde *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Deberá crear una lista de comandos de voz para el reconocedor escuchar. En este caso, creamos un conjunto de comandos para cambiar el color de un holograma. Por motivos de comodidad, también creamos los datos que vamos a usar para los comandos más adelante.

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

Los comandos se pueden especificar mediante fonéticas palabras que no esté en un diccionario:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

La lista de comandos se carga en la lista de restricciones para el reconocimiento de voz. Esto se realiza mediante un [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) objeto.

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

Suscribirse a la [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) eventos en el reconocimiento de voz [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx). Este evento notifica a la aplicación cuando uno de los comandos se le ha reconocido.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Su **OnResultGenerated** controlador de eventos recibe datos de evento en un [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instancia. Si es mayor que el umbral que se ha definido la confianza, la aplicación debe tener en cuenta que se produjo el evento. Guardar los datos del evento para que puede hacer uso de ella en un bucle de actualización posterior.

Desde *HolographicVoiceInputSampleMain.cpp*:

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

Asegúrese de utilizar los datos pero aplicables a su escenario de aplicación. En nuestro ejemplo de código, cambiamos el color del cubo girando holograma según el comando del usuario.

Desde *HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Use el dictado para el reconocimiento de voz y de las frases Monoestable

Puede configurar un reconocedor de voz para realizar escuchas para las frases u oraciones habladas por el usuario. En este caso, aplicamos un SpeechRecognitionTopicConstraint que indica que el reconocedor de voz a qué tipo de entrada que puede esperar. El flujo de trabajo de aplicación es como sigue, para este tipo de caso de uso:
1. La aplicación crea SpeechRecognizer, proporciona indicaciones de la interfaz de usuario y empieza a escuchar para que un comando que se hablará inmediatamente.
2. El usuario pronuncia una palabra o frase.
3. Se realiza el reconocimiento de voz del usuario, y se devuelve un resultado a la aplicación. En este momento, la aplicación debe proporcionar un símbolo del sistema de la interfaz de usuario que indica que se ha producido el reconocimiento.
4. Según el nivel de confianza que desea responder a y el nivel de confianza del resultado de reconocimiento de voz, la aplicación puede procesar el resultado y responder según corresponda.

En esta sección se describe cómo crear un SpeechRecognizer, compile la restricción y escuchar la entrada de voz.

El siguiente código compila la restricción de tema, que en este caso, está optimizada para la búsqueda Web.

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

A continuación, se devuelve el resultado a la aplicación. Si estamos bastante seguros en el resultado, se puede procesar el comando. Este ejemplo de código procesa los resultados con confianza menos en medio.

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

Siempre que use el reconocimiento de voz, debe supervisar para las excepciones que podrían indicar que el usuario ha desactivado el micrófono en la configuración de privacidad del sistema. Esto puede ocurrir durante la inicialización o durante el reconocimiento.

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

**NOTA:** Hay varios predefinidos [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponibles para optimizar el reconocimiento de voz.
* Si desea optimizar el dictado, use el escenario del dictado:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Cuando usa la voz para realizar una búsqueda Web, puede usar una restricción de escenario Web específicos como sigue:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Utilice la restricción de formulario para rellenar los formularios. En este caso, es mejor aplicar su propia gramática que está optimizado para rellenar el formulario.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Puede proporcionar su propia gramática con el formato SRGS.

## <a name="use-continuous-freeform-speech-dictation"></a>Use el dictado de voz continua, de forma libre

Vea el ejemplo de código de voz de Windows 10 UWP para el escenario del dictado continuo [aquí.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Controlar la degradación de la calidad

Las condiciones del entorno a veces pueden impedir que el reconocimiento de voz de trabajo. Por ejemplo, la sala podría ser produce demasiado ruidosa o el usuario podría comunicar en un volumen demasiado alto. El reconocimiento de voz API proporciona información, siempre que sea posible, acerca de las condiciones que han causado una degradación en calidad.

Esta información se envía a la aplicación con un evento de WinRT. Este es un ejemplo de cómo suscribirse a este evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

En nuestro ejemplo de código, hemos elegido escribir la información de las condiciones en la consola de depuración. Una aplicación podría ser aconsejable proporcionar comentarios al usuario a través de la interfaz de usuario y síntesis de voz, o que necesite para comportarse de manera diferente cuando se interrumpe la voz con una reducción temporal en la calidad.

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

Si no utiliza las clases ref para crear su aplicación de DirectX, debe cancelar la suscripción desde el evento antes de liberar o volver a crear el reconocedor de voz. El HolographicSpeechPromptSample tiene una rutina para detener el reconocimiento y cancelar la suscripción a eventos de este modo:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Uso de síntesis de voz para proporcionar indicaciones sonoras de voz

Los ejemplos de voz holográfica utilizan síntesis de voz para proporcionar instrucciones audibles al usuario. En este tema le guía a través del proceso de creación de una muestra de voz sintetizada y reproducirlo mediante las API de audio HRTF.

Debe proporcionar que su propia voz pide al solicitar la entrada de la frase. Esto también puede ser útil para indicar cuando se pueden hablar comandos de voz, para un escenario de reconocimiento continua. Este es un ejemplo de cómo hacerlo con un sintetizador de voz; Tenga en cuenta que también podría usar un mensaje de voz pregrabados, una interfaz de usuario visual u otro indicador de lo que dicen, por ejemplo, en escenarios donde el símbolo del sistema no es dinámico.

En primer lugar, cree el objeto SpeechSynthesizer:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

También necesita una cadena con el texto para sintetizarlo:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Voz se sintetiza asincrónicamente mediante SynthesizeTextToStreamAsync. En este caso, se ponga en marcha una tarea asincrónica para la síntesis de voz.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

La síntesis de voz se envía como una secuencia de bytes. Se puede inicializar una voz XAudio2 a través de esa secuencia de bytes; para nuestros ejemplos de código holográfica, nos reproducirlo como un efecto de audio HRTF.

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

Como con reconocimiento de voz de síntesis de voz producirá una excepción si algo va mal.

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
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Ejemplo de SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
