---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327715"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="be20a-104">Sincronizar los movimientos de objetos compartidos</span><span class="sxs-lookup"><span data-stu-id="be20a-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="be20a-105">En esta lección, aprenderemos a compartir los movimientos de objetos para que puedan colaborar juntos y ver los demás interacciones todos los participantes de una sesión compartida.</span><span class="sxs-lookup"><span data-stu-id="be20a-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="be20a-106">En esta lección se basa en el Lunar iniciador que se compiló como parte de la [Base módulo tutoriales](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="be20a-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="be20a-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="be20a-107">Objectives:</span></span>

- <span data-ttu-id="be20a-108">Importar el iniciador Lunar completado como el modelo 3D para compartirse</span><span class="sxs-lookup"><span data-stu-id="be20a-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="be20a-109">Configurar el proyecto para compartir los movimientos del modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="be20a-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="be20a-110">Obtenga información sobre cómo compilar una aplicación de colaboración multiusuario básica</span><span class="sxs-lookup"><span data-stu-id="be20a-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="be20a-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="be20a-111">Instructions</span></span>

1. <span data-ttu-id="be20a-112">Guarde la escena de la lección anterior (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="be20a-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="be20a-113">Es posible que denominó "HLSharedProjectMainPart4.unity" para que resulte más fácil encontrar cuando necesite de nuevo.</span><span class="sxs-lookup"><span data-stu-id="be20a-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="be20a-114">Elimine el objeto "NetworkLobby" (, selecciónela y presione SUPR).</span><span class="sxs-lookup"><span data-stu-id="be20a-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="be20a-115">Además, vaya a la carpeta "prefabricados" de la lección 2 y elimine el recurso prefabricado "NetworkLobby" desde allí también.</span><span class="sxs-lookup"><span data-stu-id="be20a-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="be20a-117">Importar un nuevo paquete personalizado (por ejemplo, paso 2 de la lección 2) e importar el [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) y [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="be20a-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="be20a-119">Ahora, en la carpeta "prefabricados", arrastre el nuevo recurso prefabricado de "NetworkLobby" en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="be20a-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="be20a-121">Nota: los dos paquetes que se ha importado en los pasos anteriores actualizan el recurso prefabricado "NetworkLobby".</span><span class="sxs-lookup"><span data-stu-id="be20a-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="be20a-122">¡Le evita tener que escribir mucho!</span><span class="sxs-lookup"><span data-stu-id="be20a-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="be20a-123">Ahora, haga clic en la flecha situada a la izquierda de "MixedRealityPlayspace" y mover el objeto de juego secundarios, "MainCamera" hacia abajo en el prefabricado "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="be20a-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="be20a-124">A continuación, elimine el prefabricado "MixedRealityPlayspace" (para eliminar, seleccione el recurso prefabricado y pulse "eliminar" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="be20a-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="be20a-126">Cree un nuevo objeto de juego establecer como objeto secundario al objeto primario "SharedPlayground" (para crear un nuevo objeto, haga clic con el botón derecho en el objeto primario y seleccione "Crear vacío").</span><span class="sxs-lookup"><span data-stu-id="be20a-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="be20a-127">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto para "TableAnchor" en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="be20a-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="be20a-128">Además, haga clic en "agregar el componente" y busque el componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="be20a-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="be20a-129">Selecciónelo y agregarlo al objeto.</span><span class="sxs-lookup"><span data-stu-id="be20a-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="be20a-131">Nota: establezca el posicionamiento a x = 1, y =-0,55 y, z = 2.</span><span class="sxs-lookup"><span data-stu-id="be20a-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="be20a-132">Además, establezca la rotación en y = 90.</span><span class="sxs-lookup"><span data-stu-id="be20a-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="be20a-134">Ahora en el panel de proyecto, en la carpeta "prefabricados", arrastre el recurso prefabricado "table" en el objeto secundario de "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="be20a-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="be20a-136">Seleccione "NetworkRoom", un objeto secundario en "NetworkLobby" en la jerarquía y haga clic en "agregar el componente" en el panel de inspector y busque "PhotonView" y agregue el script para el "*NetworkRoom*" objeto.</span><span class="sxs-lookup"><span data-stu-id="be20a-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="be20a-138">Por último, en el objeto "DebugWindow", cambie el ancho en 80 y el alto a 10.</span><span class="sxs-lookup"><span data-stu-id="be20a-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="be20a-140">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="be20a-140">Congratulations</span></span>

<span data-ttu-id="be20a-141">Una vez completado, todos los usuarios que se unen a su proyecto Unity pueden moverse el iniciador Lunar.</span><span class="sxs-lookup"><span data-stu-id="be20a-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="be20a-142">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="be20a-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="be20a-143">Estos conceptos sirven como los bloques de creación fundamentales para las experiencias de colaboración compartido completa.</span><span class="sxs-lookup"><span data-stu-id="be20a-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="be20a-144">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos de objetos relativos, la aplicación es todavía no se puede alinear con precisión los avatares y objetos para que los usuarios locales ven entre sí y objetos en el mismo lugar dentro de la física mundo.</span><span class="sxs-lookup"><span data-stu-id="be20a-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="be20a-145">Para fijar un experiencias compartidas locales, cada dispositivo requiere una comprensión común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="be20a-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="be20a-146">En este módulo, conseguiremos esto mediante [Azure espacial delimitadores](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que se implementará en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="be20a-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="be20a-147">Antes de continuar con la siguiente lección, necesitaremos completar el módulo de aprendizaje de ASA, que tratará aspectos básicos ASA, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales necesitan antes de que podemos integrar esto en nuestra experiencia compartido.</span><span class="sxs-lookup"><span data-stu-id="be20a-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="be20a-148">[Siguiente lección: Sharing(Photon) lección 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="be20a-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

