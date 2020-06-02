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
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="40ed7-105">3. Visualización de comentarios de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="40ed7-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="40ed7-106">En este tutorial, aprenderás a proporcionar a los usuarios comentarios sobre la detección, los eventos y los estados de anclaje al usar Azure Spatial Anchors (ASA).</span><span class="sxs-lookup"><span data-stu-id="40ed7-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="40ed7-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="40ed7-107">Objectives</span></span>

* <span data-ttu-id="40ed7-108">Aprender a configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA</span><span class="sxs-lookup"><span data-stu-id="40ed7-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="40ed7-109">Comprender y explorar los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="40ed7-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="40ed7-110">Configurar el panel de la interfaz de usuario de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="40ed7-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="40ed7-111">En la ventana Hierarchy (Jerarquía), haz clic con el botón derecho en **Instructions** (Instrucciones) > objeto **TextContent** y selecciona **3D Object** > **Text-TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para crear un objeto de texto de TextMeshPro como elemento secundario del objeto Instructions (Instrucciones) > TextContent y asignarle un nombre adecuado; por ejemplo, **Feedback**:</span><span class="sxs-lookup"><span data-stu-id="40ed7-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="40ed7-113">Para que resulte más fácil trabajar con la escena, define <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Visibilidad de la escena) como desactivada para el objeto ParentAnchor haciendo clic en el icono de ojo situado a la izquierda del objeto.</span><span class="sxs-lookup"><span data-stu-id="40ed7-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="40ed7-114">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego.</span><span class="sxs-lookup"><span data-stu-id="40ed7-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="40ed7-115">Una vez seleccionado el objeto **Feedback** (Comentarios), en la ventana Inspector, cambia su posición y tamaño para que se coloque estratégicamente bajo el texto de instrucción; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="40ed7-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="40ed7-116">Cambia el valor **Pos Y** de transformación de rectángulo a 0,24.</span><span class="sxs-lookup"><span data-stu-id="40ed7-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="40ed7-117">Cambia el valor **Width** (Ancho) de transformación de rectángulo a 0,555.</span><span class="sxs-lookup"><span data-stu-id="40ed7-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="40ed7-118">Cambia el valor **Height** (Altura) de transformación de rectángulo a 0,1.</span><span class="sxs-lookup"><span data-stu-id="40ed7-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="40ed7-119">A continuación, elige las propiedades de la fuente para que el texto encaje bien dentro del área de texto; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="40ed7-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="40ed7-120">Cambia el valor **Font Style** (Estilo de fuente) de Text Mesh Pro (Script) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="40ed7-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="40ed7-121">Cambia el valor **Font Size** (Tamaño de fuente) de Text Mesh Pro (Script) a 0,17.</span><span class="sxs-lookup"><span data-stu-id="40ed7-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="40ed7-122">Cambia el valor **Alignment** (Alineación) de Text Mesh Pro (Script) a Center and Middle (Centro y medio).</span><span class="sxs-lookup"><span data-stu-id="40ed7-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="40ed7-124">Con el objeto **Feedback** (Comentarios) aún seleccionado, en la ventana Inspector, usa el botón **Add Component (Agregar componente)** para agregar el componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]) al objeto Feedback (Comentarios):</span><span class="sxs-lookup"><span data-stu-id="40ed7-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="40ed7-126">Asigna el objeto **Feedback** (Comentarios) al campo **Feedback Text** (Texto de comentarios) del componente **Anchor Feedback Script (Script)** (Script de comentarios de anclaje [script]):</span><span class="sxs-lookup"><span data-stu-id="40ed7-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="40ed7-128">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="40ed7-128">Congratulations</span></span>

<span data-ttu-id="40ed7-129">En este tutorial, has aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de Azure Spatial Anchors para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="40ed7-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="40ed7-130">Siguiente lección: 4. Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="40ed7-130">Next Lesson: 4. Azure Spatial Anchors for Android and iOS</span></span>](mrlearning-asa-ch4.md)
