---
title: 'Tutoriales de los servicios de voz de Azure: 1. Integración y uso de reconocimiento de voz y la transcripción'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f376ab268e9c2869e48b325fa728672a16ee6d32
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303686"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integración y uso del reconocimiento de voz y la transcripción

## <a name="overview"></a>Introducción


En esta serie de tutoriales, crearás una aplicación de Mixed Reality que explore el uso de los servicios de voz de Azure con HoloLens 2. Cuando completes esta serie de tutoriales, podrás usar el micrófono del dispositivo para transcribir la voz a texto en tiempo real, traducir la voz a otros idiomas y aprovechar la característica Reconocimiento de la intención para comprender los comandos de voz mediante inteligencia artificial.

## <a name="objectives"></a>Objetivos

* Aprender a integrar los servicios de voz de Azure con una aplicación de HoloLens 2
* Aprender a usar el reconocimiento de voz para transcribir texto

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado la serie de [tutoriales de introducción](mr-learning-base-01.md), es recomendable que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *Tutoriales de MRTK*
2. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Importar Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Configurar el proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project)
6. [Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, *AzureSpeechServices*

A continuación, siga las instrucciones del artículo [Modificación de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

## <a name="configuring-the-speech-commands-start-behavior"></a>Configurar el comportamiento inicial de los comandos de voz

Dado que usarás el SDK de voz para el reconocimiento de voz y la transcripción, debes configurar los comandos de voz de MRTK para que no interfieran con la funcionalidad del SDK de voz. Para ello, puedes cambiar el comportamiento inicial de los comandos de voz de Auto Start (Inicio automático) a Manual Start (Inicio manual).

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Input** (Entrada), clona **DefaultHoloLens2InputSystemProfile** y **DefaultMixedRealitySpeechCommandsProfile** y, a continuación, cambia el valor de **Start Behavior** (Comportamiento inicial) de los comandos de voz a **Manual Start** (Inicio manual):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar y configurar perfiles de MRTK, puede consultar las instrucciones del artículo [Configuración de los perfiles de Mixed Reality Toolkit](mr-learning-base-03.md).

## <a name="configuring-the-capabilities"></a>Configuración de las funcionalidades

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén habilitadas. A continuación, habilita las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer**:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versión más reciente)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, prepararás la escena agregando el objeto prefabricado del tutorial y configurarás el componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) para controlar la escena.

En la ventana Project (Proyecto), desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpeechServices** > carpeta **Prefabs** y arrastra y coloca el objeto prefabricado **Lunarcom**en la ventana Hierarchy (Jerarquía) para agregarlo a la escena:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Con el objeto **Lunarcom** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) al objeto Lunarcom:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> El componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Con el objeto **Lunarcom** todavía seleccionado, expándelo para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **Terminal** al campo **Terminal** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Terminal para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **ConnectionLight** al campo **Connection Light** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) y el objeto **OutputText** al campo **Output Text** (Texto de salida):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Buttons para mostrar sus objetos secundarios y, a continuación, en la ventana Inspector, expande la lista **Buttons** (Botones), establece su valor de **Size** (Tamaño) en 3 y arrastra los objetos **MicButton**, **SatelliteButton** y **RocketButton** a los campos de **Element** (Elemento) 0, 1 y 2, respectivamente:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Conexión del proyecto de Unity con el recurso de Azure

Para usar los servicios de voz de Azure, debes crear un recurso de Azure y obtener una clave de API para el servicio de voz. Sigue las instrucciones de [Prueba gratuita del servicio Voz](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) y toma nota de la región de servicio (también conocida como ubicación) y la clave de API (también conocida como Key1 o Key2).

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca la sección **Speech SDK Credentials** (Credenciales del SDK de voz) de **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) y configúrala como se indica a continuación:

* En el campo **Speech Service API Key** (Clave de API del servicio Voz), escribe la clave de API (Key1 o Key2)
* En el campo **Speech Service Region** (Región del servicio Voz), escribe tu región de servicio (ubicación) con letras minúsculas y sin espacios.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Uso del reconocimiento de voz para transcribir la voz

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Speech Recognizer (Script)** (Reconocimiento de voz de Lunarcom [script]):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> El componente Lunarcom Speech Recognizer (Script) (Reconocimiento de voz de Lunarcom [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Si ahora entras en el modo de juego, puedes probar el reconocimiento de voz presionando primero el botón del micrófono:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se transcribirá en el panel del terminal:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Has implementado el reconocimiento de voz con tecnología de Azure. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.

En el próximo tutorial, obtendrás información sobre cómo ejecutar comandos con el reconocimiento de voz de Azure.

[Tutorial siguiente: 2. Usar el reconocimiento de voz para ejecutar comandos](mrlearning-speechSDK-ch2.md)
