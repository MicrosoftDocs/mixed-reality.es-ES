---
title: 'Tutoriales de funcionalidades para varios usuarios: 4. Compartir movimientos de objetos con varios usuarios'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56f7c767323285453cbeea9034f97a7c14e92359
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885628"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="d81f3-105">4. compartir movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="d81f3-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="d81f3-106">En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una sesión compartida puedan colaborar y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="d81f3-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="d81f3-107">Esta lección se basa en el selector lunar que se compiló como parte de los [Tutoriales del módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="d81f3-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="d81f3-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d81f3-108">Objectives</span></span>

- <span data-ttu-id="d81f3-109">Traer el selector lunar como el modelo 3D que se va a compartir</span><span class="sxs-lookup"><span data-stu-id="d81f3-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="d81f3-110">Configurar el proyecto para compartir los movimientos del modelo 3D</span><span class="sxs-lookup"><span data-stu-id="d81f3-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="d81f3-111">Obtenga información sobre cómo crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="d81f3-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="d81f3-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d81f3-112">Instructions</span></span>

1. <span data-ttu-id="d81f3-113">Guarde la escena de la lección anterior (control + S).</span><span class="sxs-lookup"><span data-stu-id="d81f3-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="d81f3-114">Puede asignarle el nombre HLSharedProjectMainPart4. Unity para que sea más fácil encontrarlo cuando lo necesite.</span><span class="sxs-lookup"><span data-stu-id="d81f3-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="d81f3-115">En la ventana proyecto, en la carpeta assets-> scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que esté usando.</span><span class="sxs-lookup"><span data-stu-id="d81f3-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="d81f3-117">En las líneas 34 y 38, quite "//" para activar el código para la tabla que utilizará en esta lección.</span><span class="sxs-lookup"><span data-stu-id="d81f3-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="d81f3-118">A continuación, guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="d81f3-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="d81f3-120">En la ventana proyecto, haga doble clic en el archivo PhotonRoom.cs en la carpeta assets-> scripts para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d81f3-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="d81f3-122">Al igual que en el paso 3, es necesario quitar "//" para activar el código en las líneas 25, 26 y 106.</span><span class="sxs-lookup"><span data-stu-id="d81f3-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="d81f3-125">En la vista de jerarquía, seleccione el objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="d81f3-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="d81f3-127">En la vista de proyecto, vaya a activos-> recursos-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d81f3-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="d81f3-128">En primer lugar, arrastre y coloque la tabla recurso prefabricado en la ranura Tableprefab en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="d81f3-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="d81f3-129">A continuación, arrastre y coloque RocketLauncherCompleteVariantprefab en la ranura recurso prefabricado del módulo en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="d81f3-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="d81f3-131">Si hace clic en uno de los objetos y la versión de recurso prefabricado, el inspector cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="d81f3-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="d81f3-132">Haga clic, arrastre, suelte y suelte cada objeto en su ranura adecuada.</span><span class="sxs-lookup"><span data-stu-id="d81f3-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="d81f3-133">Haga clic en la flecha situada a la izquierda de MixedRealityPlayspace y mueva el objeto de juego secundario MainCamera hacia abajo en SharedPlayground recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="d81f3-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="d81f3-134">A continuación, elimine el recurso prefabricado, MixedRealityPlayspace seleccionando recurso prefabricado y puntee en "eliminar" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="d81f3-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="d81f3-136">Asegúrese de que las posiciones de cámara y SharedPlayground principales están establecidas en 0, 0 y 0.</span><span class="sxs-lookup"><span data-stu-id="d81f3-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="d81f3-137">Seleccione el objeto "SharedPlayground" y haga clic con el botón secundario del mouse para seleccionar la opción "crear vacío" para crear un objeto de juego vacío como elemento secundario del objeto de juego "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="d81f3-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="d81f3-139">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="d81f3-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="d81f3-140">Además, haga clic en Agregar componente y busque el componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="d81f3-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="d81f3-141">Selecciónelo y agréguelo al objeto.</span><span class="sxs-lookup"><span data-stu-id="d81f3-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="d81f3-143">En el panel Proyecto de la carpeta Prefabs, arrastre la tabla recurso prefabricado hasta el objeto secundario "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="d81f3-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)
   
12. <span data-ttu-id="d81f3-145">Abra "Rocket Launcher_Complete Variant" recurso prefabricado from assets-> Resources-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d81f3-145">Open the "Rocket Launcher_Complete Variant" prefab from Assets->Resources->Prefabs.</span></span>

13. <span data-ttu-id="d81f3-146">Seleccione el GameObject "LunarModule" y agregue los dos componentes siguientes: "Photon Transform View" y "Photon View".</span><span class="sxs-lookup"><span data-stu-id="d81f3-146">Select the "LunarModule" GameObject and add the following two components: "Photon Transform View" and "Photon View".</span></span>

14. <span data-ttu-id="d81f3-147">Con el GameObject "LunarModule" todavía seleccionado, arrastre el componente "vista de transformación de Photon" a la ranura "componentes observados" del componente "vista Photon".</span><span class="sxs-lookup"><span data-stu-id="d81f3-147">With the "LunarModule" GameObject still selected, drag the "Photon Transform View" component into the "Observed Components" slot in the "Photon View" component.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d81f3-148">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="d81f3-148">Congratulations</span></span>

<span data-ttu-id="d81f3-149">Una vez completado, busque el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="d81f3-149">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="d81f3-150">Después de esto, todos los usuarios que se unen al proyecto de Unity pueden mover el selector lunar.</span><span class="sxs-lookup"><span data-stu-id="d81f3-150">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="d81f3-151">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="d81f3-151">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="d81f3-152">Estos conceptos sirven como bloques de creación fundamentales para experiencias de colaboración compartidas completas.</span><span class="sxs-lookup"><span data-stu-id="d81f3-152">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="d81f3-153">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos para que los usuarios locales no se puedan ver entre sí y objetos en el mismo lugar dentro de la mundo físico.</span><span class="sxs-lookup"><span data-stu-id="d81f3-153">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="d81f3-154">Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="d81f3-154">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="d81f3-155">En este módulo, lograremos esto mediante el uso de [delimitadores espaciales](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) de Azure que se implementarán en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="d81f3-155">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="d81f3-156">Antes de continuar con la siguiente lección, deberá completar el módulo de aprendizaje de ASA que trata los conceptos básicos de ASA, la creación de cuentas y recursos de Azure, así como otros bloques de edificios fundamentales necesarios antes de que podamos integrarlo en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="d81f3-156">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="d81f3-157">[Lección siguiente: 5. integración de los anclajes espaciales de Azure en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="d81f3-157">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
