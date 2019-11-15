---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: cf51505cab2db765325c2e7b78a52e4b790845c9
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105957"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Módulo de aprendizaje de Speech SDK: control selector de Rocket con comandos de voz

En esta lección, usaremos la característica de intención del servicio de voz de Azure para comprender la intención de la voz. Usaremos el intento de voz detectado como comandos de voz para controlar el selector de Rocket. En esta lección, se importará el recurso del selector de Rocket y se interconectarán los comandos de la voz de intención detectados con los botones de control predefinidos para controlar el cohete.

## <a name="objectives"></a>Objetivos

- Obtenga información sobre cómo conectar el intento de voz como comandos de voz.
- Obtenga información sobre cómo usar los comandos de voz para el intento de voz como comandos de entrada de control de Rocket.

## <a name="instructions"></a>Instrucciones

1. En este tutorial, vamos a usar un recurso "BaseModule" para integrar Rocket Launcher con los comandos de voz. Para ello, es necesario importar el recurso en el proyecto. Puede descargar el recurso "Rocket Launcher" mediante este [vínculo](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage).

2. Para importar el recurso, vaya a activos-> Importar paquete personalizado >-> navegue hasta el archivo descargado y haga clic en importar.

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. Después de importar el recurso "recursos del módulo base", navegue dentro de la carpeta "recursos del módulo base": > Prefabs-> seleccione "Rocket Launcher_Complete" y, a continuación, arrástrelo y colóquelo en la jerarquía de escenas existente.

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. Ahora tenemos que integrar nuestro "selector de Rocket" con nuestro proyecto LUIS en la [lección](mrlearning-speechSDK-ch4.md)anterior. Para ello, expanda el recurso prefabricado "Rocket Launcher_Complete" en la jerarquía y busque los botones "LaunchRoundButton", "ResetRoundButton" y "sugerencias de colocación".

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. Seleccione "LaunchRoundButton" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque "LunarModule" recurso prefabricado. A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "StartThruster ()" y selecciónela.

    ![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. Seleccione "ResetRoundButton" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque "LunarModule" recurso prefabricado. A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "resetModule ()" y selecciónela.

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. Seleccione "sugerencias de colocación" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque el recurso prefabricado "LunarModule". A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "TogglePlacementHints" y seleccione ToggleGameOBjects ().

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. Después, seleccione la Lunarcom_Completed recurso prefabricado en la jerarquía y navegue hasta el script "Lunarcom reconocedor de intenciones" en el inspector y, a continuación, arrastre y coloque los botones "LaunchRoundButton", "ResetRoundButton" y "sugerencias de colocación" a sus lugares respectivos.

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. Presione el botón PLAY (reproducir) en el editor de Unity y haga clic en el botón "Rocket" (jugar) y en las frases como "botón de inicio de la instalación de inserción", "mostrarme una sugerencia de colocación", "Presione el botón de REST" o cualquier otra frase relacionada con la solicitud de inicio, restablecimiento u sugerencia del iniciador de Rocket.

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>Enhorabuena

En esta lección, hemos aprendido a conectar los comandos de voz con tecnología de AI a comandos de voz para usarlos como método de entrada. Ahora nuestro programa puede usar los altavoces intención como comandos de voz para proporcionar entradas para el selector de Rocket.
