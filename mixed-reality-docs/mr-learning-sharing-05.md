---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376587"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integración de Azure Spatial Anchors en una experiencia compartida

En este tutorial, aprenderás a integrar Azure Spatial Anchors (ASA) en la experiencia compartida. ASA permite que varios dispositivos tengan una referencia común al mundo físico para que los usuarios se vean entre sí en su ubicación física real y vean la experiencia compartida en el mismo lugar.

## <a name="objectives"></a>Objetivos

* Integración de ASA en una experiencia compartida para la alineación de varios dispositivos
* Aprende los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, expande el objeto **TableAnchor** para exponer sus objetos secundarios:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.MultiUserCapabilities** > carpeta **Prefabs** (Recursos prefabricados) y arrastre el elemento prefabricado **Buttons** para colocarlo encima del objeto secundario **TableAnchor** y agregarlo a la escena como elemento secundario del objeto TableAnchor:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, configurará una serie de eventos de botón que muestran los aspectos básicos de cómo se puede usar Azure Spatial Anchors para lograr la alineación espacial en una experiencia compartida.

En la ventana Jerarquía, expande el objeto **Button** y selecciona el primer objeto de botón secundario denominado **StartAzureSession**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

En la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** como se indica a continuación:

* En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, seleccione la función **AnchorModuleScript** > **StartAzureSession ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

En la ventana Jerarquía, selecciona el segundo objeto de botón secundario denominado **CreateAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, seleccione la función **AnchorModuleScript** > **CreateAzureAnchor ()** .
* En el nuevo campo **None (Game Object)** (Ninguno [objeto de juego]) que aparece, asigna el objeto **TableAnchor**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

En la ventana Jerarquía, selecciona el tercer objeto de botón secundario denominado **ShareAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, seleccione **SharingModuleScript** > función **ShareAzureAnchor ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

En la ventana Jerarquía, seleccione el cuarto objeto de botón secundario denominado **GetAzureAnchor** y, a continuación, en la ventana Inspector, busque el componente **Interactable (Script)** (Interactivo [script]) y configure el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, seleccione **SharingModuleScript** > función **GetAzureAnchor ()** .

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Conexión de la escena al recurso de Azure

En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, selecciona el objeto **TableAnchor**.

En la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** (Administrador de anclaje espacial [script]) y configure la sección **Credenciales** con las credenciales de la cuenta de Azure Spatial Anchors que se creó como parte de los [requisitos previos](mr-learning-sharing-01.md#prerequisites) de esta serie de tutoriales:

* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.
* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> En lugar de configurar el id. y la clave de la cuenta de Spatial Anchors en la escena, puede establecerlos para todo el proyecto, lo que puede resultar ventajoso si tiene varias escenas con ASA. Para ello, en la ventana Proyecto, desplácese a Assets (Recursos) > AzureSpatialAnchors.SDK > Resources (Recursos) > recurso **SpatialAnchorConfig**, y después establezca los valores en la ventana Inspector.

En la ventana Jerarquía, seleccione el objeto **TableAnchor**. A continuación, en la ventana Inspector, busque el componente **Anchor Module (Script)** (Módulo de anclaje [script]) y configúrelo de la manera siguiente:

* Cambie algunos dígitos en el campo **Public Sharing Pin** (PIN de uso compartido público), de modo que el PIN sea único para el proyecto.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

Con el objeto **TableAnchor** aún seleccionado, en la ventana Inspector, asegúrese de que todos los componentes de script estén **habilitados**:

* Selecciona la casilla situada junto a **Spatial Anchor Manager (Script)** (Spatial Anchor Manager [script]) para habilitarla.
* Selecciona la casilla situada junto al componente **Anchor Module Script (Script)** (Script del módulo de anclaje [script]) para habilitarla.
* Selecciona la casilla situada junto al componente **Sharing Module Script (Script)** (Script del módulo de uso compartido [script]) para habilitarla.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Prueba de la experiencia con la alineación espacial

> [!NOTE]
> Azure Spatial Anchors no se puede ejecutar en Unity. Por este motivo, para probar la funcionalidad de Azure Spatial Anchors, debe implementar el proyecto en un mínimo de dos dispositivos.

Si ahora compila e implementa el proyecto de Unity en dos dispositivos, puede lograr la alineación espacial entre ellos al compartir el id. de anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. En el dispositivo 1: **Inicie la aplicación** (se crea una instancia de Rover Explorer y se coloca en la tabla).
2. En el dispositivo 2: **Inicie la aplicación** (los dos usuarios ven la tabla con Rover Explorer, pero la tabla no aparece en el mismo lugar y los avatares del usuario no se muestran donde se encuentran los usuarios).
3. En el dispositivo 1: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).
4. En el dispositivo 1: Presiona el botón **Create Azure Anchor** (Crear anclaje de Azure) (crea el anclaje en la ubicación del objeto TableAnchor y almacena la información de dicho anclaje en el recurso de Azure).
5. En el dispositivo 1: Presiona el botón **Share Azure Anchor** (Compartir anclaje de Azure) (comparte el id. del anclaje con otros usuarios en tiempo real).
6. En el dispositivo 2: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).
7. En el dispositivo 2: Presione el botón **Get Azure Anchor** (Obtener anclaje de Azure) (se conecta al recurso de Azure para recuperar la información del anclaje del identificador de anclaje compartido y, a continuación, mueve el objeto TableAnchor a la ubicación en la que se creó el anclaje con el dispositivo 1).

> [!TIP]
> Si no tiene acceso a dos dispositivos de HoloLens, puede seguir el tutorial [Creación de instancias de Azure Spatial Anchors para dispositivos móviles](mr-learning-asa-05.md) para implementar el proyecto en su dispositivo móvil.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a integrar la instancia de Spatial Anchors eficaz de Azure para alinear dispositivos en una experiencia compartida.

Con esto, damos por concluida la serie de tutoriales, en la que aprendió a configurar una cuenta de Photon, crear una aplicación de PUN, integrar PUN en un proyecto de Unity, configurar los avatares de usuario y los objetos compartidos y, por último, alinear varios participantes con Azure Spatial Anchors.
