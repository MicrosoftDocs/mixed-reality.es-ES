---
title: Módulo de ASA de aprendizaje de MR Azure delimitador espaciales en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327567"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="f1309-104">Visualización de comentarios de Azure delimitador espacial</span><span class="sxs-lookup"><span data-stu-id="f1309-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="f1309-105">En esta lección, aprenderá acerca de cómo proporcionar a los usuarios con sus comentarios sobre la detección de anclaje, eventos y el estado cuando se usa Azure espacial delimitadores.</span><span class="sxs-lookup"><span data-stu-id="f1309-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="f1309-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="f1309-106">Objectives:</span></span>

* <span data-ttu-id="f1309-107">Obtenga información sobre cómo configurar un panel de interfaz de usuario que se muestra información importante acerca de la sesión actual de ASA</span><span class="sxs-lookup"><span data-stu-id="f1309-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="f1309-108">Conocer y explorar elementos de comentarios que el SDK de ASA pone a disposición de los usuarios</span><span class="sxs-lookup"><span data-stu-id="f1309-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="f1309-109">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="f1309-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="f1309-110">Configurar el Panel de interfaz de usuario de comentarios ASA</span><span class="sxs-lookup"><span data-stu-id="f1309-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="f1309-111">En esta lección, no vamos a usar el "SaveAnchorToDisk" y "ShareAnchor" botones así que seleccione ambos botones y desactive la casilla de verificación en el panel del inspector (como se muestra a continuación) para ocultar estos botones.</span><span class="sxs-lookup"><span data-stu-id="f1309-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="f1309-113">A continuación, cree el panel de la instrucción.</span><span class="sxs-lookup"><span data-stu-id="f1309-113">Next, create the instruction panel.</span></span> <span data-ttu-id="f1309-114">Iniciar haciendo clic en el botón "instructions", mantenga el mouse sobre el "objeto 3D" y seleccione "textmeshpro-text".</span><span class="sxs-lookup"><span data-stu-id="f1309-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="f1309-116">Ajustar la escala y la posición del texto para que haga coincidir con las instrucciones de la escena.</span><span class="sxs-lookup"><span data-stu-id="f1309-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="f1309-117">Asegúrese también de que la alineación de todo el texto está centrada.</span><span class="sxs-lookup"><span data-stu-id="f1309-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="f1309-118">A continuación, elimine el texto de ejemplo del editor de texto, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="f1309-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="f1309-120">Cambie el nombre del objeto TextMeshPro a "FeedbackPanel."</span><span class="sxs-lookup"><span data-stu-id="f1309-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="f1309-122">En el panel proyecto, seleccione "activos" y haga clic en, seleccione "mostrar en el explorador."</span><span class="sxs-lookup"><span data-stu-id="f1309-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="f1309-124">Ahora, haga clic en [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) descargar los archivos necesarios en los próximos pasos.</span><span class="sxs-lookup"><span data-stu-id="f1309-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="f1309-125">Una vez que se abre el explorador, seleccione la carpeta assets y, después, en la carpeta "ASAmodulesAssets" y copie el script de comentarios de delimitador y los archivos de script del módulo de anclaje en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="f1309-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="f1309-127">Nota: Si recibe un mensaje emergente que pregunta si desea sobrescribir la antigua o mantener la antigua, asegúrese de seleccionar sobrescritura.</span><span class="sxs-lookup"><span data-stu-id="f1309-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="f1309-128">Ahora, vuelva a la carpeta Assets.</span><span class="sxs-lookup"><span data-stu-id="f1309-128">Now return to the Assets folder.</span></span> <span data-ttu-id="f1309-129">A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", a continuación, la carpeta de ejemplos y, finalmente, en la carpeta de scripts y copie el contenedor de demostración de Azure espacial anclajes en dicha carpeta.</span><span class="sxs-lookup"><span data-stu-id="f1309-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="f1309-131">Ahora que se cargan los archivos, asegúrese de que el texto "feedbackpanel" está seleccionado, en la jerarquía ASA_feedback y haga clic en "agregar el componente" y agregue el script de comentarios de anclaje, búsquelo y selecciónelo cuando aparezca.</span><span class="sxs-lookup"><span data-stu-id="f1309-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="f1309-133">Arrastre el objeto de texto "feedbackPanel" de la jerarquía de ASA_Feedback a la ranura vacía debajo de la secuencia de comandos tal como se muestra en la figura siguiente.</span><span class="sxs-lookup"><span data-stu-id="f1309-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="f1309-135">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="f1309-135">Congratulations</span></span>

<span data-ttu-id="f1309-136">En esta lección hemos aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de anclaje espacial de Azure para proporcionar el usuario con comentarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="f1309-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


