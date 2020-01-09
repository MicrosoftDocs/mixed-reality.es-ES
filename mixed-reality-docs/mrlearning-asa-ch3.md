---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334407"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="2f32c-105">3. Mostrar comentarios del delimitador espacial de Azure</span><span class="sxs-lookup"><span data-stu-id="2f32c-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="2f32c-106">En esta lección, aprenderá a proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar los anclajes espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="2f32c-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="2f32c-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2f32c-107">Objectives</span></span>

* <span data-ttu-id="2f32c-108">Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.</span><span class="sxs-lookup"><span data-stu-id="2f32c-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="2f32c-109">Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="2f32c-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="2f32c-110">Configuración del panel de interfaz de usuario de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="2f32c-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="2f32c-111">En esta lección, no vamos a usar los botones "SaveAnchorToDisk" y "ShareAnchor", así que seleccione ambos botones y desactive la casilla en el panel del Inspector (como se muestra a continuación) para ocultar estos botones.</span><span class="sxs-lookup"><span data-stu-id="2f32c-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="2f32c-113">Cree el panel de instrucciones.</span><span class="sxs-lookup"><span data-stu-id="2f32c-113">Create the instruction panel.</span></span> <span data-ttu-id="2f32c-114">Para empezar, haga clic con el botón derecho en el botón "instrucciones", mantenga el mouse sobre "objeto 3D" y seleccione "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="2f32c-114">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="2f32c-116">Ajuste la escala y la posición del texto para que coincida con las instrucciones de la escena.</span><span class="sxs-lookup"><span data-stu-id="2f32c-116">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="2f32c-117">Además, asegúrese de que la alineación para todo el texto está centrada.</span><span class="sxs-lookup"><span data-stu-id="2f32c-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="2f32c-118">A continuación, elimine el texto de ejemplo del editor de texto, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="2f32c-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="2f32c-120">Cambie el nombre del objeto TextMeshPro a "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="2f32c-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="2f32c-122">Asegúrese de que el texto "feedbackpanel" está seleccionado en la jerarquía de ASA_feedback, haga clic en "Agregar componente" y agregue el script de comentarios del delimitador buscándolo y selecciónelo cuando aparezca.</span><span class="sxs-lookup"><span data-stu-id="2f32c-122">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span>

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="2f32c-124">Arrastre el objeto de texto "feedbackPanel" desde la jerarquía de ASA_Feedback hasta la ranura vacía situada debajo del script, tal como se muestra en la figura siguiente.</span><span class="sxs-lookup"><span data-stu-id="2f32c-124">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span>

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="2f32c-126">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2f32c-126">Congratulations</span></span>

<span data-ttu-id="2f32c-127">En esta lección, hemos aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia del anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="2f32c-127">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
