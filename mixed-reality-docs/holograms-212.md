---
title: Entrada MR 212-voz
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522354"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-input-212-voice"></a>Entrada MR 212: Voz

La [entrada de voz](voice-input.md) nos proporciona otro método para interactuar con los hologramas. Los comandos de voz funcionan de forma muy natural y sencilla. Diseñe los comandos de voz para que estén:

* Clásica
* Fácil de recordar
* Contexto adecuado
* Lo suficientemente distinto de otras opciones en el mismo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

En los [conceptos básicos de MR 101](holograms-101.md), usamos KeywordRecognizer para crear dos sencillos comandos de voz. En la entrada MR 212, profundizaremos más en cómo:

* Diseñe comandos de voz que estén optimizados para el motor de voz de HoloLens.
* Haga que el usuario tenga en cuenta qué comandos de voz están disponibles.
* Confirme que hemos escuchado el comando de voz del usuario.
* Comprenda lo que está diciendo el usuario, mediante un reconocedor de dictado.
* Use un reconocedor de gramática para escuchar comandos basados en un archivo SRGS o una especificación de gramática de reconocimiento de voz.

En este curso, volveremos a visitar el explorador de modelos, que hemos creado en la [entrada mr 210](holograms-210.md) y la [entrada Mr 211](holograms-211.md).

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada MR 212: Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de comenzar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.
* Funcionalidad básica C# de programación.
* Debe haber completado los [principios básicos 101](holograms-101.md).
* Debe haber completado la [entrada MR 210](holograms-210.md).
* Debe haber completado la [entrada MR 211](holograms-211.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe estar deshabilitado *(* desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.

## <a name="unity-setup"></a>Configuración de Unity

### <a name="instructions"></a>Instrucciones

1. Inicia Unity.
2. Seleccione **abrir**.
3. Vaya a la carpeta **HolographicAcademy-hologramas-212-Voice** que previamente eliminó de archivado.
4. Busque y seleccione la carpeta de **Inicio**/del**Explorador de modelos** .
5. Haga clic en el botón **Seleccionar carpeta** .
6. En el panel **proyecto** , expanda la carpeta **escenas** .
7. Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.
3. Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**. De lo contrario, déjelo en **cualquier dispositivo**.
4. Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).
5. Haz clic en **Compilación**.
6. Cree una **nueva carpeta** denominada "app".
7. Haga clic en la carpeta de la **aplicación** .
8. Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.

Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.

1. Abra la carpeta de la **aplicación** .
2. Abra la **solución ModelExplorer de Visual Studio**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
2. Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.
3. Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** . Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.
4. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.

Si se implementa en un auricular envolvente:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.
2. Asegúrese de que el destino de implementación está establecido en **equipo local**.
3. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
4. Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojos en el panel de errores de Visual Studio. Es seguro ignorarlos. Cambie al panel de salida para ver el progreso real de la compilación. Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).

## <a name="chapter-1---awareness"></a>Capítulo 1: reconocimiento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre las **dos y no** el diseño de los comandos de voz.
* Use **KeywordRecognizer** para agregar comandos de voz basados en la mirada.
* Hacer que los usuarios conozcan los comandos de voz mediante los **comentarios**del cursor.

### <a name="voice-command-design"></a>Diseño de comandos de voz

En este capítulo, aprenderá a diseñar comandos de voz. Al crear comandos de voz:

#### <a name="do"></a>DO

* Cree comandos concisos. No quiere usar *"reproducir el vídeo seleccionado actualmente"* , ya que ese comando no es conciso y el usuario lo olvidará fácilmente. En su lugar, debe usar: *"Reproducir vídeo"* , ya que es conciso y tiene varias sílabas.
* Usar un vocabulario sencillo. Siempre intente usar palabras y frases comunes que resulten fáciles de detectar y recordar. Por ejemplo, si la aplicación tenía un objeto de nota que se podría mostrar u ocultar en la vista, no usaría el comando *"show letrero"* , ya que "letrero" es un término que rara vez se usa. En su lugar, usaría el comando: *"Mostrar nota"* para mostrar la nota en la aplicación.
* Ser coherente. Los comandos de voz deben mantenerse coherentes en toda la aplicación. Imagine que tiene dos escenas en la aplicación y ambas escenas contienen un botón para cerrar la aplicación. Si la primera escena usó el comando *"salir"* para desencadenar el botón, pero la segunda escena usaba el comando *"cerrar aplicación"* , el usuario se quedará muy confundido. Si la misma funcionalidad persiste en varias escenas, se debe usar el mismo comando de voz para desencadenarla.

#### <a name="dont"></a>NO

* Use los comandos de una sola sílaba. Por ejemplo, si estuviera creando un comando de voz para reproducir un vídeo, debe evitar el uso del comando simple *"Play"* , ya que es una sola sílaba y el sistema puede perderlo fácilmente. En su lugar, debe usar: *"Reproducir vídeo"* , ya que es conciso y tiene varias sílabas.
* Usar comandos del sistema. El sistema reserva el comando *"Select"* para desencadenar un evento TAP para el objeto que tiene actualmente el foco. No vuelva a usar el comando *"Select"* en una palabra clave o frase, ya que es posible que no funcione como se espera. Por ejemplo, si el comando de voz para seleccionar un cubo en la aplicación fuera *"seleccionar cubo"* , pero el usuario estaba examinando una esfera cuando creó el comando, la esfera se seleccionaría en su lugar. Igualmente, los comandos de la barra de la aplicación están habilitados para voz. No use los siguientes comandos de voz en la vista de CoreWindow:
    1. Volver
    2. Herramienta de desplazamiento
    3. Herramienta de zoom
    4. Herramienta de arrastre
    5. Ajustar
    6. Eliminar
* Usar sonidos similares. Intente evitar el uso de comandos de voz que Rhyme. Si tiene una aplicación de compras que admitía *"Mostrar tienda"* y *"Mostrar más"* como comandos de voz, querrá deshabilitar uno de los comandos mientras el otro estaba en uso. Por ejemplo, puede usar el botón *"Mostrar tienda"* para abrir el almacén y, a continuación, deshabilitar ese comando cuando se mostró el almacén para que el comando *"Mostrar más"* pueda usarse para la exploración.

### <a name="instructions"></a>Instrucciones

* En el panel  de jerarquías de Unity, use la herramienta de búsqueda para buscar el objeto **holoComm_screen_mesh** .
* Haga doble clic en el objeto **holoComm_screen_mesh** para verlo en la **escena**. Esta es la inspección de Astronaut, que responderá a los comandos de voz.
* En el panel **Inspector** , busque el componente de **origen de entrada de voz (Script)** .
* Expanda la sección **palabras clave** para ver el comando de voz admitido: **Abra Communicator**.
* Haga clic en engranaje en el lado derecho y, luego, seleccione **Editar script**.
* Explore **SpeechInputSource.CS** para saber cómo usa **KeywordRecognizer** para agregar comandos de voz.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.
* Abra la carpeta de la **aplicación** .
* Abra la **solución ModelExplorer de Visual Studio**.

(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).

* En Visual Studio, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
* Después de que la aplicación se implemente en HoloLens, descartará el cuadro de ajuste mediante el gesto [de punteo de aire](gestures.md#air-tap) .
* Mira fijamente en la inspección de Astronaut.
* Cuando el reloj tenga el foco, compruebe que el cursor cambia a un micrófono. Esto proporciona comentarios que la aplicación está escuchando para los comandos de voz.
* Compruebe que aparece una información sobre herramientas en el reloj. Esto ayuda a los usuarios a detectar el comando *"abrir Communicator"* .
* Mientras Gazing en el reloj, Imagine *"abrir Communicator"* para abrir el panel de Communicator.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2: confirmación

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Grabe un mensaje mediante la entrada de micrófono.
* Enviar comentarios al usuario que la aplicación está escuchando en la voz.

>[!NOTE]
>La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono. Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".
>2. Haga clic en la pestaña "Plataforma universal de Windows"
>3. En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .

### <a name="instructions"></a>Instrucciones

* En el panel  de jerarquías de Unity, compruebe que está seleccionado el objeto **holoComm_screen_mesh** .
* En el panel **Inspector** , busque el componente **Astronaut Watch (Script)** .
* Haga clic en el pequeño cubo azul que se establece como el valor de la propiedad **Communicator recurso prefabricado** .
* En el panel **proyecto** , el recurso prefabricado de **Communicator** debería tener ahora el foco.
* Haga clic en **Communicator** recurso prefabricado en el panel **proyecto** para ver sus componentes en el **Inspector**.
* Fíjese en el componente **Administrador de micrófonos (Script)** , lo que nos permitirá grabar la voz del usuario.
* Observe que el objeto **Communicator** tiene un componente de **controlador de entrada de voz (Script)** para responder al comando **send Message** .
* Fíjese en el componente **Communicator (Script)** y haga doble clic en el script para abrirlo en Visual Studio.

Communicator.cs es responsable de establecer los Estados de botón adecuados en el dispositivo Communicator. Esto permitirá a los usuarios grabar un mensaje, reproducirlo y enviar el mensaje a Astronaut. También iniciará y detendrá un formulario de onda animada para confirmar al usuario que se ha escuchado su voz.

* En **Communicator.CS**, elimine las líneas siguientes (81 y 82) del método **Start** . Esto habilitará el botón "registro" en Communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilación e implementación

* En Visual Studio, vuelva a compilar la aplicación e implementarla en el dispositivo.
* Mira la inspección de Astronaut y di *"abrir Communicator"* para mostrar el Communicator.
* Presione el botón **grabar** (micrófono) para iniciar la grabación de un mensaje verbal para el Astronaut.
* Empiece a hablar y compruebe que la animación de onda se reproduce en Communicator, que proporciona comentarios al usuario de que se oye su voz.
* Presione el botón **detener** (cuadrado izquierdo) y compruebe que la animación de onda deja de ejecutarse.
* Presione el botón de **reproducción** (triángulo derecho) para reproducir el mensaje grabado y oír en el dispositivo.
* Presione el botón **detener** (cuadrado derecho) para detener la reproducción del mensaje grabado.
* Por ejemplo, *"Enviar mensaje"* para cerrar Communicator y recibir una respuesta "mensaje recibido" de Astronaut.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3: Descripción y el reconocedor de dictado

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Use el reconocedor de dictado para convertir la voz del usuario en texto.
* Mostrar los resultados teóricos y finales del reconocedor de dictado en Communicator.

En este capítulo, usaremos el reconocedor de dictado para crear un mensaje para el Astronaut. Al usar el reconocedor de dictado, tenga en cuenta lo siguiente:

* Debe estar conectado a la red Wi-Fi para que el reconocedor de dictado funcione.
* Los tiempos de espera se producen después de un período de tiempo establecido. Hay dos tiempos de espera que se deben tener en cuenta:
  * Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.
  * Si el reconocedor ha dado un resultado pero oye el silencio durante veinte segundos, se agotará el tiempo de espera.
* Solo se puede ejecutar un tipo de reconocedor (palabra clave o dictado) a la vez.

>[!NOTE]
>La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono. Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".
>2. Haga clic en la pestaña "Plataforma universal de Windows"
>3. En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .

### <a name="instructions"></a>Instrucciones

Vamos a editar **MicrophoneManager.CS** para usar el reconocedor de dictado. Esto es lo que agregaremos:

1. Cuando se presiona el **botón grabar** , se **inicia el DictationRecognizer**.
2. Mostrar la **hipótesis** de lo que DictationRecognizer entendió.
3. Bloquee los **resultados** de lo que DictationRecognizer entendió.
4. Compruebe los tiempos de espera de DictationRecognizer.
5. Cuando se presiona el **botón detener** o se agota el tiempo de espera de la sesión MIC, **detenga el DictationRecognizer**.
6. Reinicie **KeywordRecognizer**, que escuchará el comando **send Message** .

Empecemos. Complete todos los ejercicios de codificación de 3. a en **MicrophoneManager.CS**, o copie y pegue el código finalizado que se encuentra a continuación:

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

* Vuelva a compilar en Visual Studio e impleméntela en el dispositivo.
* Descartar el cuadro de ajuste con un gesto de punteo de aire.
* Mira el Astronaut y di *"abrir Communicator"* .
* Seleccione el botón **grabar** (micrófono) para grabar el mensaje.
* Empiece a hablar. El  reconocedor de dictado interpretará su voz y mostrará el texto teórico en Communicator.
* Intente decir *"Enviar mensaje"* mientras está grabando un mensaje. Observe que el reconocedor de **palabras clave** no responde  porque el reconocedor de dictado todavía está activo.
* Deje de hablar durante unos segundos. Observe que el reconocedor de dictado completa su hipótesis y muestra el resultado final.
* Empiece a hablar y, a continuación, PAUSE durante 20 segundos. Esto hará que el  reconocedor de dictado agote el tiempo de espera.
* Tenga en cuenta que el reconocedor de **palabras clave** se vuelve a habilitar después del tiempo de espera anterior. Communicator responderá ahora a los comandos de voz.
* Por ejemplo, *"Enviar mensaje"* para enviar el mensaje a Astronaut.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4: Reconocedor de gramática

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Use el reconocedor de gramática para reconocer la voz del usuario de acuerdo con un archivo SRGS o una especificación de gramática de reconocimiento de voz.

>[!NOTE]
>La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono. Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".
>2. Haga clic en la pestaña "Plataforma universal de Windows"
>3. En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .

### <a name="instructions"></a>Instrucciones

1. En el panel **jerarquía** , busque **Jetpack_Center** y selecciónelo.
2. Busque el script de **acción tagalong** en el panel **Inspector** .
3. Haga clic en el círculo pequeño situado a la derecha del **objeto para etiquetar a lo largo** del campo.
4. En la ventana que aparece, busque **SRGSToolbox** y selecciónela en la lista.
5. Eche un vistazo al archivo **SRGSColor. XML** de la carpeta **StreamingAssets** .
* Las especificaciones de diseño de SRGS se pueden encontrar [aquí](https://www.w3.org/TR/speech-grammar/)en el sitio web de W3C.
* En nuestro archivo SRGS, tenemos tres tipos de reglas:
  * Una regla que le permite decir un color de una lista de doce colores.
  * Tres reglas que escuchan una combinación de la regla de color y una de las tres formas.
  * La regla raíz, colorChooser, que escucha cualquier combinación de las tres reglas de "color + forma". Las formas se pueden decir en cualquier orden y en cualquier cantidad de solo de una a las tres. Esta es la única regla que se escucha, ya que se especifica como la regla raíz en la parte superior del archivo en la etiqueta de &lt;gramática&gt; inicial.

### <a name="build-and-deploy"></a>Compilación e implementación

* Vuelva a compilar la aplicación en Unity y luego compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.
* Descartar el cuadro de ajuste con un gesto de punteo de aire.
* Mira el jetpack del Astronaut y realiza un gesto de pulsación de aire.
* Empiece a hablar. El reconocedor de **gramática** interpretará la voz y cambiará los colores de las formas en función del reconocimiento. Un comando de ejemplo es "círculo azul, cuadrado amarillo".
* Realice otro gesto de punteo de aire para descartar el cuadro de herramientas.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ya ha completado **la entrada Mr 212: Voz**.

* Conoce las dos y no los comandos de voz.
* Vio cómo se empleó la información sobre herramientas para que los usuarios conozcan los comandos de voz.
* Vio varios tipos de comentarios usados para confirmar que se ha escuchado la voz del usuario.
* Sabe cómo cambiar entre el reconocedor de palabras clave y el reconocedor de dictado y cómo estas dos características entienden e interpretan la voz.
* Ha aprendido a usar un archivo SRGS y el reconocedor de gramática para el reconocimiento de voz en la aplicación.
