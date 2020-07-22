---
title: 'Tutoriales de la nube de Azure: 1. Servicios en la nube de Azure para HoloLens 2'
description: Complete este curso para aprender a implementar distintos servicios de Azure con la aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, realidad mixta, unity, tutorial, hololens, hololens 2, azure blob storage, azure table storage, azure spatial anchors, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306005"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Servicios en la nube de Azure para HoloLens 2

## <a name="overview"></a>Introducción

Le damos la bienvenida a esta serie de tutoriales centrados en incorporar **servicios en la nube de Azure** a una aplicación de **HoloLens 2**. En esta serie de tutoriales de cinco partes, aprenderá a integrar varios **servicios en la nube de Azure** en un proyecto de **Unity** para **HoloLens 2**. Con cada capítulo consecutivo, agregará nuevos **servicios en la nube de Azure** para ampliar las características de la aplicación y la experiencia del usuario, al tiempo que le enseñará los aspectos básicos de cada **servicio en la nube de Azure**.

> [!NOTE]
> Esta serie de tutoriales se centrará en el **HoloLens 2**, pero, debido a la naturaleza multiplataforma de Unity, la mayoría de los aprendizajes también se aplicarán a las aplicaciones de escritorio y smartphone.

En este primer tutorial, [Introducción a los servicios en la nube de Azure para HoloLens 2](mr-learning-azure-01.md), se comienza por explicar los objetivos de la aplicación, se presenta brevemente cada servicio en la nube de Azure y se configura el proyecto de Unity.

En el segundo tutorial, [Integración de Azure Storage](mr-learning-azure-02.md), comienza por integrar Azure Storage como solución de persistencia para la aplicación de demostración, aprende las diferencias entre Blob Storage y Table Storage, prepara los recursos necesarios del proyecto, configura la escena y verifica las operaciones de lectura, actualización y eliminación de datos.

Siguiendo con el tercer tutorial, [Integración de Azure Custom Vision](mr-learning-azure-03.md), usará Azure Custom Vision para entrenar y detectar imágenes en la aplicación de HoloLens 2. El capítulo comienza con la configuración de su propio recurso de Azure Custom Vision, la preparación de los componentes de la escena y la puesta en acción mediante el entrenamiento y la detección de sus propias imágenes desde dentro de la aplicación.

A continuación, avanzará al cuarto tutorial, [Integración de Azure Spatial Anchors](mr-learning-azure-04.md), donde explorará el servicio de Azure Spatial Anchors para guardar y buscar ubicaciones, conocer los conceptos principales, preparar los recursos necesarios, configurar la escena y empezar a usar la nueva característica en la aplicación.

Con el quinto tutorial, [Integración de Azure Bot Service con LUIS](mr-learning-azure-05.md), termina dando a la aplicación un nuevo método de interacción con el usuario: el lenguaje natural. Esta característica se logrará mediante Azure Bot Framework junto con Language Understanding (LUIS). Este último capítulo le enseña los aspectos básicos de Azure Bot Service y, para acelerar el proceso, utilizará Bot Framework Composer como solución de código cero. Una vez que cree el bot, lo integrará en la escena y lo ejecutará con la fase final de la aplicación de HoloLens 2.

## <a name="application-goals"></a>Objetivos de la aplicación

En esta serie de tutoriales, compilará una aplicación de **HoloLens 2** que puede detectar objetos a partir de imágenes y encontrar su ubicación espacial. Para establecer un idioma de dominio, desde ahora llamaremos a estas entidades **objeto con seguimiento**.
El usuario puede crear un **objeto con seguimiento** para asociar un conjunto de imágenes a través de una visión de equipo o una ubicación espacial, o ambas. Todos los datos deben persistir en la nube. Además, algunos aspectos de la aplicación se controlarán de manera opcional mediante un lenguaje natural asistido a través de un bot.

### <a name="features"></a>Características

* Administración básica de datos e imágenes
* Entrenamiento y detección de imágenes
* Almacenamiento de una ubicación espacial y orientación hacia ella
* Asistente para bot para usar algunas características a través de un lenguaje natural

## <a name="azure-cloud-services"></a>Servicios en la nube de Azure

Para resolver las características necesarias para la aplicación, utilizará estos **servicios en la nube de Azure**:

### <a name="azure-storage"></a>Azure Storage

Usará [Azure Storage](https://azure.microsoft.com/services/storage/) de la solución de persistencia. Le permite almacenar datos en una tabla y cargar archivos binarios de gran tamaño, como imágenes.

### <a name="azure-custom-vision"></a>Azure Custom Vision

Con [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (parte de [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) puede asociar a *objetos con seguimiento* un conjunto de imágenes, entrenar un modelo de aprendizaje automático con el conjunto y detectar el *objeto con seguimiento*.

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Para almacenar la ubicación de un *objeto con seguimiento* y proporcionar una indicación guiada para encontrarla, use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Azure Bot Service

La aplicación se controla principalmente por una UI tradicional, por lo que se usa [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) para agregar alto de personalidad y actuar como nuevo método de interacción.

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado la serie de [tutoriales de introducción](mr-learning-base-01.md), es recomendable que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* Una cámara web conectada si desea probar desde el editor de Unity
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

> [!CAUTION]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *Azure Cloud Tutorials*
2. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Importar Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Configurar el proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project)
6. [Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar un nombre adecuado a la escena; por ejemplo, *AzureCloudServices*

A continuación, sigue las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

## <a name="installing-inbuilt-unity-packages"></a>Instalación de paquetes de Unity integrados

En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [Azure Storage para Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Azure Spatial Anchors](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creación y preparación de la escena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**. Mientras mantiene presionado la tecla CTRL, haga clic en **SceneController**, **RootMenu** y **DataManager** para seleccionar los tres objetos prefabricados:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (prefab)** contiene dos scripts, **SceneController (script)** y **UnityDispatcher (script)** . El componente de script **SceneController** contiene varias funciones de la experiencia del usuario y facilita la funcionalidad de captura de fotos, mientras que **UnityDispatcher** es una clase auxiliar para permitir las acciones de ejecución en el subproceso principal de Unity.

**RootMenu (prefab)** es el objeto prefabricado de la UI principal que contiene todas las ventanas de la UI que están conectadas entre sí a través de varios componentes de script pequeños, y controlan el flujo general de la experiencia de usuario en la aplicación.

**DataManager (prefab)** es responsable de comunicarse con Azure Storage y se explicará con más detalle en el siguiente tutorial.

Ahora, con los tres objetos prefabricados aún seleccionados, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **RootMenu** y, a continuación, volver a alejarse ligeramente:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Si te molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puedes ocultarlos. Para hacerlo, desactiva los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>.

## <a name="configuring-the-scene"></a>Configuración de la escena

En esta sección, conectará *SceneManager*, *SceneManager* y *RootMenu* juntos para tener una escena en funcionamiento preparada para el siguiente tutorial, [Integración de Azure Storage](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Conexión de los objetos

En la ventana Hierarchy (Jerarquía), seleccione el objeto **DataManager**.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

En la ventana Inspector, busque el componente **DataManager (script)** y verá un espacio vacío en el evento **On Data Manager Ready ()** . Ahora, en la ventana Hierarchy (Jerarquía), arrastre el objeto **SceneController** al evento **On Data Manager Ready ()** .

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Observará que el menú desplegable del evento se ha activado, haga clic en el menú desplegable y navegue a **SceneController** y, en el submenú, seleccione la opción **Init ()** :

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **SceneController**, en Inspector encontrará el componente **SceneController** (script).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Verá que hay varios campos sin rellenar; vamos a cambiar eso. Mueva el objeto **DataManager** de Hierarchy (Jerarquía) al campo *Data Manager* (Administrador de datos), y mueva el GameObject **RootMenu** de Hierarchy al campo *Main Menu* (Menú principal).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Ahora la escena está lista para los próximos tutoriales. No olvide guardarla en el proyecto.

## <a name="prepare-project-build-pipeline"></a>Preparación de la canalización de compilación del proyecto

Aunque el proyecto todavía tiene que rellenarse con contenido, debe realizar algunos preparativos para que el proyecto esté listo para compilar para **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Agregar las funcionalidades adicionales necesarias

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** (Jugador) y, a continuación, **Publishing Settings** (Configuración de publicación):

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

En **Publishing Settings** (Configuración de publicación), desplácese hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitó al crear el proyecto al principio del tutorial estén habilitadas. A continuación, habilite las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** y **Webcam**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Implementar la aplicación en HoloLens 2

No todas las características que usará en esta serie de tutoriales pueden ejecutarse en el editor de Unity, lo que significa que debe estar familiarizado con la implementación de la aplicación en su dispositivo HoloLens 2.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Tutoriales de introducción: Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación

> [!CAUTION]
> Todos los servicios de Azure usan Internet, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.

Cuando la aplicación se esté ejecutando en el dispositivo, acepte el acceso a las siguientes funcionalidades solicitadas:

* Micrófono
* Cámara

Estas funcionalidades son necesarias para que los servicios como *Chat Bot* y *Custom Vision* funcionen correctamente.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, se le ha presentado la serie de tutoriales, ha aprendido sobre las características que va a implementar y cómo los **servicios en la nube de Azure** se asocian a la aplicación de *HoloLens 2*. Agregó los componentes necesarios al proyecto y preparó la escena para esta serie de tutoriales.

En la lección siguiente, usará Azure Storage como solución de persistencia basada en la nube para almacenar datos e imágenes.

[Tutorial siguiente: 2. Integración de Azure Storage](mr-learning-azure-02.md)
