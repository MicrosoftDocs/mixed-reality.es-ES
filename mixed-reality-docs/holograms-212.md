---
title: Entrada MR 212 - voz
description: Siga este tutorial de programación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial de voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598927"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-input-212-voice"></a>Entrada MR 212: Voz

[Entrada de voz](voice-input.md) nos proporciona otra manera de interactuar con nuestra hologramas. Los comandos de voz funcionan de manera muy fácil y natural. Diseñar los comandos de voz para que sean:

* Natural
* Fácil de recordar
* Contexto adecuado
* Suficientemente distintos de otras opciones en el mismo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

En [MR Fundamentos 101](holograms-101.md), hemos usado el KeywordRecognizer para generar dos comandos de voz simple. En MR 212 de entrada, crearemos profundizar más y obtenga información sobre cómo:

* Comandos de voz de diseño que están optimizados para el motor de voz de HoloLens.
* Hacer que al usuario sea consciente de voz en qué comandos están disponibles.
* Confirmar que hemos oído comandos de voz del usuario.
* Comprenda qué es el usuario que indica que, mediante un módulo de reconocimiento de dictado.
* Utilice un reconocedor de gramática para escuchar comandos basados en un archivo de SRGS o especificación de gramática de reconocimiento de voz.

En este curso, volveremos a Explorador de modelos, que se basa en [MR entrada 210](holograms-210.md) y [MR entrada 211](holograms-211.md).

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Entrada MR 212: Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Básica C# capacidad de programación.
* Debe haber completado [MR Fundamentos 101](holograms-101.md).
* Debe haber completado [MR entrada 210](holograms-210.md).
* Debe haber completado [MR entrada 211](holograms-211.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.

## <a name="unity-setup"></a>Programa de instalación de Unity

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **abierto**.
3. Navegue hasta la **HolographicAcademy hologramas 212 voz** carpeta que anteriormente no archivados.
4. Busque y seleccione el **iniciando**/**el Explorador de modelos** carpeta.
5. Haga clic en el **Seleccionar carpeta** botón.
6. En el **proyecto** del panel, expanda el **escenas** carpeta.
7. Haga doble clic en **ModelExplorer** escena para cargarlo en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Si **escenas/ModelExplorer** no aparece en **escenas en compilación**, haga clic en **agregar escenas abierto** para agregar la escena.
3. Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**. En caso contrario, déjelo en **cualquier dispositivo**.
4. Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).
5. Haz clic en **Compilación**.
6. Crear un **nueva carpeta** denominada "Aplicación".
7. Solo haga clic en el **aplicación** carpeta.
8. Presione **seleccionar la carpeta** y Unity empezará a compilar el proyecto de Visual Studio.

Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.

1. Abra el **aplicación** carpeta.
2. Abra el **ModelExplorer Visual Studio solución**.

Si la implementación en HoloLens:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.
2. Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.
3. Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**. Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.

Si la implementación en un auricular envolvente:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.
2. Asegúrese de que el destino de implementación se establece en **máquina Local**.
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
4. Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojo en el panel de errores de Visual Studio. Es seguro pasarlos por alto. Progreso de la compilación conmutador al panel de salida para ver los costes reales. Errores en el panel de salida, deberá realizar una corrección (la mayoría suelen deberse a un error en una secuencia de comandos).

## <a name="chapter-1---awareness"></a>Capítulo 1 - reconocimiento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre la **consejos** de diseño de comandos de voz.
* Use **KeywordRecognizer** para agregar los comandos de voz en función de mirada.
* Informar a los usuarios de comandos de voz con cursor **comentarios**.

### <a name="voice-command-design"></a>Diseño de comandos de voz

En este capítulo, aprenderá sobre el diseño de los comandos de voz. Al crear los comandos de voz:

#### <a name="do"></a>DO

* Crear comandos concisos. No quiere usar *"Reproducir el vídeo seleccionado"*, ya que ese comando no es conciso y olvidan fácilmente por el usuario. En su lugar, debe usar: *"Reproducir vídeo"*, porque es conciso y tiene varios sílabas.
* Usar un vocabulario simple. Siempre intenta utilizar palabras y frases que resultan fáciles para el usuario detectar y recuerde comunes. Por ejemplo, si la aplicación tiene un objeto de la nota que se podría mostrar u ocultar de la vista, no utilizaría el comando *"Mostrar panel"*, ya que "panel" es un término usado con poca frecuencia. En su lugar, usaría el comando: *"Mostrar nota"*, para mostrar la nota de la aplicación.
* Ser coherente. Los comandos de voz se deben mantener coherentes en toda la aplicación. Imagine que tiene dos escenas en la aplicación y ambos escenas contienen un botón para cerrar la aplicación. Si la primera escena usa el comando *"Exit"* para desencadenar el botón, pero la segunda escena usara el comando *"Cerrar aplicación"*, a continuación, el usuario será bastante confundido. Si la misma funcionalidad que se conserva entre varias escenas, debe usarse el mismo comando de voz para activarlo.

#### <a name="dont"></a>NO

* Use los comandos Sílaba único. Por ejemplo, si está creando un comando de voz para reproducir un vídeo, debe evitar usar el comando simple *"Reproducir"*, tal y como es solo un único Sílaba y podrían perderse fácilmente por el sistema. En su lugar, debe usar: *"Reproducir vídeo"*, porque es conciso y tiene varios sílabas.
* Use los comandos del sistema. El *"Select"* comando está reservado por el sistema para desencadenar un evento Tap para el objeto tiene el foco. No volver a usar el *"Select"* comando en una palabra clave o frase, podrían no funcionar según lo esperado. Por ejemplo, si el comando de la voz para seleccionar un cubo en la aplicación era *"Cubo seleccione"*, pero el usuario estaba mirando una esfera cuando dijeron que el comando, a continuación, se seleccionan la esfera en su lugar. Del mismo modo, comandos de la barra de aplicación son voz habilitada. No use los siguientes comandos de voz en la vista de CoreWindow:
    1. Volver
    2. Herramienta de desplazamiento
    3. Herramienta de zoom
    4. Herramienta de arrastrar
    5. Ajustar
    6. Eliminar
* Use sonidos similares. Intente evitar el uso de comandos de voz una rima. Si tiene una aplicación de la compra que admite *"Mostrar Store"* y *"Mostrar más"* de comandos, como voz, a continuación, tendrá que deshabilitar uno de los comandos, mientras que el otro está en uso. Por ejemplo, podría usar la *"Mostrar Store"* botón para abrir el almacén y, a continuación, deshabilitar ese comando cuando se muestra el almacén para que la *"Mostrar más"* comando podría usarse para la exploración.

### <a name="instructions"></a>Instrucciones

* En Unity **jerarquía** del panel, utilice la herramienta de búsqueda para encontrar el **holoComm_screen_mesh** objeto.
* Haga doble clic en el **holoComm_screen_mesh** objeto para verlo en el **escena**. Se trata de inspección de los astronautas, que responderá a nuestros comandos de voz.
* En el **Inspector** panel, busque el **origen de entrada de voz (Script)** componente.
* Expanda el **palabras clave** sección para ver el comando de voz admitidos: **Abra Communicator**.
* Haga clic en el icono de engranaje a la derecha, a continuación, seleccione **editar Script**.
* Explorar **SpeechInputSource.cs** para conocer cómo utiliza el **KeywordRecognizer** para agregar los comandos de voz.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, utilice **archivo > configuración de compilación** para recompilar la aplicación.
* Abra el **aplicación** carpeta.
* Abra el **ModelExplorer Visual Studio solución**.

(Si ya creado o implementado este proyecto en Visual Studio durante la instalación, a continuación, puede abrir esa instancia de VS y haga clic en 'Volver a cargar todo' cuando se le solicite).

* En Visual Studio, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
* Después de la aplicación se implementa en el HoloLens, descartar el cuadro de ajuste utilizando el [pulsar en el aire](gestures.md#air-tap) gesto.
* Mire la inspección de los astronautas.
* Cuando el reloj tiene el foco, compruebe que el cursor cambia a un micrófono. Esto proporciona comentarios que la aplicación está escuchando comandos de voz.
* Compruebe que aparece una información sobre herramientas en el reloj. Esto ayuda a los usuarios descubrir el *"Communicator abierto"* comando.
* Mientras gazing en la inspección, por ejemplo *"Abrir Communicator"* para abrir el panel de communicator.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2: confirmación

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Grabar un mensaje mediante la entrada de micrófono.
* Proporcionar comentarios al usuario que la aplicación está escuchando en su propia voz.

>[!NOTE]
>El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono. Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"
>2. Haga clic en la pestaña "Plataforma Universal de Windows"
>3. En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad

### <a name="instructions"></a>Instrucciones

* En Unity **jerarquía** del panel, compruebe que la **holoComm_screen_mesh** objeto está seleccionado.
* En el **Inspector** panel, busque el **astronautas inspección (Script)** componente.
* Haga clic en el cubo pequeño y azul que se ha establecido como el valor de la **Communicator prefabricado** propiedad.
* En el **proyecto** panel, el **Communicator** prefabricado ahora debería tener el foco.
* Haga clic en el **Communicator** prefabricado en el **proyecto** panel para ver sus componentes en el **Inspector**.
* Examine el **Manager micrófono (Script)** componente, esto nos permitirá grabar la voz del usuario.
* Tenga en cuenta que el **Communicator** objeto tiene un **controlador de entrada de voz (Script)** componente para responder a la **enviar mensaje** comando.
* Examine el **Communicator (Script)** componente y haga doble clic en el script para abrirlo en Visual Studio.

Communicator.cs es responsable de establecer los Estados del botón adecuado en el dispositivo de communicator. Esto permitirá que los usuarios grabar un mensaje, reproducirlo y enviar el mensaje a los astronautas. También iniciará y detendrá una forma de onda animado, para confirmar que el usuario que estaba oír su voz.

* En **Communicator.cs**, elimine las líneas siguientes (81 y 82) desde el **iniciar** método. Esto permitirá que el botón 'Registro' en el communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilación e implementación

* En Visual Studio, vuelva a compilar la aplicación e implemente en el dispositivo.
* Mire la inspección de los astronautas y diga *"Communicator abierto"* para mostrar el communicator.
* Presione el **registro** botón (micrófono) para iniciar la grabación de un mensaje verbal para los astronautas.
* Empiece a hablar y compruebe que se reproduce la animación de onda en el communicator, lo que proporciona comentarios al usuario que se oye la voz.
* Presione el **detener** botón (cuadrado izquierdo) y compruebe que la animación de wave deja de ejecutarse.
* Presione el **reproducir** botón (triángulo) para reproducir el mensaje registrado y escuche en el dispositivo.
* Presione el **detener** botón (corchete derecho) para detener la reproducción del mensaje registrado.
* Por ejemplo *"Enviar mensaje"* para cerrar el communicator y recibir una respuesta de 'Mensaje recibido' de los astronautas.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3: descripción y el reconocimiento de dictado

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Usar el reconocimiento de dictado para convertir la voz del usuario en texto.
* Mostrar los resultados de hipótesis y finales de dictado del reconocedor en la communicator.

En este capítulo, vamos a usar el reconocimiento de dictado para crear un mensaje para los astronautas. Al usar el reconocimiento de dictado, tenga en cuenta que:

* Debe estar conectado a Wi-Fi para el reconocedor dictado funcione.
* Se producen tiempos de espera tras un período de tiempo establecido. Hay dos tiempos de espera a tener en cuenta:
  * Si el reconocedor se inicia y no oye ningún sonido para los primeros cinco segundos, lo hará el tiempo de espera.
  * Si el reconocedor ha dado un resultado pero, a continuación, oye silencio durante veinte segundos, lo hará el tiempo de espera.
* Puede ejecutar un único tipo de reconocedor (palabra clave o dictado) a la vez.

>[!NOTE]
>El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono. Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"
>2. Haga clic en la pestaña "Plataforma Universal de Windows"
>3. En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad

### <a name="instructions"></a>Instrucciones

Vamos a editar **MicrophoneManager.cs** para usar el reconocimiento de dictado. Esto es lo que vamos a agregar:

1. Cuando el **botón grabar** está presionado, vamos a **iniciar el DictationRecognizer**.
2. Mostrar el **hipótesis** de qué se entiende el DictationRecognizer.
3. Fijar el **resultados** de qué se entiende el DictationRecognizer.
4. Compruebe si los tiempos de espera de la DictationRecognizer.
5. Cuando el **botón detener** está presionado, o que expire la sesión de mic, **detener el DictationRecognizer**.
6. Reinicie el **KeywordRecognizer**, que escuchará el **enviar mensaje** comando.

Empecemos. Completar todos los ejercicios de codificación para 3.a en **MicrophoneManager.cs**, o copie y pegue el código terminado se encuentra a continuación:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilación e implementación

* Volver a generar en Visual Studio e implemente en el dispositivo.
* Descartar el cuadro de ajuste con un gesto de pulsar en el aire.
* Mire la inspección de los astronautas y diga *"Communicator abierto"*.
* Seleccione el **registro** botón (micrófono) para registrar el mensaje.
* Empiece a hablar. El **módulo de reconocimiento de dictado** interpretará su voz y mostrar el texto hipotética en el communicator.
* Intente decir *"Enviar mensaje"* mientras se graba un mensaje. Tenga en cuenta que el **reconocedor de palabra clave** no responde porque el **módulo de reconocimiento de dictado** todavía está activa.
* Dejar de hablar durante unos segundos. Ver como el reconocimiento de dictado se completa su hipótesis y muestra el resultado final.
* Empiece a hablar y, a continuación, hacer una pausa durante 20 segundos. Esto hará que el **módulo de reconocimiento de dictado** al tiempo de espera.
* Tenga en cuenta que el **reconocedor de palabra clave** se vuelve a habilitar después del tiempo de espera anterior. El communicator ahora responderá a los comandos de voz.
* Por ejemplo *"Enviar mensaje"* para enviar el mensaje a los astronautas.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4: módulo de reconocimiento de gramática

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Usar el reconocedor de gramática para reconocer la voz del usuario según un archivo de SRGS o especificación de gramática de reconocimiento de voz.

>[!NOTE]
>El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono. Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"
>2. Haga clic en la pestaña "Plataforma Universal de Windows"
>3. En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad

### <a name="instructions"></a>Instrucciones

1. En el **jerarquía** del panel, busque **Jetpack_Center** y selecciónelo.
2. Busque el **acción sean** secuencia de comandos en el **Inspector** panel.
3. Haga clic en el círculo pequeño a la derecha de la **objeto para etiquetas a lo largo de** campo.
4. En la ventana emergente, busque **SRGSToolbox** y selecciónela en la lista.
5. Eche un vistazo a la **SRGSColor.xml** de archivos en el **StreamingAssets** carpeta.
* La especificación de diseño SRGS puede encontrarse en el sitio Web de W3C [aquí](https://www.w3.org/TR/speech-grammar/).
* En nuestro archivo SRGS, tenemos tres tipos de reglas:
  * Una regla que permite especificar un color de una lista de doce colores.
  * Tres reglas que realizan escuchas de una combinación de la regla de color y una de las tres formas.
  * La regla raíz, colorChooser, que realiza escuchas para cualquier combinación de las tres reglas "de color + forma". Las formas se pueden decir en cualquier orden y en cualquier cantidad de solo uno a tres. Esta es la única regla que escucha, como se especifica como la regla raíz en la parte superior del archivo en la inicial &lt;gramática&gt; etiqueta.

### <a name="build-and-deploy"></a>Compilación e implementación

* Vuelva a compilar la aplicación en Unity, a continuación, compile e implemente desde Visual Studio para probar la aplicación en HoloLens.
* Descartar el cuadro de ajuste con un gesto de pulsar en el aire.
* Mire jetpack del astronautas y realizar un gesto de pulsar en el aire.
* Empiece a hablar. El **gramática reconocedor** interpretará su voz y cambiar los colores de las formas según el reconocimiento. Un comando de ejemplo es "círculo azul, amarillo cuadrado".
* Realice otra gesto de pulsar en el aire para descartar el cuadro de herramientas.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ahora ha completado **MR entrada 212: Voz**.

* Conocer la denegación de servicio y los contras de los comandos de voz.
* Se ha explicado cómo se emplea la información sobre herramientas que los usuarios sea consciente de los comandos de voz.
* Se ha visto varios tipos de comentarios que se utiliza para confirmar que se ha oído la voz del usuario.
* Saber cómo cambiar entre el reconocedor de palabra clave y el reconocimiento de dictado y forma en que estas dos características comprender e interpretan la voz.
* Ha aprendido a utilizar un archivo SRGS y el reconocimiento de la gramática de reconocimiento de voz en la aplicación.
