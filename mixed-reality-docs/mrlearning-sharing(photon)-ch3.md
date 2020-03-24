---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031227"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="87569-105">3. Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="87569-105">3. Connecting multiple users</span></span>

<span data-ttu-id="87569-106">En esta lección, aprenderemos cómo conectar varios usuarios como parte de una experiencia compartida en directo.</span><span class="sxs-lookup"><span data-stu-id="87569-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="87569-107">Al final de esta lección, podrás abrir la aplicación en varios dispositivos y ver el avatar, representado por una esfera para cada persona que se una.</span><span class="sxs-lookup"><span data-stu-id="87569-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="87569-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87569-108">Objectives</span></span>

* <span data-ttu-id="87569-109">Configurar PUN en la aplicación</span><span class="sxs-lookup"><span data-stu-id="87569-109">Configure PUN within your application</span></span>
* <span data-ttu-id="87569-110">Configurar los jugadores</span><span class="sxs-lookup"><span data-stu-id="87569-110">Configure players</span></span>
* <span data-ttu-id="87569-111">Aprender a conectar varios usuarios en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="87569-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="87569-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="87569-112">Instructions</span></span>

1. <span data-ttu-id="87569-113">En la carpeta Assets->Resources->Prefabs (Recursos -> Recursos-> Objetos prefabricados) del panel Proyecto, arrastra y coloca el objeto prefabricado NetworkLobby en la jerarquía, tal y como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="87569-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="87569-115">Al expandir NetworkLobby, verás un objeto secundario denominado NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="87569-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="87569-116">Con el objeto NetworkRoom seleccionado, ve al panel Inspector y haz clic en Add Component (Agregar componente).</span><span class="sxs-lookup"><span data-stu-id="87569-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="87569-117">Busca PhotonView y agrega el componente.</span><span class="sxs-lookup"><span data-stu-id="87569-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="87569-119">Crea un nuevo objeto de juego vacío en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="87569-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="87569-120">Haz clic con el botón derecho en la jerarquía y selecciona Vacío en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="87569-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="87569-121">Asegúrate de que la posición está establecida en x = 0, y = 0, z = 0 y asigna al objeto el nombre PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="87569-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="87569-123">Haz clic en Agregar componente y escribe Generic Net Sync (Sincronización de red genérica). Selecciona la clase Generic Net Sync (Sincronización de red genérica).</span><span class="sxs-lookup"><span data-stu-id="87569-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="87569-124">Cuando aparezca la clase, haz clic en la casilla Usuario para activarla.</span><span class="sxs-lookup"><span data-stu-id="87569-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="87569-126">Haz clic de nuevo en Add Component (Agregar componente) y escribe Photon View (Vista de Photon).</span><span class="sxs-lookup"><span data-stu-id="87569-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="87569-127">Selecciona la clase Photon View (Vista de Photon) que aparece en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="87569-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="87569-129">Haz clic en el icono Archivo de la clase Generic Net Sync (Sincronización de red genérica).</span><span class="sxs-lookup"><span data-stu-id="87569-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="87569-130">Arrástralo y colócalo en el campo Observed Components (Componentes observados) de Photon View (Vista Photon).</span><span class="sxs-lookup"><span data-stu-id="87569-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="87569-132">A continuación, creamos esferas para representar a cada persona que se une a una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="87569-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="87569-133">Haz clic con el botón secundario en el objeto PhotonUser que acabas de crear, desplázate hacia abajo hasta 3D Object (Objeto 3D) y haz clic en Sphere (Esfera).</span><span class="sxs-lookup"><span data-stu-id="87569-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="87569-134">Se creará un objeto de juego de esfera como elemento secundario del objeto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="87569-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="87569-136">Reduce verticalmente la esfera a x = 0,06, y = 0,06 y z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="87569-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="87569-138">Arrastra el objeto de juego PhotonUser a la carpeta Prefabs del panel Project (Proyecto) y, a continuación, elimínalo de la escena.</span><span class="sxs-lookup"><span data-stu-id="87569-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="87569-139">Ya has creado un objeto prefabricado que se puede usar al generar nuevos jugadores o crear instancias a partir de estos en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="87569-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="87569-141">Comprueba que el objeto de juego se haya copiado correctamente en la carpeta Prefabs antes de eliminarlo de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="87569-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="87569-142">Crea un objeto nuevo en la jerarquía siguiendo las instrucciones del paso 3 y asígnale el nombre SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="87569-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="87569-143">A continuación, haz clic en Add Component (Agregar componente) y busca un administrador de red genérico.</span><span class="sxs-lookup"><span data-stu-id="87569-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="87569-144">Vuelve a hacer clic en el componente Generic Network Manager (Administrador de red genérico).</span><span class="sxs-lookup"><span data-stu-id="87569-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="87569-145">Cambia la posición del objeto a x = 0, y = 0 y z = 0.</span><span class="sxs-lookup"><span data-stu-id="87569-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="87569-147">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="87569-147">Congratulations</span></span>

<span data-ttu-id="87569-148">Una vez completados todos los pasos anteriores y finalizado el proceso de compilación, presiona el botón Play (Jugar) y conecta el dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87569-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="87569-149">Deberías ver una esfera a tu alrededor a medida que mueves la cabeza.</span><span class="sxs-lookup"><span data-stu-id="87569-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="87569-150">Se mostrará para cualquier usuario que se una a tu proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="87569-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="87569-151">[Siguiente lección: 4. Uso compartido de movimientos de objetos con varios usuarios](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="87569-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
