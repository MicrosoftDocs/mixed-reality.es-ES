---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326881"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="8ba6e-104">**Conectar varios usuarios**</span><span class="sxs-lookup"><span data-stu-id="8ba6e-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="8ba6e-105">En esta lección, se obtendrá información sobre cómo conectar varios usuarios como parte de una experiencia compartida en vivo.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="8ba6e-106">Al final de esta lección, podrá abrir la aplicación en varios dispositivos y ver representaciones "avatar" de cada persona que une (avatares representados por una esfera).</span><span class="sxs-lookup"><span data-stu-id="8ba6e-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="8ba6e-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="8ba6e-107">Objectives:</span></span>

- <span data-ttu-id="8ba6e-108">Configurar el juego de palabras dentro de la aplicación</span><span class="sxs-lookup"><span data-stu-id="8ba6e-108">Configure PUN within your application</span></span>
- <span data-ttu-id="8ba6e-109">Configurar los jugadores</span><span class="sxs-lookup"><span data-stu-id="8ba6e-109">Configure players</span></span>
- <span data-ttu-id="8ba6e-110">Obtenga información sobre cómo conectar varios usuarios en una experiencia compartido</span><span class="sxs-lookup"><span data-stu-id="8ba6e-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="8ba6e-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8ba6e-111">Instructions</span></span>

1. <span data-ttu-id="8ba6e-112">En los recursos > recursos > prefabricados carpeta del panel proyecto, arrastrar y colocar la "NetworkLobby" prefabricado en a la jerarquía, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="8ba6e-114">Al expandir el prefabricado "NetworkLobby", debería ver un objeto secundario denominado "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="8ba6e-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="8ba6e-115">Con él seleccionado, vaya al panel de inspector y haga clic en "Agregar el componente".</span><span class="sxs-lookup"><span data-stu-id="8ba6e-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="8ba6e-116">Busque "PhotonView" y agregue el componente.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="8ba6e-118">Crear un nuevo objeto de juego vacío en la jerarquía (haga clic con el botón derecho en la jerarquía y seleccione "Empty" en el menú contextual).</span><span class="sxs-lookup"><span data-stu-id="8ba6e-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="8ba6e-119">Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="8ba6e-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="8ba6e-121">A continuación, deseamos crear ámbitos para representar a cada persona que une una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="8ba6e-122">A la derecha, haga clic en el objeto "PhotonUser" que acaba de crear, ir a "objeto 3D" y haga clic en "Esfera".</span><span class="sxs-lookup"><span data-stu-id="8ba6e-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="8ba6e-123">Esto creará un objeto de juego esfera como elemento secundario del objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="8ba6e-125">Escalar la esfera hasta x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="8ba6e-127">Arrastre el objeto de juego "PhotonUser" en la carpeta "prefabricados" en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="8ba6e-128">A continuación, eliminarlo de la escena.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-128">Then, delete it from the scene.</span></span> <span data-ttu-id="8ba6e-129">Ahora hemos creado un prefabricado que se usará al generar o crear una instancia de nuevos jugadores en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="8ba6e-131">Nota: asegúrese de que el objeto de juego ha copiado correctamente en la carpeta "prefabs" antes de eliminarlos de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="8ba6e-132">Cree un nuevo objeto en la jerarquía (con instrucciones similares a la de paso 3) y asígnele el nombre "SharedPlayground."</span><span class="sxs-lookup"><span data-stu-id="8ba6e-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="8ba6e-133">A continuación, haga clic en "Agregar componente" y busque "Administrador de red genéricos" y haga clic en él para agregar el componente del Administrador de red genéricos.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="8ba6e-134">Cambiar la posición del objeto a x = 0, y = 0 y, z = 0.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="8ba6e-136">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8ba6e-136">Congratulations</span></span>

<span data-ttu-id="8ba6e-137">Una vez que finalizan todos los pasos anteriores, y el proceso de compilación ha finalizado, cuando presione el botón play y se conecta el 2 de HoloLens, debería ver una esfera mover mover la cabeza!</span><span class="sxs-lookup"><span data-stu-id="8ba6e-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="8ba6e-138">Se mostrará para cualquier usuario que se une a su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="8ba6e-139">[Siguiente lección: Sharing(Photon) lección 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="8ba6e-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

