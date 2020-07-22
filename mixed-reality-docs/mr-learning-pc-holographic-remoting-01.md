---
title: 'Tutoriales de comunicación remota holográfica para PC: 1. Introducción a la comunicación remota holográfica para PC'
description: Complete este curso para aprender cómo crear una experiencia de realidad mixta remota del PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306734"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Introducción a la comunicación remota holográfica para PC

## <a name="overview"></a>Introducción

  Le damos la bienvenida a los tutoriales de HoloLens 2. En esta serie de tutoriales de dos partes, aprenderá a crear una demostración de experiencia de realidad mixta, así como a crear una aplicación para PC para la comunicación remota holográfica.

   En este tutorial sobre cómo [crear una experiencia de realidad mixta](mr-learning-pc-holographic-remoting-01.md), aprenderá a crear una experiencia de realidad mixta. Se mostrarán los elementos de la interfaz de usuario, la manipulación de modelos 3D, el recorte de modelos y las características de seguimiento ocular.

  En el segundo tutorial, [Creación de una aplicación de comunicación remota holográfica](mr-learning-pc-holographic-remoting-02.md), aprenderá a crear una aplicación de PC para comunicación remota holográfica. Y a conectarla a HoloLens 2 en cualquier momento, de modo que podrá visualizar contenido 3D en realidad mixta.

## <a name="objectives"></a>Objetivos

* Importar recursos y configurar la escena
* Interacción con hologramas mediante botones y elementos de la interfaz de usuario
* Configurar objetos 3D para la característica de recorte
* Aprender a activar la información sobre herramientas con el seguimiento ocular

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* Conocimientos básicos de programación de C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X montado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

>[RECOMENDADO] Haber completado la serie de tutoriales de introducción o contar con experiencia previa básica en el uso de Unity y MRTK

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.X. Sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*

1. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importar Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Configurar el proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, **PC Holographic Remoting**

A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK para la escena por el perfil **DefaultHoloLens2ConfigurationProfile**. Cambie las opciones de visualización de la malla de reconocimiento espacial a **Oclusión**.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descargue e **importe** el paquete [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).

>[!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Una vez importados los recursos del tutorial, la ventana Proyecto debería tener un aspecto similar al siguiente:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>Configuración y preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

Desde la ventana Proyecto, desplácese hasta **Assets** (Recursos) > **MRTK.Tutorials.PCHolograhicRemoting** > carpeta **Prefabs** (Recursos prefabricados). Mientras mantiene presionado el botón CTRL, haga clic en los seis elementos prefabricados siguientes.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Instrucciones
* ModelParent
* Plataforma

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Arrastre y coloque estos modelos de la carpeta Prefabs en la **ventana Jerarquía**.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **ModelParent** y, a continuación, volver a acercarse ligeramente:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Si le molestan los grandes iconos de la escena, como los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">desactive el menú Gizmos</a>.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, agregará scripts a la escena para crear eventos de botón que muestren los aspectos básicos de la funcionalidad de cambio y recorte de modelos.

### <a name="1-configuring-the-interactable-script-component"></a>1. Configuración del componente Interactable (Script) (Interactivo [script])

En la ventana Jerarquía, expanda el objeto **ButtonParent** y seleccione **NextButton**. En la ventana Inspector, busque el componente **Interactable (Script)** (Interactivo [script]) y haga clic en el icono **+** debajo del evento **OnClick ()** .

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Con el objeto **NextButton** aún seleccionado en la ventana Jerarquía, haga clic en el objeto **ButtonParent** y arrástrelo desde la ventana Jerarquía al campo **None (Object)** (Ninguno [objeto]) del evento que acaba de agregar; de este modo, el objeto ButtonParent escuchará los eventos de clic de este botón:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Haga clic en la lista desplegable **Ninguna función** del mismo evento. A continuación, seleccione **ViewButtonControl** > **NextModel ()** para establecer la función **NextModel ()** como la acción que se desencadenará cuando se activen los eventos de botón presionado de este botón:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Configuración de los botones restantes

Para cada uno de los botones restantes, complete el proceso descrito anteriormente para asignar funciones a los eventos **OnClick ()** :

* Para el objeto PreviousButton, asigne la función **ViewButtonControl** > **PreviousModel ()** .

* En el caso de ClippingButton, seleccione **ToggleButton** > función **ToggleClipping ()** .

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Configuración de los componentes View Button Control (Script) (Ver control de botón [script]) y Toggle Button (Script) (Botón de alternancia [script])

Ahora los botones están configurados para mostrar la funcionalidad de cambio y recorte del modelo. Es el momento de agregar los modelos 3D y los objetos de recorte al script.

Hemos incluido seis modelos 3D distintos para la demostración; expanda el objeto ***ModelParentobject*** para exponer estos modelos 3D.

Con el objeto ButtonParent aún seleccionado en la ventana Jerarquía, en la ventana Inspector, busque el componente **View Button Control (Script)** (Ver control de botón [script]) y expanda la variable **Models**.

En el campo **Size**, escriba el número de modelos 3D que quiere tener en la escena. En este caso, sería seis. Se crearán los campos para agregar nuevos modelos 3D.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Arrastre y coloque cada objeto secundario del objeto ModelParent en dichos campos.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Arrastre y coloque el objeto **ClippingObjects** desde la ventana Jerarquía hasta el campo **Clipping Object** (Objeto de recorte) del componente **Toggle Button (Script)** (Botón de alternancia [script]).
>[!NOTE]
>Permanezca solo en el objeto primario de botón.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

En la ventana Jerarquía, seleccione el elemento prefabricado **ClippingObjects** y habilítelo en la ventana Inspector para activar los objetos de recorte.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Configuración de los objetos de recorte para habilitar la característica de recorte

En esta sección, agregará el representador de objetos secundarios del objeto MarsCuriosityRover a un objeto de recorte individual para mostrar el recorte del modelo MarsCuriosityRover.

En la ventana Jerarquía, expanda el objeto **ClippingObjects** para exponer los tres objetos de recorte diferentes que usará en este proyecto.

Para configurar el objeto **ClippingSphere**, haga clic en él y, en la ventana Inspector, busque el componente **Clipping Sphere (Script)** (Esfera de recorte [script]). Escriba el número de representadores en el campo de tamaño que necesita agregar al modelo 3D. En este caso, agregue 10 objetos secundarios MarsCuriosityRover. De este modo, se crearán campos para agregar los representadores; después, arrastre y coloque los objetos del modelo secundario del objeto MarsCuriosityRover en estos campos.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Siga el mismo proceso y agregue los representadores de objetos secundarios de MarsCuriosityRover a los objetos **ClippingBox** y **ClippingPlane**.

En este tutorial, solo se usará el modelo MarsCuriosityRover como demostración de la característica de recorte. Se agregarán características de recorte a más modelos, se aumentará el tamaño del representador y se agregarán sus representadores de malla individuales.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Configuración del seguimiento ocular para resaltar información sobre herramientas

En esta sección, explorarás cómo habilitar el seguimiento ocular en el proyecto. Por ejemplo, implementará la funcionalidad para resaltar la información sobre herramientas relacionada con las piezas de MarsCuriosityRover cuando las mira, y ocultará dicha información al apartar la mirada.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identificación de los objetos de destino y la información sobre herramientas asociada

En la ventana Jerarquía, expanda el objeto ModelParent. Expanda ***MarsCuriosity-> Rover*** para encontrar cinco piezas principales de MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** y **POI-RUHF Antenna**.

* Observe los cinco objetos de información sobre herramientas correspondientes con las piezas de MarsCuriosityRover en la ventana Jerarquía. 
* Configurará estos objetos para mejorar la experiencia al mirar las piezas de MarsCuriosityRover.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implementación de los eventos While Looking At Target () y On Look Away ()

En la ventana Jerarquía, seleccione el objeto ***POI-Camera***. En la ventana Inspector, busque el componente **Eye Tracking Target (Script)** (Objetivo de seguimiento ocultar [script]) y configure los eventos **While Looking At Target ()**  & **On Look Away ()** como se indica a continuación:

* Asigne el objeto **POI-Camera ToolTip** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **Ninguna función** del evento **While Looking At Target ()** , seleccione **GameObject** > **SetActive (bool)** . Active la **Casilla** debajo para que, al mirar el objeto de destino, la acción desencadenada sea resaltar la información sobre herramientas.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Siga el mismo proceso y haga clic en la lista desplegable **Ninguna función** del escucha de eventos **On Look Away ()** . A continuación, seleccione **GameObject** > **SetActive (bool)** y deje la **Casilla** vacía para que, al apartar la mirada del objeto de destino, la acción desencadenada sea ocultar la información sobre herramientas.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Siga el mismo proceso y asigne los objetos de información sobre herramientas a los eventos **While Looking At Target ()**  & **On Look Away ()** de las piezas de **MarsCuriosityRover** correspondientes.

Para habilitar el seguimiento ocular, siga estas [instrucciones](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a crear una experiencia de realidad mixta que muestra los elementos de la interfaz de usuario, la manipulación de modelos 3D, el recorte de modelos y las características de seguimiento ocular. El tutorial le proporcionó los elementos NextButton y PreviousButton que le permiten explorar la experiencia del visor de modelos 3D. El elemento ClippingObjectButton activó los objetos de recorte para experimentar la característica de recorte. El tutorial también le proporcionó un elemento de seguimiento ocular para habilitar el resaltado de la información sobre herramientas en la experiencia.

En la próxima lección, aprenderá a crear una aplicación de comunicación remota holográfica para PC para conectarse a HoloLens 2 en cualquier momento, de modo que podrá visualizar contenido 3D en realidad mixta.

[Siguiente lección: 2. Creación de una aplicación de comunicación remota holográfica](mr-learning-pc-holographic-remoting-02.md)
