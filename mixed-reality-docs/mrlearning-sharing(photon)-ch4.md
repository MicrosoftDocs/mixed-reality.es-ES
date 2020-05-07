---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604976"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4. Integración de Azure Spatial Anchors en una experiencia compartida

En este tutorial, aprenderás a integrar Azure Spatial Anchors (ASA) en la experiencia compartida. ASA permite que varios dispositivos tengan una referencia común al mundo físico para que los usuarios se vean entre sí en su ubicación física real y vean la experiencia compartida en el mismo lugar.

## <a name="objectives"></a>Objetivos

* Integración de ASA en una experiencia compartida para la alineación de varios dispositivos
* Aprende los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, expande el objeto **TableAnchor** para exponer sus objetos secundarios:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados) y arrastra el elemento prefabricado **Buttons** para colocarlo encima del objeto secundario **TableAnchor** de la ventana Jerarquía y agregarlo a la escena como elemento secundario del objeto TableAnchor:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, configurarás una serie de eventos de botón que muestran los aspectos básicos de cómo se puede usar Azure Spatial Anchors para lograr la alineación espacial en una experiencia compartida.

En la ventana Jerarquía, expande el objeto **Button** y selecciona el primer objeto de botón secundario denominado **StartAzureSession**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

En la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** como se indica a continuación:

* En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, selecciona la función **AnchorModuleScript** > **StartAzureSession ()** .

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

En la ventana Jerarquía, selecciona el segundo objeto de botón secundario denominado **CreateAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, selecciona la función **AnchorModuleScript** > **CreateAzureAnchor ()** .
* En el nuevo campo **None (Game Object)** (Ninguno [objeto de juego]) que aparece, asigna el objeto **TableAnchor**.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

En la ventana Jerarquía, selecciona el tercer objeto de botón secundario denominado **ShareAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, selecciona la función **SharingModuleScript** > **ShareAzureAnchor ()** .

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

En la ventana Jerarquía, selecciona el cuarto objeto de botón secundario denominado **GetAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:

* En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.
* En el menú desplegable **Ninguna función**, selecciona la función **SharingModuleScript** > **GetAzureAnchor ()** .

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Conexión de la escena al recurso de Azure

En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, selecciona el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Spatial Anchor Manager (Script)** (Administrador de anclaje espacial [script]) y configura la sección **Credenciales** con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mrlearning-sharing(photon)-ch1.md#prerequisites) de esta serie de tutoriales:

* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.
* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

Con el objeto **TableAnchor** todavía seleccionado, en la ventana Inspector, asegúrate de que todos los componentes de script estén habilitados:

* Selecciona la casilla situada junto a **Spatial Anchor Manager (Script)** (Spatial Anchor Manager [script]) para habilitarla.
* Selecciona la casilla situada junto al componente **Anchor Module Script (Script)** (Script del módulo de anclaje [script]) para habilitarla.
* Selecciona la casilla situada junto al componente **Sharing Module Script (Script)** (Script del módulo de uso compartido [script]) para habilitarla.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Prueba de la experiencia con la alineación espacial

> [!NOTE]
> Azure Spatial Anchors no se puede ejecutar en Unity. Por este motivo, para probar la funcionalidad de Azure Spatial Anchors, debes implementar el proyecto en un mínimo de dos dispositivos HoloLens.

Si ahora compilas e implementas el proyecto de Unity en dos dispositivos HoloLens, puedes lograr la alineación espacial entre ellos al compartir el identificador de anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. En el dispositivo HoloLens 1: **Inicia la aplicación** (se crea una instancia del iniciador de Rocket y se coloca en la tabla).
2. En el dispositivo HoloLens 2: **Inicia la aplicación** (los dos usuarios ven la tabla con el iniciador de Rocket, sin embargo, la tabla no aparece en el mismo lugar y los avatares del usuario no se muestran donde se encuentran los usuarios).
3. En el dispositivo HoloLens 1: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).
4. En el dispositivo HoloLens 1: Presiona el botón **Create Azure Anchor** (Crear anclaje de Azure) (crea el anclaje en la ubicación del objeto TableAnchor y almacena la información de dicho anclaje en el recurso de Azure).
5. En el dispositivo HoloLens 1: Presiona el botón **Share Azure Anchor** (Compartir anclaje de Azure) (comparte el id. del anclaje con otros usuarios en tiempo real).
6. En el dispositivo HoloLens 2: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).
7. En el dispositivo HoloLens 2: Presiona el botón **Get Azure Anchor** (Obtener el anclaje de Azure) (se conecta al recurso de Azure para recuperar la información del anclaje del identificador del anclaje compartido y, a continuación, mueve el objeto TableAnchor a la ubicación en la que se creó el anclaje con el dispositivo HoloLens 1).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a integrar la instancia de Spatial Anchors eficaz de Azure para alinear dispositivos en una experiencia compartida. Con esto, damos por concluida la serie de tutoriales, en la que has aprendido a configurar una cuenta y una aplicación de Photon, integrar Photon y PUN en una aplicación de Unity, configurar los avatares de usuario y los objetos compartidos y, por último, alinear varios participantes con ASA.
