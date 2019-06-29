---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465215"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="5c862-104">**Conectar varios usuarios**</span><span class="sxs-lookup"><span data-stu-id="5c862-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="5c862-105">En esta lección, se obtenga información sobre cómo conectar varios usuarios como parte de una experiencia compartida en vivo.</span><span class="sxs-lookup"><span data-stu-id="5c862-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="5c862-106">Al final de esta lección, podrá abrir la aplicación en varios dispositivos y vea avatar, representado por una esfera, representaciones de cada persona que se une.</span><span class="sxs-lookup"><span data-stu-id="5c862-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="5c862-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="5c862-107">Objectives:</span></span>

- <span data-ttu-id="5c862-108">Configurar el juego de palabras dentro de la aplicación</span><span class="sxs-lookup"><span data-stu-id="5c862-108">Configure PUN within your application</span></span>
- <span data-ttu-id="5c862-109">Configurar los jugadores</span><span class="sxs-lookup"><span data-stu-id="5c862-109">Configure players</span></span>
- <span data-ttu-id="5c862-110">Obtenga información sobre cómo conectar varios usuarios en una experiencia compartido</span><span class="sxs-lookup"><span data-stu-id="5c862-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="5c862-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="5c862-111">Instructions</span></span>

1. <span data-ttu-id="5c862-112">En los recursos -> recursos -> carpeta prefabricados en el panel proyecto, arrastre y coloque el prefabricado NetworkLobby en a la jerarquía, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="5c862-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="5c862-114">Al expandir NetworkLobby, verá un objeto secundario llamado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="5c862-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="5c862-115">Con NetworkRoom seleccionado, vaya al panel de Inspector y haga clic en Agregar componente.</span><span class="sxs-lookup"><span data-stu-id="5c862-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="5c862-116">Buscar PhotonView y agregue el componente.</span><span class="sxs-lookup"><span data-stu-id="5c862-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="5c862-118">Crear un nuevo objeto de juego vacío en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="5c862-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="5c862-119">Haga clic con el botón derecho en la jerarquía y seleccione vacía en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="5c862-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="5c862-120">Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="5c862-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="5c862-122">Haga clic en Agregar componente y escriba sincronización neto genérico. Seleccione la clase genérica sincronización Net.</span><span class="sxs-lookup"><span data-stu-id="5c862-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="5c862-123">Cuando aparezca la clase, haga clic en la casilla de verificación de usuario para activarlo.</span><span class="sxs-lookup"><span data-stu-id="5c862-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="5c862-125">Haga clic en Agregar componente nuevo y escriba Photon View.</span><span class="sxs-lookup"><span data-stu-id="5c862-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="5c862-126">Seleccione la clase de vista Photon que aparece en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="5c862-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="5c862-128">Haga clic en el icono del archivo para la clase genérica sincronización Net.</span><span class="sxs-lookup"><span data-stu-id="5c862-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="5c862-129">Arrastre y colóquelo en el campo de la vista Photon componentes observado.</span><span class="sxs-lookup"><span data-stu-id="5c862-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="5c862-131">A continuación, creamos esferas para representar a cada persona que une una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="5c862-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="5c862-132">Haga clic en el objeto PhotonUser que acaba de crear y scrolldown a "esfera objeto 3D y haga clic en.</span><span class="sxs-lookup"><span data-stu-id="5c862-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="5c862-133">Esto creará un objeto de juego esfera como elemento secundario del objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="5c862-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="5c862-135">Escalar la esfera hasta x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="5c862-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="5c862-137">Arrastre el objeto de juego PhotonUser en la carpeta prefabricados en el panel de proyecto y, a continuación, eliminarlo de la escena.</span><span class="sxs-lookup"><span data-stu-id="5c862-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="5c862-138">Ahora hemos creado un prefabricado que se puede usar al generar o crear una instancia de nuevos jugadores en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="5c862-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="5c862-140">Nota: asegúrese de que el objeto de juego ha copiado correctamente en la carpeta prefabricados antes de eliminarlos de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="5c862-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="5c862-141">Crear un nuevo objeto en la jerarquía, siga las instrucciones en el paso 3 y asígnele el nombre SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="5c862-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="5c862-142">A continuación, haga clic en Agregar componente, busque el Administrador de red genéricos y haga clic en él para agregar el componente del Administrador de red genéricos.</span><span class="sxs-lookup"><span data-stu-id="5c862-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="5c862-143">Cambiar la posición del objeto a x = 0, y = 0 y, z = 0.</span><span class="sxs-lookup"><span data-stu-id="5c862-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="5c862-145">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="5c862-145">Congratulations</span></span>

<span data-ttu-id="5c862-146">Una vez que finalizan todos los pasos anteriores, y el proceso de compilación también está completando, presione el botón Reproducir y conectar el 2 de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c862-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="5c862-147">Debería ver una esfera mover mover la cabeza.</span><span class="sxs-lookup"><span data-stu-id="5c862-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="5c862-148">Se mostrará para cualquier usuario que se une a su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="5c862-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="5c862-149">[Siguiente lección: Sharing(Photon) lección 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="5c862-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

