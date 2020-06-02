---
title: 'Tutoriales sobre Azure Spatial Anchors: 3. Visualización de comentarios de Azure Spatial Anchors'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866905"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Visualización de comentarios de Azure Spatial Anchors

En este tutorial, aprenderás a proporcionar a los usuarios comentarios sobre la detección, los eventos y los estados de anclaje al usar Azure Spatial Anchors (ASA).

## <a name="objectives"></a>Objetivos

* Aprender a configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA
* Comprender y explorar los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="set-up-asa-feedback-ui-panel"></a>Configurar el panel de la interfaz de usuario de comentarios de ASA

En la ventana Hierarchy (Jerarquía), haz clic con el botón derecho en **Instructions** (Instrucciones) > objeto **TextContent** y selecciona **3D Object** > **Text-TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para crear un objeto de texto de TextMeshPro como elemento secundario del objeto Instructions (Instrucciones) > TextContent y asignarle un nombre adecuado; por ejemplo, **Feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Para que resulte más fácil trabajar con la escena, define <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Visibilidad de la escena) como desactivada para el objeto ParentAnchor haciendo clic en el icono de ojo situado a la izquierda del objeto. Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego.

Una vez seleccionado el objeto **Feedback** (Comentarios), en la ventana Inspector, cambia su posición y tamaño para que se coloque estratégicamente bajo el texto de instrucción; por ejemplo:

* Cambia el valor **Pos Y** de transformación de rectángulo a 0,24.
* Cambia el valor **Width** (Ancho) de transformación de rectángulo a 0,555.
* Cambia el valor **Height** (Altura) de transformación de rectángulo a 0,1.

A continuación, elige las propiedades de la fuente para que el texto encaje bien dentro del área de texto; por ejemplo:

* Cambia el valor **Font Style** (Estilo de fuente) de Text Mesh Pro (Script) a Bold (Negrita).
* Cambia el valor **Font Size** (Tamaño de fuente) de Text Mesh Pro (Script) a 0,17.
* Cambia el valor **Alignment** (Alineación) de Text Mesh Pro (Script) a Center and Middle (Centro y medio).

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Con el objeto **Feedback** (Comentarios) aún seleccionado, en la ventana Inspector, usa el botón **Add Component (Agregar componente)** para agregar el componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]) al objeto Feedback (Comentarios):

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Asigna el objeto **Feedback** (Comentarios) al campo **Feedback Text** (Texto de comentarios) del componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]):

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de Azure Spatial Anchors para proporcionar a los usuarios comentarios en tiempo real.

[Siguiente lección: 4. Azure Spatial Anchors para iOS y Android](mrlearning-asa-ch4.md)
