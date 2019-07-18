---
title: Módulo de uso compartido de aprendizaje MR para HoloLens 2
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293666"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="f6d5f-104">Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="f6d5f-104">Connecting multiple users</span></span>

<span data-ttu-id="f6d5f-105">En esta lección, aprenderá a conectar varios usuarios como parte de una experiencia compartida en directo.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="f6d5f-106">Al final de esta lección, podrá abrir la aplicación en varios dispositivos y ver el Avatar, representado por una esfera, representaciones de cada persona que se une.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="f6d5f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f6d5f-107">Objectives:</span></span>

- <span data-ttu-id="f6d5f-108">Configuración de BURDO dentro de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f6d5f-108">Configure PUN within your application</span></span>
- <span data-ttu-id="f6d5f-109">Configuración de reproductores</span><span class="sxs-lookup"><span data-stu-id="f6d5f-109">Configure players</span></span>
- <span data-ttu-id="f6d5f-110">Obtenga información acerca de cómo conectar varios usuarios en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="f6d5f-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="f6d5f-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="f6d5f-111">Instructions</span></span>

1. <span data-ttu-id="f6d5f-112">En la carpeta assets-> Resources-> Prefabs en el panel Proyecto, arrastre y coloque el NetworkLobby recurso prefabricado en la jerarquía, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="f6d5f-114">Al expandir NetworkLobby, verá un objeto secundario denominado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="f6d5f-115">Con NetworkRoom seleccionado, vaya al panel de inspectores y haga clic en Agregar componente.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="f6d5f-116">Busque PhotonView y agregue el componente.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-116">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="f6d5f-118">Cree un nuevo objeto de juego vacío en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="f6d5f-119">Haga clic con el botón derecho en la jerarquía y seleccione vacío en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="f6d5f-120">Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y asigne al objeto el nombre PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="f6d5f-122">Haga clic en Agregar componente y escriba Generic net Sync. Seleccione la clase de sincronización de red genérica.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="f6d5f-123">Cuando aparezca la clase, haga clic en la casilla usuario para activarla.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-123">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="f6d5f-125">Vuelva a hacer clic en Agregar componente y escriba vista de Photon.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="f6d5f-126">Seleccione la clase de vista Photon que aparece en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-126">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="f6d5f-128">Haga clic en el icono de archivo de la clase net Sync genérica.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="f6d5f-129">Arrástrelo y colóquelo en el campo componentes observados de la vista Photon.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-129">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="f6d5f-131">A continuación, creamos esferas para representar a cada persona que se une a una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="f6d5f-132">Haga clic con el botón derecho en el objeto PhotonUser que acaba de crear y scrollDown en "objeto 3D" y haga clic en sphere.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="f6d5f-133">Se creará un objeto de juego de esfera como elemento secundario del objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="f6d5f-135">Escale la esfera hacia abajo hasta x = 0.06, y = 0.06, ad z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="f6d5f-137">Arrastre el objeto de juego PhotonUser a la carpeta Prefabs del panel Proyecto y, a continuación, elimínelo de la escena.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="f6d5f-138">Ahora hemos creado un recurso prefabricado que se puede usar al generar o crear instancias de nuevos jugadores en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="f6d5f-140">Nota: Asegúrese de que el objeto de juego se ha copiado correctamente en la carpeta Prefabs antes de eliminarlo de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="f6d5f-141">Cree un nuevo objeto en la jerarquía siguiendo las instrucciones del paso 3 y asígnele el nombre SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="f6d5f-142">A continuación, haga clic en Agregar componente y busque administrador de red genérico y haga clic en él para agregar el componente de administrador de red genérico.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="f6d5f-143">Cambie la posición del objeto a x = 0, y = 0 y z = 0.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="f6d5f-145">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="f6d5f-145">Congratulations</span></span>

<span data-ttu-id="f6d5f-146">Una vez completados todos los pasos anteriores, también se completa el proceso de compilación, presione el botón reproducir y conecte su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="f6d5f-147">Debería ver una esfera desplazada a medida que mueve el cabezal.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="f6d5f-148">Esto se mostrará para cualquier usuario que se una a su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="f6d5f-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="f6d5f-149">[Siguiente lección: Lección 4 de uso compartido (Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="f6d5f-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

