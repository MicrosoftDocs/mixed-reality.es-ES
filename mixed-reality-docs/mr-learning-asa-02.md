---
title: 'Tutoriales sobre Azure Spatial Anchors: 2. Introducción a Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376497"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introducción a Azure Spatial Anchors

## <a name="overview"></a>Introducción

En este tutorial, explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors, y para crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.

## <a name="objectives"></a>Objetivos

* Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2
* Aprender a crear anclajes espaciales y a capturarlos desde Azure

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*
1. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)
1. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Importar Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Configurar el proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project)
1. [Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, *AzureSpatialAnchors*

A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:

1. Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.
1. Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Occlusion** (Oclusión).

## <a name="installing-inbuilt-unity-packages"></a>Instalación de paquetes de Unity integrados

En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versión 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** y, a continuación, haga clic y arrastre los siguientes objetos prefabricados a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:

* Objeto prefabricado **ButtonParent**
* Objeto prefabricado **DebugWindow**
* Objeto prefabricado **Instructions**
* Objeto prefabricado **ParentAnchor**

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Si le molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, desactive los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>, como se muestra en la imagen anterior.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestren los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.

En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **StopAzureSession**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StopAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **CreateAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **CreateAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función CreateAzureAnchor ().

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **RemoveLocalAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **RemoveLocalAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función RemoveLocalAnchor ().

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **FindAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **FindAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **DeleteAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **DeleteAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Conexión de la escena al recurso de Azure

En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** . Configure la sección **Credentials** (Credenciales) con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mr-learning-asa-01.md#prerequisites) de esta serie de tutoriales:

* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.
* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Prueba de los comportamientos básicos de Azure Spatial Anchors

Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad de Azure Spatial Anchors, debe compilar el proyecto e implementar la aplicación en el dispositivo.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Cuando la aplicación se ejecute en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:

1. Mueva el cubo a una ubicación diferente.
1. Inicie una sesión de Azure.
1. Cree un anclaje de Azure (se crea un anclaje en la ubicación del cubo).
1. Detenga la sesión de Azure.
1. Quite el anclaje local (permite que el usuario mueva el cubo).
1. Mueva el cubo a otro lugar.
1. Inicie una sesión de Azure.
1. Busque el anclaje de Azure (posiciona el cubo en la ubicación del paso 3).
1. Elimine el anclaje de Azure.
1. Detenga la sesión de Azure.

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.

## <a name="anchoring-an-experience"></a>Anclaje de una experiencia

En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors. Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto. En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, configure los componentes **Transform** de la manera siguiente:

* Cambie **Scale X** (Escala X) a 1.1.
* Cambie **Scale Z** (Escala Z) a 1.1.

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** > **Rover** y haga clic y arrastre el objeto prefabricado **RoverExplorer_Complete** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

Con el objeto RoverModule_Complete recién agregado todavía seleccionado en la ventana Hierarchy (Jerarquía), arrástralo sobre el objeto **ParentAnchor** para convertirlo en un elemento secundario del objeto ParentAnchor:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

Si vuelve a compilar el proyecto e implementar la aplicación en el dispositivo, ahora podrá cambiar la posición de toda la experiencia del explorador de róver moviendo el cubo cuyo tamaño se ha cambiado.

> [!TIP]
> Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el cuadro de límite que rodea la experiencia, el uso de gizmos de posición y rotación, etc.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors. El tutorial le ha proporcionado varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors. Además de crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.

En el siguiente tutorial, aprenderá a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.

[Tutorial siguiente: 3. Guardado, recuperación y uso compartido de Azure Spatial Anchors](mr-learning-asa-03.md)
