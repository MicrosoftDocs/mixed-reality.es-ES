---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465222"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="20548-104">Sincronizar los movimientos de objeto compartidas</span><span class="sxs-lookup"><span data-stu-id="20548-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="20548-105">En esta lección, se obtenga información sobre cómo compartir los movimientos de objetos para que puedan colaborar juntos y ver los demás interacciones todos los participantes de una sesión compartida.</span><span class="sxs-lookup"><span data-stu-id="20548-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="20548-106">En esta lección se basa en el Lunar iniciador que se compiló como parte de la [Base módulo tutoriales](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="20548-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="20548-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="20548-107">Objectives:</span></span>

- <span data-ttu-id="20548-108">Vuelva a poner en el lunar iniciador como el modelo 3D para compartirse</span><span class="sxs-lookup"><span data-stu-id="20548-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="20548-109">Configurar el proyecto para compartir los movimientos del modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="20548-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="20548-110">Obtenga información sobre cómo compilar una aplicación de colaboración multiusuario básica</span><span class="sxs-lookup"><span data-stu-id="20548-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="20548-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="20548-111">Instructions</span></span>


1. <span data-ttu-id="20548-112">Guarde la escena de la lección anterior (Control + S).</span><span class="sxs-lookup"><span data-stu-id="20548-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="20548-113">Puede asignarle el nombre HLSharedProjectMainPart4.unity para que resulte más fácil encontrar cuando lo necesite.</span><span class="sxs-lookup"><span data-stu-id="20548-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="20548-114">En la ventana de proyecto, en los recursos -> carpeta de Scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o que alguna vez code editor que está utilizando.</span><span class="sxs-lookup"><span data-stu-id="20548-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="20548-115">En líneas 34 y 38, quite la / / para activar el código de la tabla que se utilizará en esta lección.</span><span class="sxs-lookup"><span data-stu-id="20548-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="20548-116">a continuación, guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="20548-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="20548-117">En la ventana de proyecto, haga doble clic en el archivo PhotonRoom.cs en los recursos -> carpeta de Scripts para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20548-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="20548-118">Al igual que en el paso 3, se deberá quitar la / / para activar el código en líneas 106, 25 y 26.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="20548-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="20548-119">En la vista de jerarquía, seleccione el objeto NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="20548-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="20548-120">En la vista del proyecto, vaya a recursos -> recursos -> prefabricados.</span><span class="sxs-lookup"><span data-stu-id="20548-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="20548-121">En primer lugar, arrastre y coloque el recurso prefabricado de tabla a la ranura Tableprefab en la clase PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="20548-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="20548-122">A continuación arrastre y coloque el recurso prefabricado LunarModule a la ranura en la clase PhotonRoom prefabricado de módulo.</span><span class="sxs-lookup"><span data-stu-id="20548-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="20548-123">Nota: Si hace clic en uno de los objetos prefabricados y versión, el inspector se cambiará a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="20548-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="20548-124">Haga clic en, arrastrar, colocar y liberar cada objeto en su espacio adecuado.</span><span class="sxs-lookup"><span data-stu-id="20548-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="20548-125">Haga clic en la flecha situada a la izquierda del MixedRealityPlayspace y mover el objeto de juego secundarios, MainCamera hacia abajo en el prefabricado SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="20548-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="20548-126">A continuación, elimine el recurso prefabricado, MixedRealityPlayspace para eliminar, seleccione el recurso prefabricado y pulse "delete" en el teclado).</span><span class="sxs-lookup"><span data-stu-id="20548-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="20548-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="20548-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="20548-128">Nota:  Asegúrese de que se establecen las posiciones de la cámara principal y SharedPlayground en 0,0,0.</span><span class="sxs-lookup"><span data-stu-id="20548-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="20548-129">Cree un nuevo objeto de juego que se establece como un objeto secundario al objeto primario SharedPlayground para crear un nuevo objeto.</span><span class="sxs-lookup"><span data-stu-id="20548-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="20548-130">Haga clic con el botón derecho en el objeto primario y seleccione Crear vacío.</span><span class="sxs-lookup"><span data-stu-id="20548-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="20548-131">Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel del Inspector.</span><span class="sxs-lookup"><span data-stu-id="20548-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="20548-132">Además, haga clic en Agregar componente y busque el componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="20548-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="20548-133">Selecciónelo y agregarlo al objeto.</span><span class="sxs-lookup"><span data-stu-id="20548-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="20548-135">Nota: Establecer la posición a x = 1, y =-0,55 y, z = 2.</span><span class="sxs-lookup"><span data-stu-id="20548-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="20548-136">Además, establezca la rotación en y = 90.</span><span class="sxs-lookup"><span data-stu-id="20548-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="20548-138">Ahora, desde el panel de proyecto en la carpeta prefabricados, arrastre el recurso prefabricado de tabla en el objeto secundario de "TableAnchor" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="20548-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="20548-140">Por último, en el objeto DebugWindow, cambie el ancho en 80 y el alto a 10.</span><span class="sxs-lookup"><span data-stu-id="20548-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="20548-142">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="20548-142">Congratulations</span></span>


<span data-ttu-id="20548-143">Una vez completado, todos los usuarios que se unen a su proyecto Unity pueden moverse el iniciador lunar.</span><span class="sxs-lookup"><span data-stu-id="20548-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="20548-144">Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="20548-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="20548-145">Estos conceptos sirven como los bloques de creación fundamentales para las experiencias de colaboración completas y compartido.</span><span class="sxs-lookup"><span data-stu-id="20548-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="20548-146">Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos de objetos relativos, la aplicación es todavía no se puede alinear con precisión los avatares y objetos para que los usuarios locales ven entre sí y objetos en el mismo lugar dentro de la física mundo.</span><span class="sxs-lookup"><span data-stu-id="20548-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="20548-147">Para fijar un experiencias compartidas locales, cada dispositivo requiere una comprensión común del entorno físico.</span><span class="sxs-lookup"><span data-stu-id="20548-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="20548-148">En este módulo, se conseguirá esto usando [Azure espacial delimitadores](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) que se implementará en la lección siguiente.</span><span class="sxs-lookup"><span data-stu-id="20548-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="20548-149">Antes de continuar con la siguiente lección, necesitaremos completar el módulo de aprendizaje de ASA que abarca conceptos básicos ASA, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales necesitan antes de que podemos integrar esto en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="20548-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="20548-150">[Siguiente lección: Sharing(Photon) lección 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="20548-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

