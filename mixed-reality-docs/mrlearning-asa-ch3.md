---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438417"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="baba3-105">3. Mostrar comentarios del delimitador espacial de Azure</span><span class="sxs-lookup"><span data-stu-id="baba3-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="baba3-106">En esta lección, aprenderá a proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar los anclajes espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="baba3-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="baba3-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="baba3-107">Objectives</span></span>

* <span data-ttu-id="baba3-108">Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.</span><span class="sxs-lookup"><span data-stu-id="baba3-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="baba3-109">Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="baba3-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="baba3-110">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="baba3-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="baba3-111">Configuración del panel de interfaz de usuario de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="baba3-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="baba3-112">En esta lección, no vamos a usar los botones "SaveAnchorToDisk" y "ShareAnchor", así que seleccione ambos botones y desactive la casilla en el panel del Inspector (como se muestra a continuación) para ocultar estos botones.</span><span class="sxs-lookup"><span data-stu-id="baba3-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="baba3-114">Cree el panel de instrucciones.</span><span class="sxs-lookup"><span data-stu-id="baba3-114">Create the instruction panel.</span></span> <span data-ttu-id="baba3-115">Para empezar, haga clic con el botón derecho en el botón "instrucciones", mantenga el mouse sobre "objeto 3D" y seleccione "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="baba3-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="baba3-117">Ajuste la escala y la posición del texto para que coincida con las instrucciones de la escena.</span><span class="sxs-lookup"><span data-stu-id="baba3-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="baba3-118">Además, asegúrese de que la alineación para todo el texto está centrada.</span><span class="sxs-lookup"><span data-stu-id="baba3-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="baba3-119">A continuación, elimine el texto de ejemplo del editor de texto, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="baba3-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="baba3-121">Cambie el nombre del objeto TextMeshPro a "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="baba3-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="baba3-123">En el panel Proyecto, seleccione "recursos" y haga clic con el botón secundario y, a continuación, seleccione "Mostrar en el explorador".</span><span class="sxs-lookup"><span data-stu-id="baba3-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="baba3-125">Haga clic [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) para descargar los archivos necesarios en los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="baba3-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="baba3-126">Una vez que se abra el explorador, seleccione la carpeta assets y, a continuación, la carpeta "ASAmodulesAssets" y copie los archivos de script del módulo de delimitador y los de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="baba3-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="baba3-128">Nota: Si recibe un mensaje emergente que le pregunta si desea sobrescribir el antiguo o conservar el antiguo, seleccione sobrescribir.</span><span class="sxs-lookup"><span data-stu-id="baba3-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="baba3-129">Vuelva a la carpeta assets.</span><span class="sxs-lookup"><span data-stu-id="baba3-129">Return to the Assets folder.</span></span> <span data-ttu-id="baba3-130">A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", seguida de la carpeta Examples y, por último, la carpeta scripts.</span><span class="sxs-lookup"><span data-stu-id="baba3-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="baba3-131">A continuación, copie el contenedor de demostración de anclajes espaciales de Azure en esa carpeta.</span><span class="sxs-lookup"><span data-stu-id="baba3-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="baba3-133">Ahora que los archivos se han cargado, asegúrese de que el texto "feedbackpanel" está seleccionado en la jerarquía de ASA_feedback, haga clic en "Agregar componente" y agregue el script de comentarios de delimitador buscándolo y seleccionándolo cuando aparezca.</span><span class="sxs-lookup"><span data-stu-id="baba3-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="baba3-135">Arrastre el objeto de texto "feedbackPanel" desde la jerarquía de ASA_Feedback hasta la ranura vacía situada debajo del script, tal como se muestra en la figura siguiente.</span><span class="sxs-lookup"><span data-stu-id="baba3-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="baba3-137">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="baba3-137">Congratulations</span></span>

<span data-ttu-id="baba3-138">En esta lección, hemos aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia del anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="baba3-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


