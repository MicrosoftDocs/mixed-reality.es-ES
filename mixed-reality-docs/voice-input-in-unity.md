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
# <a name="voice-input-in-unity"></a>Entrada de voz en Unity

Unity expone tres maneras de agregar una [entrada de voz](voice-input.md) a la aplicación de Unity.

Con KeywordRecognizer (uno de los dos tipos de PhraseRecognizers), se puede proporcionar a la aplicación una matriz de comandos de cadena para realizar escuchas. Con GrammarRecognizer (el otro tipo de PhraseRecognizer), se puede proporcionar a la aplicación un archivo SRGS que defina una gramática específica para realizar escuchas. Con el DictationRecognizer, la aplicación puede escuchar cualquier palabra y proporcionar al usuario una nota u otra presentación de la voz.

>[!NOTE]
>Solo se puede controlar el reconocimiento de dictado o de frase a la vez. Esto significa que, si GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no puede estar activo y viceversa.

## <a name="enabling-the-capability-for-voice"></a>Habilitación de la funcionalidad de Voice

La capacidad del **micrófono** se debe declarar para que una aplicación aproveche la entrada de voz.
1. En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".
2. Haga clic en la pestaña "tienda Windows"
3. En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .

## <a name="phrase-recognition"></a>Reconocimiento de frases

Para permitir que la aplicación escuche frases específicas que habla el usuario, realice alguna acción; debe:
1. Especificar las frases que se van a escuchar con KeywordRecognizer o GrammarRecognizer
2. Controle el evento OnPhraseRecognized y tome las medidas correspondientes a la frase reconocida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Espacio de nombres**: *UnityEngine. Windows. Speech*<br>
**Distintos** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Necesitamos algunas instrucciones Using para guardar algunas pulsaciones de teclas:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

A continuación, vamos a agregar algunos campos a la clase para almacenar el reconocedor y la palabra clave > Diccionario de acciones:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Ahora, agregue una palabra clave al diccionario (por ejemplo, dentro de un método Start ()). Estamos agregando la palabra clave "activar" en este ejemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Cree el reconocedor de palabras clave e indíquele lo que desea reconocer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Regístrese ahora para el evento OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Un controlador de ejemplo es:

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

Por último, empiece a reconocer.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**System.IO** *UnityEngine. Windows. Speech*<br>
**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

El GrammarRecognizer se usa si se especifica la gramática de reconocimiento mediante SRGS. Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más complejas o si desea activar o desactivar fácilmente conjuntos de comandos. Vea: [Cree gramáticas con XML de SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obtener información sobre el formato de archivo.

Una vez que tenga la gramática de SRGS y esté en el proyecto en una [carpeta StreamingAssets](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Cree un GrammarRecognizer y pásele la ruta de acceso al archivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Regístrese ahora para el evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Obtendrá una devolución de llamada que contiene la información especificada en la gramática de SRGS que puede controlar de forma adecuada. La mayor parte de la información importante se proporcionará en la matriz semanticMeanings.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Por último, empiece a reconocer.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dictado

**System.IO** *UnityEngine. Windows. Speech*<br>
**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use DictationRecognizer para convertir la voz del usuario en texto. DictationRecognizer expone la funcionalidad de [dictado](voice-input.md#dictation) y admite el registro y la escucha de eventos de hipótesis y frases completadas, de forma que puede enviar comentarios al usuario mientras hablan y después. Los métodos Start () y STOP () respectivamente habilitan y deshabilitan el reconocimiento de dictado. Una vez que se realiza con el reconocedor, se debe desechar mediante el método Dispose () para liberar los recursos que utiliza. Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se publican antes.

Solo se necesitan algunos pasos para empezar a trabajar con el dictado:
1. Crear un nuevo DictationRecognizer
2. Controlar los eventos de dictado
3. Inicio de DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitar la funcionalidad para el dictado

La capacidad de "cliente de Internet", además de la capacidad de "micrófono" mencionada anteriormente, se debe declarar para que una aplicación aproveche el dictado.
1. En el editor de Unity, vaya a la página "Editar > configuración del proyecto > reproductor" para ir a la configuración del reproductor.
2. Haga clic en la pestaña "tienda Windows"
3. En la sección "configuración de publicación > funcionalidades", Compruebe la funcionalidad de **InternetClient** .

### <a name="dictationrecognizer"></a>DictationRecognizer

Cree un DictationRecognizer como el siguiente:

```
dictationRecognizer = new DictationRecognizer();
```

Hay cuatro eventos de dictado a los que se puede suscribir y controlar para implementar el comportamiento de dictado.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Este evento se desencadena después de que el usuario se pausa, normalmente al final de una frase. Aquí se devuelve la cadena completa reconocida.

En primer lugar, suscríbase al evento DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

A continuación, controle la devolución de llamada DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Este evento se desencadena continuamente mientras el usuario está hablando. A medida que el reconocedor realiza escuchas, proporciona texto de lo que se oye hasta ahora.

En primer lugar, suscríbase al evento DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

A continuación, controle la devolución de llamada DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Este evento se desencadena cuando se detiene el reconocedor, ya sea de detención (), se ha producido un tiempo de espera o de algún otro error.

En primer lugar, suscríbase al evento DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

A continuación, controle la devolución de llamada DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Este evento se desencadena cuando se produce un error.

En primer lugar, suscríbase al evento DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

A continuación, controle la devolución de llamada DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Una vez que haya suscrito y controlado los eventos de dictado que le interesan, inicie el reconocedor de dictado para comenzar a recibir eventos.

```
dictationRecognizer.Start();
```

Si ya no desea mantener el DictationRecognizer en torno, debe cancelar la suscripción a los eventos y eliminar el DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Útiles**
* Los métodos Start () y STOP () respectivamente habilitan y deshabilitan el reconocimiento de dictado.
* Una vez que se realiza con el reconocedor, se debe desechar mediante el método Dispose () para liberar los recursos que utiliza. Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se publican antes.
* Los tiempos de espera se producen después de un período de tiempo establecido. Puede buscar estos tiempos de espera en el evento DictationComplete. Hay dos tiempos de espera que se deben tener en cuenta:
   1. Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.
   2. Si el reconocedor ha dado un resultado pero oye el silencio durante veinte segundos, se agotará el tiempo de espera.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usar el reconocimiento de frases y el dictado

Si desea usar tanto el reconocimiento de frases como el dictado en la aplicación, deberá apagarlo completamente antes de poder iniciar el otro. Si tiene varios KeywordRecognizers en ejecución, puede cerrarlos todos a la vez con:

```
PhraseRecognitionSystem.Shutdown();
```

Para restaurar todos los reconocedores a su estado anterior, una vez detenido el DictationRecognizer, puede llamar a:

```
PhraseRecognitionSystem.Restart();
```

También puede iniciar una KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem también.

## <a name="using-the-microphone-helper"></a>Uso de la aplicación auxiliar de micrófono

El kit de herramientas de realidad mixta en GitHub contiene una clase auxiliar de micrófono para sugerir a los desarrolladores si hay un micrófono utilizable en el sistema. Un uso para este es el lugar en el que desea comprobar si hay un micrófono en el sistema antes de mostrar las sugerencias de interacción de voz en la aplicación.

El script de la aplicación auxiliar de micrófono se puede encontrar en la [carpeta INPUT/scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). El repositorio de GitHub también contiene un [pequeño ejemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) en el que se muestra cómo usar el ayudante.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz en el kit de herramientas de realidad mixta
Puede encontrar ejemplos de la entrada de voz en esta escena.

- [HoloToolkit-Examples/INPUT/Scenes/SpeechInputSource. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
