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
# <a name="voice-input-in-unity"></a>Entrada de voz en Unity

Unity expone tres maneras de agregar [entrada de voz](voice-input.md) a la aplicación de Unity.

Con el KeywordRecognizer (uno de los dos tipos de PhraseRecognizers), la aplicación se puede proporcionar una matriz de cadena de comandos para escuchar. Con el GrammarRecognizer (el otro tipo de PhraseRecognizer), la aplicación se puede proporcionar un archivo SRGS define una gramática específicos para que escuche. Con el DictationRecognizer, la aplicación puede escuchar cualquier palabra y proporcionar al usuario una nota u otra pantalla de su voz.

>[!NOTE]
>Solo el dictado o reconocimiento de frase se puede controlar a la vez. Esto significa que si un GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no pueden activarse y viceversa.

## <a name="enabling-the-capability-for-voice"></a>Habilitación de la capacidad de voz

El **micrófono** se debe declarar la funcionalidad de una aplicación aprovechar la entrada de voz.
1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"
2. Haga clic en la pestaña "Windows Store"
3. En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad

## <a name="phrase-recognition"></a>Reconocimiento de frase

Para habilitar la aplicación realizar escuchas de específicos de frases habla por el usuario, a continuación, realizar alguna acción, deberá:
1. Especifique qué frases para que escuche para usar un KeywordRecognizer o GrammarRecognizer
2. Controle el evento OnPhraseRecognized y tomar la acción que corresponde a la frase reconocida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Necesitaremos algunas instrucciones using al guardar algunas pulsaciones de teclas:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

A continuación, vamos a agregar unos cuantos campos a la clase para almacenar el módulo de reconocimiento y la palabra clave -> diccionario de acción:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Ahora puede agregar una palabra clave al diccionario (por ejemplo, dentro de un método Start()). Estamos agregando la palabra clave "activar" en este ejemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Crear el módulo de reconocimiento de la palabra clave e indicarle lo que debemos reconocer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Regístrese ahora para el evento OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Es un controlador de ejemplo:

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

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Se usa el GrammarRecognizer si está especificando la gramática de reconocimiento de SRGS. Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más compleja, o si desea activar y desactivar los conjuntos de comandos la fácilmente. Vea: [Crear mediante gramáticas XML de SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para obtener información de formato de archivo.

Una vez que tiene la gramática de SRGS, y se encuentra en el proyecto en un [StreamingAssets carpeta](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Cree un GrammarRecognizer y pasar la ruta de acceso al archivo de SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Regístrese ahora para el evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Recibirá una devolución de llamada que contiene la información especificada en la gramática de SRGS que pueden controlar adecuadamente. Se proporcionará la mayor parte de la información importante en la matriz semanticMeanings.

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

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Utilice el DictationRecognizer para convertir la voz del usuario en texto. Expone el DictationRecognizer [dictado](voice-input.md#dictation) funcionalidad y permite registrar y escuchar las hipótesis y una frase completa eventos, por lo que puede proporcionar comentarios para el usuario mientras habla y posteriormente. Métodos Start() y Stop() habilitan y deshabilitar el reconocimiento de dictado respectivamente. Una vez terminado el reconocedor, debe eliminarse mediante el método Dispose() para liberar los recursos que usa. Lanzará estos recursos automáticamente durante la recolección de elementos con un costo de rendimiento adicionales si no se libera antes de eso.

Hay solo unos pocos pasos necesarios para empezar a trabajar con dictado:
1. Crear un nuevo DictationRecognizer
2. Controlar eventos de dictado
3. Iniciar el DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitación de la capacidad de dictado

La capacidad de "Cliente de Internet", además de la funcionalidad de "Micrófono" se ha mencionado anteriormente, se debe declarar para que una aplicación aprovechar el dictado.
1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a la página "Editar > proyecto configuración > Player"
2. Haga clic en la pestaña "Windows Store"
3. En la sección "Funcionalidades de publicación configuración >", compruebe el **InternetClient** capacidad

### <a name="dictationrecognizer"></a>DictationRecognizer

Crear un DictationRecognizer así:

```
dictationRecognizer = new DictationRecognizer();
```

Hay cuatro eventos de dictado que puedan estar suscrito a y normalmente para implementar el comportamiento de dictado.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Este evento se desencadena después de que el usuario pone en pausa, normalmente al final de una frase. El completo reconoce la cadena se devuelve aquí.

En primer lugar, se suscribe al evento DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

A continuación, controlar la devolución de llamada DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Este evento se desencadena continuamente mientras está hablando con el usuario. Como el reconocimiento de escucha, proporciona el texto de lo que es oído hasta ahora.

En primer lugar, se suscribe al evento DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

A continuación, controlar la devolución de llamada DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Este evento se desencadena cuando se detiene el reconocedor, ya sea desde Stop() llama, un tiempo de espera que se producen o algún otro error.

En primer lugar, se suscribe al evento DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

A continuación, controlar la devolución de llamada DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Este evento se desencadena cuando se produce un error.

En primer lugar, se suscribe al evento DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

A continuación, controlar la devolución de llamada DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Una vez que se haya suscrito y controla los eventos de dictado que le interesen, inicie el reconocimiento de dictado para empezar a recibir eventos.

```
dictationRecognizer.Start();
```

Si ya no desea mantener el DictationRecognizer alrededor, deberá cancelar la suscripción a los eventos y desechar la DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Sugerencias**
* Métodos Start() y Stop() habilitan y deshabilitar el reconocimiento de dictado respectivamente.
* Una vez terminado el reconocedor, deben eliminarse mediante el método Dispose() para liberar los recursos que usa. Lanzará estos recursos automáticamente durante la recolección de elementos con un costo de rendimiento adicionales si no se libera antes de eso.
* Se producen tiempos de espera tras un período de tiempo establecido. Puede buscar estos tiempos de espera en el evento DictationComplete. Hay dos tiempos de espera a tener en cuenta:
   1. Si el reconocedor se inicia y no oye ningún sonido para los primeros cinco segundos, lo hará el tiempo de espera.
   2. Si el reconocedor ha dado un resultado pero, a continuación, oye silencio durante veinte segundos, lo hará el tiempo de espera.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usar el reconocimiento de frase y el dictado

Si desea usar el reconocimiento de frase y el dictado en la aplicación, deberá totalmente apagar uno antes de empezar a otro. Si tiene varios ejecución KeywordRecognizers, puede apagar ellos todas a la vez con:

```
PhraseRecognitionSystem.Shutdown();
```

Para restaurar todos los reconocedores a su estado anterior, una vez se ha detenido el DictationRecognizer, puede llamar:

```
PhraseRecognitionSystem.Restart();
```

También se pudo iniciar un KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem así.

## <a name="using-the-microphone-helper"></a>Uso de la aplicación auxiliar de micrófono

El Kit de herramientas de realidad mixta en GitHub contiene una clase auxiliar de micrófono para sugerir a los desarrolladores si no hay un micrófono utilizable en el sistema. Un uso para ella es donde puede que desee comprobar si hay micrófono en el sistema antes de mostrar cualquier voz sugerencias de interacción en la aplicación.

El script de aplicación auxiliar de micrófono puede encontrarse en el [carpeta de entrada, Scripts o utilidades](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). El repositorio de GitHub contiene también un [pequeño ejemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) que muestra cómo utilizar la aplicación auxiliar.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz en el Kit de herramientas de realidad mixta
Puede encontrar los ejemplos de la entrada de voz en esta escena.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
