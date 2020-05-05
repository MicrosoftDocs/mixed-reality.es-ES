---
title: 'Tutoriales sobre las funcionalidades multiusuario: 1. Configuración de Photon Unity Networking'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610738"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configuración de Photon Unity Networking

## <a name="overview"></a>Introducción

En este tutorial, aprenderás a prepararte para la creación de una experiencia compartida con Photon Unity Networking (PUN). Photon es una de las diversas opciones de redes disponibles para que los desarrolladores de Mixed Reality creen experiencias compartidas. Obtendrás información sobre cómo crear una aplicación de Photon PUN, importar recursos de Photon PUN en el proyecto de Unity y conectar el proyecto de Unity a la aplicación de Photon PUN.

## <a name="objectives"></a>Objetivos

* Información sobre cómo crear una aplicación de Photon PUN
* Información sobre cómo buscar e importar los recursos de Photon PUN
* Información sobre cómo conectar el proyecto de Unity a la aplicación de Photon PUN

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado los [tutoriales de introducción](mrlearning-base.md) ni los [tutoriales de Azure Spatial Anchors](mrlearning-asa-ch1.md), te recomendamos que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado
* Completa la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:

1. [Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*

2. [Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).

3. [Importar recursos de TextMesh Pro Essential](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurar el proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *MultiUserCapabilities*

A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización del reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

> [!CAUTION]
> Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.

## <a name="configuring-the-capabilities"></a>Configuración de las funcionalidades

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén habilitadas. A continuación, habilita las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** y **RemovableStorage**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>Adición de paquetes de Unity integrados
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

En esta sección, instalarás el paquete integrado de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que importarás en la siguiente sección.

En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> Puede que el paquete de AR Foundation tarde unos segundos en aparecer en la lista.

En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation** e instala el paquete haciendo clic en el botón **Instalar**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> Después de importar el paquete de recursos del tutorial de MultiUserCapabilities, verás varios errores con el código [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) en la ventana de la consola en los que se indicará que falta el tipo o el espacio de nombres. Este comportamiento es el esperado y se resolverá en la sección siguiente cuando importes los recursos de Photon.

## <a name="importing-the-photon-assets"></a>Importación de recursos de Photon

En esta sección, importarás los recursos de Photon Unity Network (PUN) del almacén de recursos de Unity.

En el menú de Unity, selecciona **Ventana** > **Asset Store** (Almacén de recursos) para abrir la ventana del almacén de recursos, busca y selecciona **PUN 2 - FREE** de Exit Games y, a continuación, haz clic en el botón **Descargar** para descargar el paquete de recursos en tu cuenta de Unity:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

Una vez completada la descarga, haz clic en el botón **Importar** para abrir la ventana Import Unity Package (Importar paquete de Unity):

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Una vez que Unity haya completado el proceso de importación, se mostrará la ventana Pun Wizard (Asistente para PUN) con el menú de configuración de PUN cargado. Por ahora, puedes omitir o cerrar esta ventana:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Configuración de Photon

En esta sección, crearás una cuenta de Photon, si aún no tienes ninguna, y crearás una nueva aplicación de PUN.

Ve al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">panel</a> de Photon e inicia sesión si ya tienes una cuenta que quieras usar. De lo contrario, haz clic en el vínculo **Crear una** y sigue las instrucciones para registrar una cuenta nueva:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

Una vez que hayas iniciado sesión, haz clic en el botón **Crear una nueva aplicación**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

En la página Crear una nueva aplicación, escribe los valores siguientes:

* En Photon Type (Tipo de Photon), selecciona Photon PUN.
* En Nombre, escribe un nombre adecuado, por ejemplo, _Tutoriales de MRTK_.
* En Descripción, puedes escribir una descripción adecuada.
* En URL, deja el campo vacío.

A continuación, haz clic en el botón **Crear** para crear la nueva aplicación.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Una vez que Photon haya finalizado el proceso de creación, la nueva aplicación de PUN aparecerá en el panel:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Conexión del proyecto de Unity con la aplicación de PUN

En esta sección, conectarás el proyecto de Unity a la aplicación de PUN que creaste en la sección anterior.

En el panel de Photon, haz clic en el campo **Id. de la aplicación** para mostrar el identificador de la aplicación y, a continuación, cópialo en el portapapeles:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

En el menú de Unity, selecciona **Ventana** > **Photon Unity Networking** > **Pun Wizard** (Asistente para PUN) para abrir la ventana del asistente para PUN, haz clic en el botón **Proyecto de instalación** para abrir el menú de configuración de PUN y configúralo de la siguiente manera:

* En el campo **AppId or Email** (Id. de la aplicación o correo electrónico), pega el identificador de la aplicación de PUN que copiaste en el paso anterior

A continuación, haz clic en el botón **Proyecto de instalación** para aplicar el id. de la aplicación:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Una vez que Unity termine el proceso de configuración de PUN, se mostrará el mensaje **Listo** en el menú de configuración de PUN. Así mismo, se seleccionará automáticamente el recurso **PhotonServerSettings** en la ventana Proyecto para que sus propiedades se muestren en la ventana Inspector:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

Has creado correctamente una aplicación de Photon PUN y la has conectado al proyecto de Unity. El siguiente paso consiste en permitir las conexiones con otros usuarios para que varios usuarios puedan verse entre sí.

[Tutorial siguiente: 2. Conexión de varios usuarios](mrlearning-sharing(photon)-ch2.md)
