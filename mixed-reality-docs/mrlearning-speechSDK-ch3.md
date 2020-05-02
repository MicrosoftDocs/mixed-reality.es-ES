---
title: 'Tutoriales de los servicios de voz de Azure: 3. Adición del componente Speech Translation de Azure Cognitive Services'
description: En este curso, aprenderás a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028343"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Adición del componente Speech Translation de Azure Cognitive Services

En este tutorial, agregarás traducción de voz al proyecto, lo que te permitirá traducir y transcribir la voz en tres idiomas diferentes.

## <a name="objectives"></a>Objetivos

* Aprender a integrar la traducción de voz de Azure

## <a name="instructions"></a>Instrucciones

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Translation Recognizer (Script)** (Reconocimiento de traducción de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:

* Cambia **Target Language** (Idioma de destino) al idioma que quieras; por ejemplo, _German_ (Alemán).

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> El componente Lunarcom Translation Recognizer (Script) (Reconocimiento de traducción de Lunarcom [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Si ahora entras en el modo de juego, puedes probar la traducción de voz presionando primero el botón del satélite: A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se traducirá al idioma seleccionado y se transcribirá en el panel del terminal:

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Ahora, el proyecto puede traducir correctamente las palabras que digas en varios idiomas diferentes. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.

[Tutorial siguiente: 4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural](mrlearning-speechSDK-ch4.md)
