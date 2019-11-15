---
title: 'Tutoriales de funcionalidades para varios usuarios: 4. Compartir movimientos de objetos con varios usuarios'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 34b8165888c13b0c94be8951d5a4fdc07fab5308
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106035"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="8faf3-105">4. compartir movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="8faf3-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="8faf3-106">En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una sesión compartida puedan colaborar y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="8faf3-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="8faf3-107">Esta lección se basa en el selector lunar que se compiló como parte de los [Tutoriales del módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="8faf3-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="8faf3-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8faf3-108">Objectives:</span></span>

- <span data-ttu-id="8faf3-109">Traer el selector lunar como el modelo 3D que se va a compartir</span><span class="sxs-lookup"><span data-stu-id="8faf3-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="8faf3-110">Configurar el proyecto para compartir los movimientos del modelo 3D</span><span class="sxs-lookup"><span data-stu-id="8faf3-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="8faf3-111">Obtenga información sobre cómo crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="8faf3-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="8faf3-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8faf3-112">Instructions</span></span>


1. <span data-ttu-id="8faf3-113">Guarde la escena de la lección anterior (control + S).</span><span class="sxs-lookup"><span data-stu-id="8faf3-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="8faf3-114">Puede asignarle el nombre HLSharedProjectMainPart4. Unity para que sea más fácil encontrarlo cuando lo necesite.</span><span class="sxs-lookup"><span data-stu-id="8faf3-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="8faf3-115">En la ventana proyecto, en la carpeta assets-> scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que esté usando.</span><span class="sxs-lookup"><span data-stu-id="8faf3-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="8faf3-117">En las líneas 34 y 38, quite "//" para activar el código para la tabla que utilizará en esta lección.</span><span class="sxs-lookup"><span data-stu-id="8faf3-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="8faf3-118">A continuación, guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="8faf3-118">Next, save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="8faf3-120">En la ventana proyecto, haga doble clic en el archivo PhotonRoom.cs en la carpeta assets-> scripts para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8faf3-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="8faf3-122">Al igual que en el paso 3, es necesario quitar "//" para activar el código en las líneas 25, 26 y 106.</span><span class="sxs-lookup"><span data-stu-id="8faf3-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="8faf3-125">En la vista de jerarquía, seleccione el objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="8faf3-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="8faf3-127">En la vista de proyecto, vaya a activos-> recursos-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="8faf3-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="8faf3-128">En primer lugar, arrastre y coloque la tabla recurso prefabricado en la ranura Tableprefab en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="8faf3-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="8faf3-129">A continuación, arrastre y coloque RocketLauncherCompleteVariantprefab en la ranura recurso prefabricado del módulo en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="8faf3-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

<span data-ttu-id="8faf3-131">Nota: Si hace clic en uno de los objetos y la versión de recurso prefabricado, el inspector cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="8faf3-131">Note: If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="8faf3-132">Haga clic, arrastre, suelte y suelte cada objeto en su ranura adecuada.</span><span class="sxs-lookup"><span data-stu-id="8faf3-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="8faf3-133">Haga clic en la flecha situada a la izquierda de MixedRealityPlayspace y mueva el objeto de juego secundario MainCamera hacia abajo en SharedPlayground recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="8faf3-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="8faf3-134">A continuación, elimine el recurso prefabricado, MixedRealityPlayspace seleccionando recurso prefabricado y puntee en "eliminar" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="8faf3-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="8faf3-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8faf3-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="8faf3-136">Nota: Asegúrese de que las posiciones de cámara y SharedPlayground principales están establecidas en 0, 0,0.</span><span class="sxs-lookup"><span data-stu-id="8faf3-136">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="8faf3-137">Seleccione el objeto "SharedPlayground" y haga clic con el botón secundario del mouse para seleccionar la opción "crear vacío" para crear un objeto de juego vacío como elemento secundario del objeto de juego "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="8faf3-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="8faf3-139">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="8faf3-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="8faf3-140">Además, haga clic en Agregar componente y busque el componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="8faf3-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="8faf3-141">Selecciónelo y agréguelo al objeto.</span><span class="sxs-lookup"><span data-stu-id="8faf3-141">Select it and add it to the object.</span></span> 

![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="8faf3-143">En el panel Proyecto de la carpeta Prefabs, arrastre la tabla recurso prefabricado hasta el objeto secundario "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="8faf3-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="8faf3-145">En el objeto DebugWindow, cambie el ancho a 50 y el alto a 20.</span><span class="sxs-lookup"><span data-stu-id="8faf3-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="8faf3-147">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8faf3-147">Congratulations</span></span>


<span data-ttu-id="8faf3-148">Una vez completado, busque el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="8faf3-148">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="8faf3-149">Después de esto, todos los usuarios que se unen al proyecto de Unity pueden mover el selector lunar.</span><span class="sxs-lookup"><span data-stu-id="8faf3-149">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="8faf3-150">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="8faf3-150">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="8faf3-151">Estos conceptos sirven como bloques de creación fundamentales para experiencias de colaboración compartidas completas.</span><span class="sxs-lookup"><span data-stu-id="8faf3-151">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="8faf3-152">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos para que los usuarios locales no se puedan ver entre sí y objetos en el mismo lugar dentro de la mundo físico.</span><span class="sxs-lookup"><span data-stu-id="8faf3-152">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="8faf3-153">Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="8faf3-153">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="8faf3-154">En este módulo, lograremos esto mediante el uso de [delimitadores espaciales](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) de Azure que se implementarán en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="8faf3-154">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="8faf3-155">Antes de continuar con la siguiente lección, deberá completar el módulo de aprendizaje de ASA que trata los conceptos básicos de ASA, la creación de cuentas y recursos de Azure, así como otros bloques de edificios fundamentales necesarios antes de que podamos integrarlo en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="8faf3-155">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="8faf3-156">[Lección siguiente: 5. integración de los anclajes espaciales de Azure en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="8faf3-156">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

