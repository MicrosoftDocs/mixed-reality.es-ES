---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031248"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="0128f-105">4. Uso compartido de movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="0128f-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="0128f-106">En este tutorial, aprenderás a compartir los movimientos de objetos para que todos los participantes de una sesión compartida puedan colaborar y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="0128f-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="0128f-107">Esta lección se basa en el lanzacohetes lunar que se creó como parte de los [tutoriales del módulo básico](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="0128f-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="0128f-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0128f-108">Objectives</span></span>

- <span data-ttu-id="0128f-109">Seleccionar el lanzacohetes lunar como modelo 3D que se compartirá</span><span class="sxs-lookup"><span data-stu-id="0128f-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="0128f-110">Configurar el proyecto para compartir los movimientos del modelo 3D</span><span class="sxs-lookup"><span data-stu-id="0128f-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="0128f-111">Aprender a crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="0128f-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="0128f-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0128f-112">Instructions</span></span>

1. <span data-ttu-id="0128f-113">Guarda la escena de la lección anterior (Control + S).</span><span class="sxs-lookup"><span data-stu-id="0128f-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="0128f-114">Puedes asignarle el nombre HLSharedProjectMainPart4.unity para que sea más fácil de encontrar cuando la necesites.</span><span class="sxs-lookup"><span data-stu-id="0128f-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="0128f-115">Desde la ventana Project (Proyecto), en la carpeta Assets -> Scripts (Recursos -> Scripts), haz doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que estés usando.</span><span class="sxs-lookup"><span data-stu-id="0128f-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="0128f-117">En las líneas 34 y 38, quita "//" para activar el código para la tabla que usarás en esta lección.</span><span class="sxs-lookup"><span data-stu-id="0128f-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="0128f-118">A continuación, guarda el archivo.</span><span class="sxs-lookup"><span data-stu-id="0128f-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="0128f-120">En la ventana Project (Proyecto), haz doble clic en el archivo PhotonRoom.cs en la carpeta Assets -> Scripts (Recursos -> Scripts) para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0128f-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="0128f-122">Al igual que en el paso 3, es necesario quitar "//" para activar el código en las líneas 25, 26 y 106.</span><span class="sxs-lookup"><span data-stu-id="0128f-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="0128f-125">En la vista Hierarchy (Jerarquía), selecciona el objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="0128f-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="0128f-127">En la vista Project (Proyecto), desplázate a Assets->Resources->Prefabs (Recursos -> Recursos -> Objetos prefabricados).</span><span class="sxs-lookup"><span data-stu-id="0128f-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="0128f-128">En primer lugar, arrastra y suelta el objeto prefabricado Table (Tabla) en el espacio Tableprefab de la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="0128f-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="0128f-129">A continuación, arrastra y suelta RocketLauncherCompleteVariantprefab en el espacio Module de la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="0128f-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="0128f-131">Si haces clic en uno de los objetos prefabricados y sueltas, el inspector cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="0128f-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="0128f-132">Haz clic en cada objeto y arrástralo y suéltalo en su espacio correspondiente.</span><span class="sxs-lookup"><span data-stu-id="0128f-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="0128f-133">Haz clic en la flecha situada a la izquierda de MixedRealityPlayspace y desplaza el objeto de juego secundario MainCamera hacia abajo en el objeto prefabricado SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="0128f-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="0128f-134">A continuación, elimina el objeto prefabricado MixedRealityPlayspace seleccionando el objeto prefabricado y pulsa "Suprimir" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="0128f-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="0128f-136">Asegúrate de que tanto las posiciones de la cámara principal como de SharedPlayground están establecidas en 0,0,0.</span><span class="sxs-lookup"><span data-stu-id="0128f-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="0128f-137">Selecciona el objeto "SharedPlayground" y haz clic con el botón derecho del mouse para seleccionar la opción "Create empty" (Crear vacío) " para crear un objeto de juego vacío como elemento secundario del objeto de juego "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="0128f-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="0128f-139">Con el nuevo objeto seleccionado en la jerarquía, cambia el nombre del objeto a TableAnchor en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="0128f-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="0128f-140">Además, haz clic en Agregar componente y busca el componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="0128f-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="0128f-141">Selecciónalo y agrégalo al objeto.</span><span class="sxs-lookup"><span data-stu-id="0128f-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="0128f-143">En el panel Project (Proyecto) de la carpeta Prefabs, arrastra el objeto prefabricado Table (Tabla) hasta el objeto secundario "TableAnchor" que acabas de crear.</span><span class="sxs-lookup"><span data-stu-id="0128f-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0128f-145">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="0128f-145">Congratulations</span></span>

<span data-ttu-id="0128f-146">Una vez completados estos pasos, busca el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="0128f-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="0128f-147">Después de esto, todos los usuarios que se unan al proyecto de Unity podrán mover el lanzacohetes lunar.</span><span class="sxs-lookup"><span data-stu-id="0128f-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="0128f-148">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="0128f-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="0128f-149">Estos conceptos sirven como bloques de creación fundamentales para conseguir experiencias de colaboración compartidas completas.</span><span class="sxs-lookup"><span data-stu-id="0128f-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="0128f-150">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos, de modo que los usuarios locales no se pueden ver entre sí ni los objetos en el mismo lugar dentro del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="0128f-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="0128f-151">Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="0128f-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="0128f-152">En este módulo, lo conseguirás con [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>), que se implementará en la siguiente lección.</span><span class="sxs-lookup"><span data-stu-id="0128f-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="0128f-153">Antes de continuar con la siguiente lección, deberás completar el módulo de aprendizaje de ASA que abarca los conceptos básicos de ASA, la creación de cuentas y recursos de Azure, así como otros bloques de creación fundamentales para poder integrar esto en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="0128f-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="0128f-154">[Siguiente lección: 5. Integración de Azure Spatial Anchors en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="0128f-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
