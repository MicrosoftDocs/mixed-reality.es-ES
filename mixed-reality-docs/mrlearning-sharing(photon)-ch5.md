---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031688"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="8be8e-105">5. Integración de Azure Spatial Anchors en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="8be8e-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="8be8e-106">En esta lección, aprenderás a integrar Azure Spatial Anchors (ASA) en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="8be8e-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="8be8e-107">ASA permite que varios dispositivos colocados tengan una referencia común si su entorno físico va a delimitar experiencias virtuales de forma que todos los participantes vean objetos en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="8be8e-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="8be8e-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8be8e-108">Objectives</span></span>

* <span data-ttu-id="8be8e-109">Integrar ASA en una experiencia compartida para la alineación de varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="8be8e-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="8be8e-110">Aprender los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.</span><span class="sxs-lookup"><span data-stu-id="8be8e-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="8be8e-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8be8e-111">Instructions</span></span>

1. <span data-ttu-id="8be8e-112">Selecciona el objeto prefabricado TableAnchor, bajo el objeto principal MixedRealityPlayspace, y elimínalo.</span><span class="sxs-lookup"><span data-stu-id="8be8e-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="8be8e-114">En la vista Project (Proyecto), ve a Assets -> Resources -> Prefabs (Recursos -> Recursos -> Objetos prefabricados) y arrastra el objeto prefabricado TableAnchor sobre el objeto SharedPlayground para convertirlo en un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="8be8e-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="8be8e-115">Expande el objeto principal MixedRealityPlayspace, el objeto TableAnchor y también el objeto Buttons (Botones).</span><span class="sxs-lookup"><span data-stu-id="8be8e-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="8be8e-117">Ahora, en la jerarquía, selecciona ShareAzureAnchorButton y desplaza tu atención al panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="8be8e-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="8be8e-118">Desplázate hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, selecciona AnchorModuleScript y haz clic en ShareAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="8be8e-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="8be8e-120">Selecciona GetAzureAnchorButton (consulta el paso 4) y vuelve a desplazar tu atención al panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="8be8e-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="8be8e-121">Desplázate hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, selecciona AnchorModuleScript, haz clic en GetSharedAnchorNetwork() y guarda los cambios.</span><span class="sxs-lookup"><span data-stu-id="8be8e-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="8be8e-123">Repite el paso 4 para enlazar la función StartAzureSession() a StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="8be8e-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="8be8e-124">Repite el paso 4 para enlazar la función CreateAzureAnchor() a CreateAzureAnchorButton y comprueba que el objeto TableAnchor está asignado al campo "Game Object" (Objeto de juego) del parámetro de la función.</span><span class="sxs-lookup"><span data-stu-id="8be8e-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="8be8e-125">Sigue las instrucciones de [Conexión de la escena al recurso de Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para agregar las credenciales de servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="8be8e-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="8be8e-126">Para probar el módulo de uso compartido, haz clic en el botón "Start Azure ASA Session" (Iniciar sesión de Azure ASA), lo que iniciará la sesión de Azure Spatial Anchors y creará un anclaje de Azure al hacer clic en el botón "Create Azure Anchor" (Crear anclaje de Azure).</span><span class="sxs-lookup"><span data-stu-id="8be8e-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="8be8e-127">Espera a que se cree el anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="8be8e-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="8be8e-128">Una vez creado el anclaje de Azure, haz clic en el botón "Share Azure Anchor" (Compartir anclaje de Azure) para compartir el anclaje de Azure creado desde HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8be8e-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="8be8e-129">Para recibir el anclaje compartido de Azure compartido en otra instancia de HoloLens, haz clic en "Start Azure ASA Session" (Iniciar sesión de Azure ASA) para empezar a trabajar en la sesión de ASA actual.</span><span class="sxs-lookup"><span data-stu-id="8be8e-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="8be8e-130">Haz clic en el botón "Get Azure Anchor" (Obtener anclaje de Azure)" para obtener el anclaje de Azure desde la otra instancia de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8be8e-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8be8e-131">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8be8e-131">Congratulations</span></span>

<span data-ttu-id="8be8e-132">En esta lección, has aprendido a integrar los nuevos anclajes espaciales de Azure para alinear dispositivos colocados en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="8be8e-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="8be8e-133">Esto también concluye el módulo de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="8be8e-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="8be8e-134">Hemos aprendido a configurar una nueva cuenta de Photon, a integrar Photon y PUN en una nueva aplicación de Unity, a configurar avatares y objetos compartidos y, por último, a alinear varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="8be8e-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
