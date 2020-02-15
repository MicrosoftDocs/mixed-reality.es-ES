---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250716"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="158f5-105">3. Mostrar comentarios del delimitador espacial de Azure</span><span class="sxs-lookup"><span data-stu-id="158f5-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="158f5-106">En este tutorial, obtendrá información sobre cómo proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar delimitadores espaciales (ASA) de Azure.</span><span class="sxs-lookup"><span data-stu-id="158f5-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="158f5-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="158f5-107">Objectives</span></span>

* <span data-ttu-id="158f5-108">Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.</span><span class="sxs-lookup"><span data-stu-id="158f5-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="158f5-109">Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="158f5-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="158f5-110">Configuración del panel de interfaz de usuario de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="158f5-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="158f5-111">En la ventana jerarquía, haga clic con el botón derecho en las **instrucciones** > objeto **TextContent** y seleccione **objeto 3D** > **Text-TextMeshPro** para crear un objeto de texto TextMeshPro como un elemento secundario de las instrucciones > objeto TextContent y asígnele un nombre adecuado, por ejemplo, **feedback**:</span><span class="sxs-lookup"><span data-stu-id="158f5-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning: base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="158f5-113">Para que sea más fácil trabajar con la escena, haga clic en el icono de ojo situado a la izquierda del objeto para establecer la visibilidad de la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">escena</a> del objeto ParentAnchor en OFF.</span><span class="sxs-lookup"><span data-stu-id="158f5-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="158f5-114">Esto oculta el objeto en la ventana de la escena sin cambiar su visibilidad en el juego.</span><span class="sxs-lookup"><span data-stu-id="158f5-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="158f5-115">Con el objeto de **comentarios** aún seleccionado, en la ventana del inspector cambie su posición y el tamaño para que se coloquen en un lugar inferior al texto de la instrucción, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="158f5-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="158f5-116">Cambie la transformación de rectángulo **Y** a-0,24</span><span class="sxs-lookup"><span data-stu-id="158f5-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="158f5-117">Cambiar el **ancho** de la transformación Rect a 0,555</span><span class="sxs-lookup"><span data-stu-id="158f5-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="158f5-118">Cambiar el **alto** de la transformación Rect a 0,1</span><span class="sxs-lookup"><span data-stu-id="158f5-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="158f5-119">A continuación, elija Propiedades de fuente para que el texto se ajuste perfectamente dentro del área de texto, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="158f5-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="158f5-120">Cambiar el **estilo de fuente** de la malla de texto Pro (Script) a negrita</span><span class="sxs-lookup"><span data-stu-id="158f5-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="158f5-121">Cambiar el **tamaño de fuente** de la malla de texto Pro (Script) a 0,17</span><span class="sxs-lookup"><span data-stu-id="158f5-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="158f5-122">Cambiar la **alineación** de la malla de texto Pro (Script) al centro y el medio</span><span class="sxs-lookup"><span data-stu-id="158f5-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning: base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="158f5-124">Con el objeto de **comentarios** aún seleccionado, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **script de comentarios de delimitador (Script)** al objeto de comentarios:</span><span class="sxs-lookup"><span data-stu-id="158f5-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning: base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="158f5-126">Asigne el objeto de **comentarios** al campo de **texto de comentarios** del componente script de **comentarios de delimitador (Script)** :</span><span class="sxs-lookup"><span data-stu-id="158f5-126">Assign the **Feedback** object to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning: base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="158f5-128">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="158f5-128">Congratulations</span></span>

<span data-ttu-id="158f5-129">En este tutorial, ha aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia del anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="158f5-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
