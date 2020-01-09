---
title: 'Tutoriales de anclaje espacial de Azure: 1. Introducción a los delimitadores espaciales de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334453"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a los anclajes espaciales de Azure

## <a name="overview"></a>Introducción

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
* Complete la sección [creación de un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) de la guía de [Inicio rápido: creación de una aplicación de HoloLens en Unity que usa anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .

>[!IMPORTANT]
>Esta serie de tutoriales requiere <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> y la versión recomendada es Unity 2019.1.14. Esto sustituye a los requisitos de versión de Unity o a las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-the-unity-project"></a>Crear el proyecto de Unity

En esta sección, creará un nuevo proyecto de Unity y lo configurará para Windows Mixed Reality.

1. Cree un proyecto de Unity y asígnele un nombre adecuado, por ejemplo, el _tutorial de anclajes espaciales de Azure_.

2. Configure el proyecto de Unity para Windows Mixed Reality.

    >[!TIP]
    >Para obtener un recordatorio sobre cómo crear un proyecto de Unity y configurarlo para Windows Mixed Reality, puede consultar las secciones creación de un [nuevo proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y [configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) del tutorial [inicialización del proyecto y de la primera aplicación](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que forma parte de la serie de [tutoriales de introducción](mrlearning-base.md) .

## <a name="adding-inbuilt-unity-packages"></a>Agregar paquetes de Unity integrados

En esta sección, agregará recursos y paquetes de Unity integrados que necesitarán los kits de herramientas y los SDK que utilizará en el proyecto.

1. Importe los recursos de TMP Essential.

    >[!NOTE]
    >Estamos agregando este paquete porque lo requiere el kit de herramientas de realidad mixta.

    En el menú de Unity, seleccione **Window** > **TEXTMESHPRO** > **Import tmp Essential Resources**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    En la ventana emergente importar paquete Unity, primero asegúrese de que se seleccionan todos los recursos haciendo clic en el botón **todos** y, a continuación, importe los recursos haciendo clic en el botón **importar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. Instale AR Foundation.

    >[!NOTE]
    >Estamos agregando este paquete porque lo requiere el SDK de anclaje espacial de Azure.

    En el menú de Unity, seleccione **ventana** > **Administrador de paquetes**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    En la ventana del administrador de paquetes, seleccione **ar Foundation** e instale el paquete haciendo clic en el botón **instalar** .

    >[!IMPORTANT]
    >Puede que tarde unos segundos en aparecer en la lista.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>Importar los activos del tutorial

En esta sección, descargará e importará todos los recursos del tutorial.

1. Descargue los recursos.

    * [AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versión 2.0.0)
    * [Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.1.0.1. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.1.0.1. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. Importe los recursos.

    En el menú de Unity, seleccione **recursos** > **importar paquete** > **paquete personalizado.** ...

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    En el paquete de importación... en la ventana emergente, seleccione **AzureSpatialAnchors. unitypackage Tools** y haga clic en el botón **abrir** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    En la ventana emergente importar paquete Unity, primero asegúrese de que se seleccionan todos los recursos haciendo clic en el botón **todos** y, a continuación, importe los recursos haciendo clic en el botón **importar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    Repita estos pasos para importar los paquetes de recursos restantes. Una vez que haya finalizado, la carpeta **assets** del proyecto de Unity debe contener estas subcarpetas.

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>Creación y preparación de la escena

En esta sección, creará y preparará la escena agregando el kit de herramientas de realidad mixta y algunos de los tutoriales Prefabs.

1. Cree una nueva escena.

    En el menú de Unity, seleccione **archivo** > **nueva escena**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    En el menú de Unity, seleccione **archivo** > **Guardar como..** ..

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    En la ventana emergente guardar escena, vaya a la carpeta **escenas** del proyecto, asigne un nombre adecuado a la escena, por ejemplo, _ASATutorialScene_, y guarde la escena haciendo clic en el botón **Guardar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >Puede guardar la escena en cualquier lugar que desee, siempre y cuando se encuentre dentro de la carpeta activos del proyecto. Sin embargo, para mantener el proyecto organizado, normalmente se recomienda guardarlo en la carpeta Scenes del proyecto.

2. Agregue el kit de herramientas de realidad mixta.

    En el menú de Unity, seleccione el **Kit de herramientas de realidad mixta** > **Agregar a la escena y configurar..** ..

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    En la ventana emergente seleccionar MixedRealityToolkitConfigurationProfile, haga clic en **DefaultHoloLens2ConfigurationProfile** para establecerlo como el perfil de configuración MRTK de la escena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    En el menú de Unity, seleccione **archivo** > **Guardar** para guardar la escena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >Puede usar el método abreviado de teclado CTRL + S (comando + S en macOS) para guardar rápidamente la escena mientras está trabajando en este tutorial.

3. Agregue el tutorial Prefabs.

    En el panel Proyecto, vaya a **activos** > **MRTK. Tutoriales. AzureSpatialAnchors** > carpeta **Prefabs** Mientras mantiene presionado el botón CTRL (comando en macOS), haga clic en **ButtonParent**, **DebugWindow**y **ParentAnchor** para seleccionar los tres Prefabs.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    Con los tres Prefabs todavía seleccionados, arrástrelos al panel jerarquía para agregarlos a la escena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto ParentAnchor y, a continuación, hacer zoom ligeramente hacia afuera.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >Si encuentra iconos grandes en la escena, por ejemplo, los iconos ' t ' de gran tamaño que distraen, puede ocultarlos cambiando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">el Gizmos</a> a la posición de apagado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para que funcione la escena

En esta sección, agregará Prefabs y scripts a la escena para crear una serie de botones que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.

1. Configure el componente de botón presionado Hololens Lens 2 (Script).

    En el panel jerarquía, expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    En el panel Inspector, desplácese hacia abajo hasta el componente **Button Hololens Lens 2 (Script)** y agregue un nuevo agente de escucha de eventos al evento **pressed ()** . para ello, haga clic en el icono de **+** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    Con el objeto StartAzureSession todavía seleccionado en el panel jerarquía, haga clic y arrastre el objeto **ParentAnchor** desde el panel jerarquía al campo **ninguno (objeto)** vacío del agente de escucha de eventos que acaba de agregar para hacer que el objeto ParentAnchor escuche los eventos presionados por el botón de este botón.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    Haga clic en la lista desplegable **no función** del mismo agente de escucha de eventos y, a continuación, seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el botón eventos presionados desde este botón.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. Configure el componente interactuable (Script).

    Con el objeto StartAzureSession todavía seleccionado en el panel de jerarquías, en el panel Inspector, desplácese hacia abajo hasta el componente **interactuable (Script)** y repita el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. Configurar los botones restantes

    Para cada uno de los botones restantes, complete el proceso que se describe en los pasos 1 y 2 anteriores para asignar funciones a los eventos Button pressed () y OnClick () que se indican a continuación:

    * Para el objeto **StopAzureSession** , asigne la función **StopAzureSession ()** .
    * Para el objeto **CreateAnchor** , asigne la función **CreateAzureAnchor ()** y, a continuación, arrastre el **ParentAnchor** de nuevo al campo **ninguno (objeto de juego)** vacío.
    * Para **empezar a buscar el objeto delimitador** , asigne la función **FindAzureAnchor ()** .
    * Para eliminar el objeto de **delimitador de Azure** , asigne la función **DeleteAzureAnchor ()** .
    * Para el objeto **eliminar el delimitador local** , asigne la función **RemoveLocalAnchor ()** y, a continuación, arrastre el **ParentAnchor** de nuevo al campo **ninguno (objeto de juego)** vacío.

4. Conexión de la escena al recurso de Azure

    En el panel jerarquía, seleccione el objeto **ParentAnchor** y, en el panel Inspector, desplácese hacia abajo hasta el componente **Administrador de delimitadores espaciales (Script)** .

    Después, en la sección **credenciales** , pegue el identificador y la clave de la cuenta de anclaje espacial en los campos ID. de cuenta de anclaje **espacial** y **anclaje espacial** correspondientes.

    >[!NOTE]
    >Ha creado el identificador de cuenta y la clave de los delimitadores espaciales como parte de los [requisitos previos](mrlearning-asa-ch1.md#prerequisites)de este tutorial.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >Asegúrese de guardar la escena.

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Prueba de los comportamientos básicos de los anclajes espaciales de Azure

Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, es el momento de implementar la aplicación para que pueda experimentar los anclajes espaciales de Azure de primera mano.

1. Agregue capacidades adicionales necesarias.

    En el menú de Unity, seleccione **editar** > **configuración del proyecto...** para abrir el panel de configuración del reproductor.

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    En el panel de configuración del reproductor, seleccione **reproductor** y, a continuación, **configuración de publicación**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    En la **configuración de publicación**, desplácese hacia abajo hasta la sección **capacidades** y compruebe que **SpatialPerception**, que habilitó al crear el proyecto al principio del tutorial, está habilitado. A continuación, habilitó las capacidades **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **cámara web**y **micrófono** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. Implemente la aplicación en HoloLens 2.

    >[!TIP]
    >Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las secciones [compilar la aplicación en el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) del tutorial [inicialización del proyecto y la primera aplicación](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que forma parte de la serie de [tutoriales de introducción](mrlearning-base.md) .

3. Ejecute la aplicación y siga las instrucciones de la aplicación.

    >[!CAUTION]
    >Los delimitadores espaciales de Azure usan Internet para guardar y cargar los datos de delimitador, por lo que debe asegurarse de que el dispositivo está conectado a Internet.

    Cuando la aplicación se ejecuta en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de **instrucciones del módulo de delimitador espacial de Azure** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>Delimitar una experiencia

En las secciones anteriores, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. Usamos un cubo para representar y visualizar el objeto de juego primario con el delimitador adjunto. En esta sección, aprenderá a anclar una experiencia completa colocándolo como un elemento secundario del objeto ParentAnchor.

1. Agregue la experiencia del selector de Rocket.

    En el panel Proyecto, vaya a **activos** > **MRTK. Tutoriales. GettingStarted** > carpeta **Prefabs** y seleccione **Rocket Launcher_Complete** recurso prefabricado.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    Con el Rocket Launcher_Complete recurso prefabricado todavía seleccionado, arrástrelo sobre el objeto **ParentAnchor** en el panel jerarquía para convertirlo en un elemento secundario del objeto ParentAnchor.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. Cambie la posición de la experiencia del selector de Rocket.

    Mueva el módulo **Rocket Launcher_Complete** objeto para que el **ParentAnchor** (el cubo) siga expuesto.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    En la aplicación, los usuarios ahora pueden volver a colocar toda la experiencia del selector de Rocket moviendo el cubo.

    >[!TIP]
    >Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (por ejemplo, el cubo que se usa en este tutorial), el uso de un botón para alternar un rectángulo de selección que rodea la experiencia, el uso de la posición y la rotación. Gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. En esta lección se proporcionan varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar delimitadores de Azure en un único dispositivo.

En la siguiente lección, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, y cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial.

[Lección siguiente: 2. guardar, recuperar y compartir anclajes espaciales de Azure](mrlearning-asa-ch2.md)
