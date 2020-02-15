---
title: 'Tutoriales de anclaje espacial de Azure: 1. Introducción a los delimitadores espaciales de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250870"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a los anclajes espaciales de Azure

## <a name="overview"></a>Información general

Esta es la segunda serie de los tutoriales de HoloLens 2. En esta serie de tutoriales de tres partes, conocerá los aspectos básicos de los delimitadores espaciales de Azure.

En este primer tutorial, [Introducción a los anclajes espaciales de Azure](mrlearning-asa-ch1.md), explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar los delimitadores de Azure en un único dispositivo.

En el segundo tutorial, [guardado, recuperación y uso compartido de los anclajes espaciales de Azure](mrlearning-asa-ch2.md), aprenderá a guardar los anclajes espaciales de Azure en varias sesiones de la aplicación guardando la información del delimitador en el almacenamiento de HoloLens 2 y compartiendo esta información de delimitador en otros dispositivos para una alineación de delimitador de varios dispositivos.

En el tercer tutorial, en el que se [muestran los comentarios del delimitador espacial de Azure](mrlearning-asa-ch3.md), aprenderá a proporcionar a los usuarios comentarios sobre los eventos y Estados de delimitador al usar delimitadores espaciales de Azure.

## <a name="objectives"></a>Objetivos

* Conozca los aspectos básicos del desarrollo con los anclajes espaciales de Azure para HoloLens 2
* Crear, cargar y descargar anclajes espaciales

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no ha completado la serie de [tutoriales de introducción](mrlearning-base.md) , se recomienda que complete los tutoriales en primer lugar.

* Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Cierta capacidad C# de programación básica
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2. X instalado y el módulo de compatibilidad de compilación plataforma universal de Windows agregado
* Complete la sección [creación de un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) de la guía de [Inicio rápido: creación de una aplicación de HoloLens en Unity que usa anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2. X. Esto sustituye a los requisitos de versión de Unity o a las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-the-unity-project"></a>Crear el proyecto de Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

En esta sección, creará un nuevo proyecto de Unity y lo preparará para el desarrollo de MRTK. Para ello, siga [las instrucciones de](mrlearning-base-ch1.md#build-your-application-to-your-device) [inicialización del proyecto y de la primera aplicación](mrlearning-base-ch1.md), sin incluir los siguientes pasos:

1. [Cree un nuevo proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asígnele un nombre adecuado, por ejemplo, *tutoriales de MRTK*.

2. [Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importar recursos esenciales de TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configuración del proyecto de Unity para el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Agregue el kit de herramientas de realidad mixta a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y proporcione a la escena un nombre adecuado, por ejemplo, *AzureSpatialAnchors*

> [!CAUTION]
> Como se mencionó en el [proyecto de configuración del proyecto de Unity para las instrucciones del kit de herramientas de realidad mixta](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas anteriormente, es posible que MSBuild para Unity no admita todos los SDK que va a usar y puede ser difícil de deshabilitar una vez que se ha habilitado. Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.

## <a name="adding-inbuilt-unity-packages"></a>Agregar paquetes de Unity integrados
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

En esta sección, instalará el paquete de AR Foundation integrado de Unity porque lo requiere el SDK de anclaje espacial de Azure que se importará en la sección siguiente.

En el menú de Unity, seleccione **ventana** > **Administrador de paquetes**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Puede que tarde unos segundos en aparecer en la lista.

En la ventana del administrador de paquetes, seleccione **ar Foundation** e instale el paquete haciendo clic en el botón **instalar** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importar los activos del tutorial

Descargue e **importe** los siguientes paquetes personalizados **de Unity en el orden en que**aparecen:

* [AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)
* [MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.2.0.1. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.2.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, puede consultar las instrucciones para [importar el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

Después de haber importado los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creación y preparación de la escena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

En esta sección, va a preparar la escena agregando algunos de los tutoriales de Prefabs.

En la ventana del proyecto, vaya a **activos** > **MRTK. Tutoriales. AzureSpatialAnchors** > carpeta **Prefabs** Mientras mantiene presionado el botón CTRL, haga clic en **ButtonParent**, **DebugWindow**, **instrucciones**y **ParentAnchor** para seleccionar los cuatro Prefabs:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Con las cuatro Prefabs todavía seleccionadas, arrástrelas a la ventana de jerarquía para agregarlas a la escena:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto ParentAnchor y, a continuación, hacer zoom ligeramente hacia afuera:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Si encuentra iconos grandes en la escena, por ejemplo, los iconos ' t ' de gran tamaño que distraen, puede ocultarlos cambiando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">el Gizmos</a> a la posición de apagado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para que funcione la escena

En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. configurar el componente de botón presionado Hololens Lens 2 (Script)

En la ventana jerarquía, expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

En la ventana del inspector, busque el componente del botón que se ha **presionado Hololens Lens 2 (Script)** y agregue un nuevo agente de escucha de eventos al evento **pressed ()** . para ello, haga clic en el icono de **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Con el objeto StartAzureSession todavía seleccionado en la ventana de jerarquía, haga clic en el objeto **ParentAnchor** de la ventana de la jerarquía y arrástrelo hasta el campo no vacío **(objeto)** del agente de escucha de eventos que acaba de agregar para hacer que el objeto ParentAnchor escuche los eventos presionados por el botón de este botón:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Haga clic en la lista desplegable **no función** del mismo agente de escucha de eventos y, a continuación, seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el botón eventos presionados desde este botón:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. configurar el componente interactuable (Script)

Con el objeto StartAzureSession todavía seleccionado en la ventana de la jerarquía, en la ventana del inspector, busque el componente **interactuable (Script)** y repita el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. configurar los botones restantes

Para cada uno de los botones restantes, complete el proceso que se describe en los pasos 1 y 2 anteriores para asignar funciones a los eventos **Button pressed ()** y **OnClick ()** :

* Para el objeto **StopAzureSession** , asigne la función AnchorModuleScript > **StopAzureSession ()** .
* Para el objeto **CreateAzureAnchor** , asigne la función AnchorModuleScript > **CreateAzureAnchor ()** .
  * a continuación, arrastre **ParentAnchor** de nuevo al campo vacío **ninguno (objeto de juego)** .
* Para el objeto **RemoveLocalAnchor** , asigne la función AnchorModuleScript > **RemoveLocalAnchor ()** .
  * a continuación, arrastre **ParentAnchor** de nuevo al campo vacío **ninguno (objeto de juego)** .
* Para el objeto **FindAzureAnchor** , asigne la función AnchorModuleScript > **FindAzureAnchor ()** .
* Para el objeto **DeleteAzureAnchor** , asigne la función AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. conectar la escena al recurso de Azure

En la ventana jerarquía, seleccione el objeto **ParentAnchor** y, en la ventana del inspector, desplácese hacia abajo hasta el componente **Administrador de delimitadores espaciales (Script)** .

A continuación, en la sección **credenciales** , pegue el identificador y la clave de la cuenta de anclaje espacial que creó como parte de los [requisitos previos](mrlearning-asa-ch1.md#prerequisites)de este tutorial, en los campos de clave de cuenta de los **delimitadores** espaciales y los **delimitadores espaciales** correspondientes:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Prueba de los comportamientos básicos de los anclajes espaciales de Azure

Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, es el momento de implementar la aplicación para que pueda experimentar los anclajes espaciales de Azure de primera mano.

### <a name="1-add-additional-required-capabilities"></a>1. agregar funcionalidades adicionales necesarias

En el menú de Unity, seleccione **editar** > **configuración del proyecto...** para abrir la ventana Configuración del reproductor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

En la ventana Configuración del reproductor, seleccione **reproductor** y, a continuación, **configuración de publicación**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

En la **configuración de publicación**, desplácese hacia abajo hasta la sección **capacidades** y compruebe que las capacidades **InternetClient**, **Microphone**y **SpatialPerception** , que ha habilitado al crear el proyecto al principio del tutorial, están habilitadas. A continuación, habilita las funcionalidades de **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**y **Webcam** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. implementación de la aplicación en HoloLens 2

Los anclajes espaciales de Azure no se pueden ejecutar en Unity, por lo que para probar la funcionalidad de los anclajes espaciales de Azure, debe implementar el proyecto en el dispositivo.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones [compilar la aplicación en el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) .

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Ejecute la aplicación en HoloLens 2 y siga las instrucciones de la aplicación.

> [!CAUTION]
> Los delimitadores espaciales de Azure usan Internet para guardar y cargar los datos de delimitador, por lo que debe asegurarse de que el dispositivo está conectado a Internet.

Cuando la aplicación se ejecuta en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de delimitador espacial de Azure:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Delimitar una experiencia

En las secciones anteriores, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. Usamos un cubo para representar y visualizar el objeto de juego primario con el delimitador adjunto. En esta sección, aprenderá a anclar una experiencia completa colocándolo como un elemento secundario del objeto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. agregar la experiencia del selector de Rocket

En la ventana de proyecto, navegue a los **recursos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs** > carpeta **RocketLauncher** y seleccione el **RocketLauncher_Complete** recurso prefabricado:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Con el RocketLauncher_Complete recurso prefabricado todavía seleccionado, arrástrelo sobre el objeto **ParentAnchor** de la ventana jerarquía para convertirlo en un elemento secundario del objeto ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. cambiar la posición de la experiencia del selector de Rocket

Coloque, gire y escale el objeto de **RocketLauncher_Complete** a una escala y orientación adecuadas, y asegúrese también de que el objeto **ParentAnchor** todavía está expuesto, por ejemplo:

* **Posición** de transformación X = 1, Y = 0, Z = 3,75
* Transformación de **giro** X = 0, Y = 90, Z = 0
* **Escala** de transformación X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

En la aplicación, los usuarios ahora pueden volver a colocar toda la experiencia del selector de Rocket moviendo el cubo.

> [!TIP]
> Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (por ejemplo, el cubo que se usa en este tutorial), el uso de un botón para alternar un rectángulo de selección que rodea la experiencia, el uso de la posición y la rotación. Gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. El tutorial le proporcionó varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de anclajes espaciales de Azure y crear, cargar y descargar los anclajes espaciales de Azure en un único dispositivo.

En la siguiente lección, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, y cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial.

[Lección siguiente: 2. guardar, recuperar y compartir anclajes espaciales de Azure](mrlearning-asa-ch2.md)
