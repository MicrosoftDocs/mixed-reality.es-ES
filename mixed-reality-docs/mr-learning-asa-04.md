---
title: 'Tutoriales sobre Azure Spatial Anchors: 4. Visualización de comentarios de Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376527"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Visualización de comentarios de Azure Spatial Anchors

En este tutorial, aprenderá a proporcionar a los usuarios comentarios sobre la detección, los eventos y los estados de anclaje al usar Azure Spatial Anchors (ASA).

## <a name="objectives"></a>Objetivos

* Aprender a configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA
* Conocer y explorar los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="setting-up-asa-feedback-panel"></a>Configurar el panel de comentarios de ASA

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Instructions** (Instrucciones)  > **TextContent**. Seleccione **Objeto 3D** > **Text - TextMeshPro** (Texto: TextMeshPro) para crear un objeto de texto TextMeshPro como elemento secundario del objeto Instructions (Instrucciones) > TextContent:

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Para que resulte más fácil trabajar con la escena, define <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Visibilidad de la escena) como desactivada para el objeto ParentAnchor haciendo clic en el icono de ojo situado a la izquierda del objeto. Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego.

Cambie el nombre del objeto **Feedback** (Comentarios) del texto recién creado (TMP) y, luego, en la ventana Inspector, cambie su posición y tamaño para que se coloque estratégicamente bajo el texto de instrucción; por ejemplo:

* Cambie el valor **Pos Y** (Posición Y) del componente de transformación de rectángulo a -0,24.
* Cambie el valor **Width** (Ancho) del componente de transformación de rectángulo a 0,555.
* Cambie el valor **Height** (Altura) del componente de transformación de rectángulo a 0,1.

A continuación, elija las propiedades de la fuente para que el texto encaje bien dentro del área de texto; por ejemplo:

* Cambie el **estilo de fuente** del componente TextMeshPro - Text ( TextMeshPro: texto) a Bold (Negrita).
* Cambie el **tamaño de fuente** del componente TextMeshPro - Text (TextMeshPro: texto) a 0,17.
* Cambie la **alineación** del componente TextMeshPro - Text (TextMeshPro: texto) a Center (Centro) y Middle (Medio).

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **Feedback** (Comentarios) y, a continuación, en la ventana Inspector, use el botón**Add Component** (Agregar componente) para agregar el componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]) y configúrelo del modo siguiente:

* Asigne el objeto **Feedback** (Comentarios) al campo **Feedback Text** (Texto de comentarios) del componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]).

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a crear un panel de interfaz de usuario. Este muestra el estado actual de la experiencia de  Azure Spatial Anchors para proporcionar a los usuarios comentarios en tiempo real.

[Tutorial siguiente: 5. Azure Spatial Anchors para iOS y Android](mr-learning-asa-05.md)
