---
title: 'Tutoriales de funcionalidades para varios usuarios: 4. Compartir movimientos de objetos con varios usuarios'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2e676d319ba7221cf9549b200b3d748f26025aa7
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701900"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="98f94-105">4. Compartir movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="98f94-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="98f94-106">En este tutorial, aprenderá a compartir los movimientos de los objetos para que todos los participantes de una sesión compartida puedan colaborar juntos y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="98f94-106">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="98f94-107">Esta lección se basa en el selector lunar que se compiló como parte de los tutoriales del [módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="98f94-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="98f94-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="98f94-108">Objectives:</span></span>

- <span data-ttu-id="98f94-109">Traer el selector lunar como el modelo 3D que se va a compartir</span><span class="sxs-lookup"><span data-stu-id="98f94-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="98f94-110">Configure el proyecto para compartir los movimientos del modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="98f94-110">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="98f94-111">Obtenga información sobre cómo crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="98f94-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="98f94-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="98f94-112">Instructions</span></span>


1. <span data-ttu-id="98f94-113">Guarde la escena de la lección anterior (control + S).</span><span class="sxs-lookup"><span data-stu-id="98f94-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="98f94-114">Puede asignarle el nombre HLSharedProjectMainPart4. Unity para que sea más fácil encontrarlo cuando lo necesite.</span><span class="sxs-lookup"><span data-stu-id="98f94-114">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="98f94-115">En la ventana proyecto, en la carpeta assets-> scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que esté usando.</span><span class="sxs-lookup"><span data-stu-id="98f94-115">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="98f94-117">En las líneas 34 y 38, quite//para activar el código para la tabla que se va a usar en esta lección.</span><span class="sxs-lookup"><span data-stu-id="98f94-117">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="98f94-118">a continuación, guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="98f94-118">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="98f94-120">En la ventana proyecto, haga doble clic en el archivo PhotonRoom.cs en la carpeta assets-> scripts para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98f94-120">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="98f94-122">Al igual que en el paso 3, es necesario quitar//para activar el código de las líneas 25, 26 y 106.</span><span class="sxs-lookup"><span data-stu-id="98f94-122">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="98f94-125">En la vista de jerarquía, seleccione el objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="98f94-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="98f94-127">En la vista de proyecto, vaya a activos-> recursos-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="98f94-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="98f94-128">En primer lugar, arrastre y coloque la tabla recurso prefabricado en la ranura Tableprefab en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="98f94-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="98f94-129">A continuación, arrastre y coloque RocketLauncherCompleteVariantprefab en la ranura recurso prefabricado del módulo en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="98f94-129">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="98f94-131">Nota: Si hace clic en uno de los objetos y la versión de recurso prefabricado, el inspector cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="98f94-131">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="98f94-132">Haga clic, arrastre, suelte y suelte cada objeto en su ranura adecuada.</span><span class="sxs-lookup"><span data-stu-id="98f94-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="98f94-133">Haga clic en la flecha situada a la izquierda de MixedRealityPlayspace y mueva el objeto secundario Game, MainCamera al SharedPlayground recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="98f94-133">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="98f94-134">A continuación, elimine el recurso prefabricado, MixedRealityPlayspace, para eliminarlo, seleccione el recurso prefabricado y pulse en "eliminar" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="98f94-134">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="98f94-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="98f94-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="98f94-136">Nota:  Asegúrese de que las posiciones de cámara y SharedPlayground principales están establecidas en 0, 0 y 0.</span><span class="sxs-lookup"><span data-stu-id="98f94-136">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="98f94-137">Cree un nuevo conjunto de objetos de juego como un objeto secundario para el objeto primario SharedPlayground con el fin de crear un nuevo objeto.</span><span class="sxs-lookup"><span data-stu-id="98f94-137">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="98f94-138">Haga clic con el botón derecho en el objeto primario y seleccione crear vacío.</span><span class="sxs-lookup"><span data-stu-id="98f94-138">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="98f94-139">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="98f94-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="98f94-140">Además, haga clic en Agregar componente y busque el componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="98f94-140">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="98f94-141">Selecciónelo y agréguelo al objeto.</span><span class="sxs-lookup"><span data-stu-id="98f94-141">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="98f94-143">Ahora, en el panel Proyecto de la carpeta Prefabs, arrastre la tabla recurso prefabricado al objeto secundario "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="98f94-143">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="98f94-145">Por último, en el objeto DebugWindow, cambie el ancho a 50 y el alto a 20.</span><span class="sxs-lookup"><span data-stu-id="98f94-145">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="98f94-147">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="98f94-147">Congratulations</span></span>


<span data-ttu-id="98f94-148">Una vez completado, todos los usuarios que se unen al proyecto de Unity pueden mover el selector lunar.</span><span class="sxs-lookup"><span data-stu-id="98f94-148">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="98f94-149">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="98f94-149">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="98f94-150">Estos conceptos sirven como bloques de creación fundamentales para experiencias de colaboración compartidas completas.</span><span class="sxs-lookup"><span data-stu-id="98f94-150">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="98f94-151">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos para que los usuarios locales puedan ver los objetos y los objetos en el mismo lugar dentro del físico WWPN.</span><span class="sxs-lookup"><span data-stu-id="98f94-151">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="98f94-152">Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="98f94-152">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="98f94-153">En este módulo, lograremos esto mediante el uso de delimitadores espaciales (ASA) de [Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) que se implementarán en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="98f94-153">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="98f94-154">Antes de continuar con la siguiente lección, deberá completar el módulo de aprendizaje de ASA que trata los conceptos básicos de ASA, la creación de cuentas y recursos de Azure y otros bloques de edificios fundamentales necesarios antes de que podamos integrar esto en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="98f94-154">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="98f94-155">[Siguiente lección: 5. Integración de Azure Spatial Anchors en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="98f94-155">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

