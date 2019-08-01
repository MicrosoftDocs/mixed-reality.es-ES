---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 45a71cada97dff4a2fb32f2eaf7700816f2e0d42
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702029"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="9e487-105">3. Visualización de los comentarios del delimitador espacial de Azure</span><span class="sxs-lookup"><span data-stu-id="9e487-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="9e487-106">En esta lección, aprenderá a proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="9e487-106">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="9e487-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9e487-107">Objectives</span></span>

* <span data-ttu-id="9e487-108">Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.</span><span class="sxs-lookup"><span data-stu-id="9e487-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="9e487-109">Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="9e487-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="9e487-110">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9e487-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="9e487-111">Configuración del panel de interfaz de usuario de comentarios de ASA</span><span class="sxs-lookup"><span data-stu-id="9e487-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="9e487-112">En esta lección, no vamos a usar los botones "SaveAnchorToDisk" y "ShareAnchor", por lo que debe seleccionar ambos botones y desactivar la casilla en el panel Inspector (como se muestra a continuación) para ocultar estos botones.</span><span class="sxs-lookup"><span data-stu-id="9e487-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="9e487-114">A continuación, cree el panel de instrucciones.</span><span class="sxs-lookup"><span data-stu-id="9e487-114">Next, create the instruction panel.</span></span> <span data-ttu-id="9e487-115">Para empezar, haga clic con el botón derecho en el botón "instrucciones", mantenga el mouse sobre "objeto 3D" y seleccione "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="9e487-115">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="9e487-117">Ajuste la escala y la posición del texto para que coincida con las instrucciones de la escena.</span><span class="sxs-lookup"><span data-stu-id="9e487-117">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="9e487-118">Además, asegúrese de que la alineación para todo el texto está centrada.</span><span class="sxs-lookup"><span data-stu-id="9e487-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="9e487-119">A continuación, elimine el texto de ejemplo del editor de texto, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="9e487-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="9e487-121">Cambie el nombre del objeto TextMeshPro a "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="9e487-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="9e487-123">En el panel Proyecto, seleccione "recursos" y haga clic con el botón secundario y, a continuación, seleccione "Mostrar en el explorador".</span><span class="sxs-lookup"><span data-stu-id="9e487-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="9e487-125">Ahora, haga clic [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) para descargar los archivos necesarios en los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="9e487-125">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="9e487-126">Una vez que se abra el explorador, seleccione la carpeta Assets, la carpeta "ASAmodulesAssets" y copie los archivos de script del módulo de delimitador y los de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="9e487-126">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="9e487-128">Nota: Si aparece un mensaje emergente que le pregunta si desea sobrescribir el antiguo o conservar el antiguo, asegúrese de que selecciona sobrescribir.</span><span class="sxs-lookup"><span data-stu-id="9e487-128">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="9e487-129">Ahora vuelva a la carpeta assets.</span><span class="sxs-lookup"><span data-stu-id="9e487-129">Now return to the Assets folder.</span></span> <span data-ttu-id="9e487-130">A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", a continuación, a la carpeta Examples y, por último, a la carpeta scripts, y copie el contenedor de demostración de delimitadores espaciales de Azure en esa carpeta.</span><span class="sxs-lookup"><span data-stu-id="9e487-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="9e487-132">Ahora que los archivos se han cargado, asegúrese de que el texto "feedbackpanel" está seleccionado, en la jerarquía de ASA_feedback y haga clic en "Agregar componente" y agregue el script de comentarios de delimitador. para ello, búsquelo y selecciónelo cuando aparezca.</span><span class="sxs-lookup"><span data-stu-id="9e487-132">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="9e487-134">Arrastre el objeto de texto "feedbackPanel" desde la jerarquía de ASA_Feedback hasta la ranura vacía situada debajo del script, tal como se muestra en la figura siguiente.</span><span class="sxs-lookup"><span data-stu-id="9e487-134">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9e487-136">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="9e487-136">Congratulations</span></span>

<span data-ttu-id="9e487-137">En esta lección se ha aprendido cómo crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="9e487-137">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


