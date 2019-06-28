---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416016"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="2d4d2-104">Sincronizar los movimientos de objetos compartidos</span><span class="sxs-lookup"><span data-stu-id="2d4d2-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="2d4d2-105">En esta lección, aprenderemos a compartir los movimientos de objetos para que puedan colaborar juntos y ver los demás interacciones todos los participantes de una sesión compartida.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="2d4d2-106">En esta lección se basa en el Lunar iniciador que se compiló como parte de la [Base módulo tutoriales](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="2d4d2-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="2d4d2-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="2d4d2-107">Objectives:</span></span>

- <span data-ttu-id="2d4d2-108">Vuelva a poner en el Lunar iniciador como el modelo 3D para compartirse</span><span class="sxs-lookup"><span data-stu-id="2d4d2-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="2d4d2-109">Configurar el proyecto para compartir los movimientos del modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="2d4d2-110">Obtenga información sobre cómo compilar una aplicación de colaboración multiusuario básica</span><span class="sxs-lookup"><span data-stu-id="2d4d2-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="2d4d2-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="2d4d2-111">Instructions</span></span>

1. <span data-ttu-id="2d4d2-112">Guarde la escena de la lección anterior (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="2d4d2-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="2d4d2-113">Es posible que denominó "HLSharedProjectMainPart4.unity" para que resulte más fácil encontrar cuando necesite de nuevo.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="2d4d2-114">En la ventana de proyecto, en los activos > carpeta de Scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o que alguna vez code editor que está utilizando.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="2d4d2-115">En las líneas 34 y 38, quite la "/ /" para activar el código de la tabla que se utilizará en esta lección.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="2d4d2-116">A continuación, guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="2d4d2-117">En la ventana de proyecto, haga doble clic en el archivo PhotonRoom.cs en los activos > carpeta de secuencias de comandos para volver a abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="2d4d2-118">Al igual que en el paso 3 se deberá quitar la "/ /" para activar el código en líneas 106, 25 y 26.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="2d4d2-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="2d4d2-119">En la vista de jerarquía, seleccione el objeto NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="2d4d2-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="2d4d2-120">En la vista del proyecto, vaya a activos > recursos > prefabricados.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="2d4d2-121">En primer lugar, arrastre y coloque el recurso prefabricado de tabla a la ranura "Tableprefab" en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="2d4d2-122">A continuación arrastre y coloque el recurso prefabricado LunarModule a la ranura "Módulo prefabricado" en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="2d4d2-123">Nota: Si hace clic en uno de los objetos prefabricados y versión, el inspector se cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="2d4d2-124">Haga clic en, arrastrar, colocar y liberar cada objeto en su espacio adecuado.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="2d4d2-125">Ahora, haga clic en la flecha situada a la izquierda de "MixedRealityPlayspace" y mover el objeto de juego secundarios, "MainCamera" hacia abajo en el prefabricado "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="2d4d2-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="2d4d2-126">A continuación, elimine el prefabricado "MixedRealityPlayspace" (para eliminar, seleccione el recurso prefabricado y pulse "eliminar" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="2d4d2-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="2d4d2-128">Nota:  Asegúrese de que se establecen las posiciones de la cámara principal y SharedPlayground en 0,0,0.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="2d4d2-129">Cree un nuevo objeto de juego establecer como objeto secundario al objeto primario "SharedPlayground" (para crear un nuevo objeto, haga clic con el botón derecho en el objeto primario y seleccione "Crear vacío").</span><span class="sxs-lookup"><span data-stu-id="2d4d2-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="2d4d2-130">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto para "TableAnchor" en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="2d4d2-131">Además, haga clic en "agregar el componente" y busque el componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="2d4d2-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="2d4d2-132">Selecciónelo y agregarlo al objeto.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="2d4d2-134">Nota: establezca el posicionamiento a x = 1, y =-0,55 y, z = 2.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="2d4d2-135">Además, establezca la rotación en y = 90.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="2d4d2-137">Ahora en el panel de proyecto, en la carpeta "prefabricados", arrastre el recurso prefabricado "table" en el objeto secundario de "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="2d4d2-139">Por último, en el objeto "DebugWindow", cambie el ancho en 80 y el alto a 10.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="2d4d2-141">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2d4d2-141">Congratulations</span></span>

<span data-ttu-id="2d4d2-142">Una vez completado, todos los usuarios que se unen a su proyecto Unity pueden moverse el iniciador Lunar.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="2d4d2-143">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="2d4d2-144">Estos conceptos sirven como los bloques de creación fundamentales para las experiencias de colaboración compartido completa.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="2d4d2-145">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos de objetos relativos, la aplicación es todavía no se puede alinear con precisión los avatares y objetos para que los usuarios locales ven entre sí y objetos en el mismo lugar dentro de la física mundo.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="2d4d2-146">Para fijar un experiencias compartidas locales, cada dispositivo requiere una comprensión común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="2d4d2-147">En este módulo, conseguiremos esto mediante [Azure espacial delimitadores](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que se implementará en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="2d4d2-148">Antes de continuar con la siguiente lección, necesitaremos completar el módulo de aprendizaje de ASA, que tratará aspectos básicos ASA, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales necesitan antes de que podemos integrar esto en nuestra experiencia compartido.</span><span class="sxs-lookup"><span data-stu-id="2d4d2-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="2d4d2-149">[Siguiente lección: Sharing(Photon) lección 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="2d4d2-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

