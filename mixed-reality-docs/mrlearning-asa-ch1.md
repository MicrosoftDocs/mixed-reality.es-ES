---
title: 'Tutoriales sobre Azure Spatial Anchors: 1. Introducción a Azure Spatial Anchors'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2a171d601d094375a56734e8d7890c9d3e17c887
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866915"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a Azure Spatial Anchors

## <a name="overview"></a>Introducción

Esta es la segunda serie de los tutoriales de HoloLens 2. En esta serie de tutoriales de cuatro partes, aprenderás los aspectos básicos de Azure Spatial Anchors.

En este primer tutorial, [Introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md), explorarás los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar anclajes de Azure en un único dispositivo.

En el segundo tutorial, [Guardar, recuperar y compartir Azure Spatial Anchors](mrlearning-asa-ch2.md), aprenderás a guardar Azure Spatial Anchors en varias sesiones de aplicación al guardar la información de anclaje en el almacenamiento de HoloLens 2 y a compartir esta información en otros dispositivos para alinear el anclaje en varios dispositivos.

En el tercer tutorial, [Mostrar comentarios de Azure Spatial Anchors](mrlearning-asa-ch3.md), aprenderás a proporcionar a los usuarios comentarios sobre los eventos y estados de anclaje al usar Azure Spatial Anchors.

En el cuarto tutorial, [Azure Spatial Anchors para iOS y Android](mrlearning-asa-ch4.md), aprenderás a compilar e implementar tu proyecto en dispositivos iOS y Android.

## <a name="objectives"></a>Objetivos

* Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2
* Crear, cargar y descargar anclajes espaciales

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado la serie de [tutoriales de introducción](mrlearning-base.md), es recomendable que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado
* Completa la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación HoloLens en Unity que use Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Si piensas implementar en Android
    * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS
    * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de Android agregado
* Si piensas implementar en iOS
    * Un equipo macOS que tenga instalada la versión más reciente de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
    * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS
    * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de iOS agregado

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-the-unity-project"></a>Creación del proyecto de Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:

1. [Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*

2. [Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).

3. [Importar recursos de TextMesh Pro Essential](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurar el proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *AzureSpatialAnchors*

A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

> [!CAUTION]
> Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.

## <a name="adding-inbuilt-unity-packages"></a>Adición de paquetes de Unity integrados
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

En esta sección, instalarás el paquete integrado de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que importarás en la siguiente sección.

En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Puede que el paquete de AR Foundation tarde unos segundos en aparecer en la lista.

En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation** e instala el paquete haciendo clic en el botón **Instalar**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creación y preparación de la escena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

Desde la ventana Proyecto, desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Objetos prefabricados). Mientras mantienes presionado el botón CTRL, haz clic en **ButtonParent**, **DebugWindow**, **Instructions** y **ParentAnchor** para seleccionar los cuatro objetos prefabricados:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Con los cuatro objetos prefabricados aún seleccionados, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Para centrarte en los objetos de la escena, puedes hacer doble clic en el objeto ParentAnchor y, a continuación, volver a alejarte ligeramente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Si te molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puedes ocultarlos. Para hacerlo, desactiva los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, agregarás scripts a la escena para crear una serie de eventos de botón que muestran los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Configurar el componente Pressable Button Holo Lens 2 (Script) (Botón presionable de HoloLens 2 [script])

En la ventana Hierarchy (Jerarquía), expande el objeto **ButtonParent** y selecciona el primer objeto secundario denominado **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

En la ventana Inspector, busca el componente **Pressable Button Holo Lens 2 (Script)** (Botón presionable de HoloLens 2 [script]) y agrega un nuevo cliente de escucha de eventos al evento **Button Pressed ()** (Botón presionado []). Para hacerlo, haz clic en el icono **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Con el objeto StartAzureSession aún seleccionado en la ventana Hierarchy (Jerarquía), haz clic en el objeto **ParentAnchor** y arrástralo desde la ventana Hierarchy (Jerarquía) al campo **None (Object)** (Ninguno [objeto]) del cliente de escucha de eventos que acabas de agregar para que el objeto ParentAnchor escuche los eventos de botón presionado de este botón:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Haz clic en la lista desplegable **No Function** (Ninguna función) del mismo cliente de escucha de eventos y, a continuación, selecciona **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el evento de botón presionado desde este botón:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Configurar el componente Interactable (Script) (Interactuable [script])

Con el objeto StartAzureSession todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, busca el componente **Interactable (Script)** (Interactuable [script]) y repite el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Configurar los botones restantes

Para cada uno de los botones restantes, completa el proceso descrito en los pasos 1 y 2 anteriores para asignar funciones a los eventos **Button Pressed ()** (Botón presionado []) y **OnClick ()** :

* Para el objeto **StopAzureSession**, asigna la funciónAnchorModuleScript > **StopAzureSession ()** .
* Para el objeto **CreateAzureAnchor**, asigna la función AnchorModuleScript > **CreateAzureAnchor ()** .
  * A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]).
* Para el objeto **RemoveLocalAnchor**, asigna la función AnchorModuleScript > **RemoveLocalAnchor ()** .
  * A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]) vacío.
* Para el objeto **FindAzureAnchor**, asigna la función AnchorModuleScript > **FindAzureAnchor ()** .
* Para el objeto **DeleteAzureAnchor**, asigna la función AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Conexión de la escena al recurso de Azure

En la ventana Hierarchy (Jerarquía), selecciona el objeto **ParentAnchor** y, en la ventana Inspector, desplázate hacia abajo hasta el componente **Spatial Anchor Manager (Script)** (Administrador del anclaje espacial [script]).

A continuación, en la sección **Credentials** (Credenciales), pega el identificador y la clave de la cuenta de Spatial Anchors, que creaste como parte de los [Requisitos previos](mrlearning-asa-ch1.md#prerequisites) de este tutorial, en los campos **Spatial Anchors Account Id** (Id. de cuenta de Spatial Anchors) y **Spatial Anchors Account Key** (Clave de cuenta de Spatial Anchors):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Prueba de los comportamientos básicos de Azure Spatial Anchors

Ahora que la escena está configurada para mostrar los aspectos básicos de Azure Spatial Anchors, es el momento de implementar la aplicación para que puedas experimentar Azure Spatial Anchors de primera mano.

### <a name="1-add-additional-required-capabilities"></a>1. Agregar las funcionalidades adicionales necesarias

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

En la ventana Player Settings (Configuración del jugador), selecciona **Player** (Jugador) y, a continuación, **Publishing Settings** (Configuración de publicación):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén activadas. A continuación, habilita las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** y **Webcam**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Implementar la aplicación en HoloLens 2

Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puedes consultar las instrucciones de [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación

> [!CAUTION]
> Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debes asegurarte de que el dispositivo está conectado a Internet.

Cuando la aplicación se ejecute en el dispositivo, sigue las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Anclaje de una experiencia

En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors. Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto. En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Incorporación de la experiencia del lanzacohetes

En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher) y selecciona el objeto prefabricado **RocketLauncher_Complete**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Con el objeto prefabricado RocketLauncher_Complete todavía seleccionado, arrástralo sobre el objeto **ParentAnchor** en la ventana Hierarchy (Jerarquía) para convertirlo en un elemento secundario del objeto ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Cambio de posición de la experiencia del lanzacohetes

Coloca, gira y escala el objeto **RocketLauncher_Complete** a una escala y orientación adecuadas, al mismo tiempo que se garantiza que el objeto **ParentAnchor** sigue expuesto; por ejemplo:

* Transforma el valor de **Position** (Posición) X = 0, Y = 0, Z = 3,75
* Transforma el valor de **Rotation** (Rotación) X = 0, Y = 90, Z = 0
* Transforma el valor de **Scale** (Escala) X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

Ahora, en la aplicación, los usuarios pueden mover el cubo para cambiar la posición de la experiencia del lanzacohetes por completo.

> [!TIP]
> Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el cuadro de límite que rodea la experiencia, el uso de gizmos de posición y rotación, etc.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors. El tutorial te ha proporcionado varios botones que te permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors y crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.

En la siguiente lección, aprenderás a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.

[Siguiente lección: 2. Guardado, recuperación y uso compartido de Azure Spatial Anchors](mrlearning-asa-ch2.md)
