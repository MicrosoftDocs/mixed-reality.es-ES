---
title: 'Tutoriales de los servicios de voz de Azure: 2. Adición de un modo sin conexión para la traducción de voz a texto local'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7a0fa915a80763300eff470e29356034d6a0f841
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303676"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. Usar el reconocimiento de voz para ejecutar comandos

En este tutorial, agregarás la posibilidad de ejecutar comandos con el reconocimiento de voz de Azure, lo que te permitirá hacer que pase algo en función de la palabra o frase que definas.

## <a name="objectives"></a>Objetivos

* Aprender a usar el reconocimiento de voz de Azure para ejecutar comandos

## <a name="instructions"></a>Instrucciones

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Wake Word Recognizer (Script)** (Reconocimiento de la palabra de activación de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:

* En el campo **Wake Word** (Palabra de activación), escribe una frase adecuada; por ejemplo, _Activate terminal_ (Activar terminal).
* En el campo **Dismiss Word** (Palabra de descarte), escribe una frase adecuada; por ejemplo, _Dismiss terminal_ (Descartar terminal).

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> El componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Si ahora entras en el modo de juego, como en el tutorial anterior, el panel del terminal está habilitado de forma predeterminada, pero puedes deshabilitarlo diciendo la palabra de descarte: **Dismiss terminal** (Descartar terminal):

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Para volver a habilitarlo, indica la palabra de activación **Activate terminal** (Activar terminal):

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

> [!TIP]
> Si prevé que no podrá conectarse a Azure con frecuencia, también puede implementar comandos de voz mediante MRTK, para lo que debe seguir las instrucciones de [Uso de comandos de voz](mr-learning-base-09.md).

## <a name="congratulations"></a>Enhorabuena

Has implementado comandos de voz con tecnología de Azure. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.

En el próximo tutorial, aprenderás a traducir la voz mediante la traducción de voz de Azure.

[Tutorial siguiente: 3. Adición del componente de traducción de voz de Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
