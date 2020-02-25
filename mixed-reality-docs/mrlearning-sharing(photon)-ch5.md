---
title: 'Tutoriales de funcionalidades para varios usuarios: 5. Integración de los anclajes espaciales de Azure en una experiencia compartida'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553813"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="750cf-105">5. integrar los anclajes espaciales de Azure en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="750cf-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="750cf-106">En esta lección, aprenderá a integrar anclajes espaciales de Azure (ASA) en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="750cf-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="750cf-107">ASA permite que varios dispositivos colocalizados tengan una referencia común si su entorno físico va a delimitar experiencias virtuales de forma que todos los participantes vean objetos en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="750cf-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="750cf-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="750cf-108">Objectives</span></span>

* <span data-ttu-id="750cf-109">Integre ASA en una experiencia compartida para la alineación de varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="750cf-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="750cf-110">Conozca los aspectos básicos de cómo funciona ASA en el contexto de una experiencia compartida local.</span><span class="sxs-lookup"><span data-stu-id="750cf-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="750cf-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="750cf-111">Instructions</span></span>

1. <span data-ttu-id="750cf-112">Seleccione TableAnchor recurso prefabricado bajo el objeto primario MixedRealityPlayspace y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="750cf-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="750cf-114">En la vista de proyecto, vaya a activos-> Resources-> Prefabs y arrastre el recurso prefabricado TableAnchor sobre el objeto SharedPlayground para convertirlo en un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="750cf-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="750cf-115">Expanda el objeto primario MixedRealityPlayspace, el objeto TableAnchor y expanda también el objeto botones.</span><span class="sxs-lookup"><span data-stu-id="750cf-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="750cf-117">Ahora, en la jerarquía, seleccione ShareAzureAnchorButton y desplace su atención al panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="750cf-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="750cf-118">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, seleccione AnchorModuleScript y haga clic en ShareAnchorNetwork ().</span><span class="sxs-lookup"><span data-stu-id="750cf-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="750cf-120">Seleccione GetAzureAnchorButton (consulte el paso 4) y vuelva a llamar al panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="750cf-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="750cf-121">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, seleccione AnchorModuleScript, haga clic en GetSharedAnchorNetwork () y en guardar.</span><span class="sxs-lookup"><span data-stu-id="750cf-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="750cf-123">Repita el paso 4 para enlazar la función StartAzureSession () a StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="750cf-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="750cf-124">Repita el paso 4 para enlazar la función CreateAzureAnchor () a CreateAzureAnchorButton y comprobar que el objeto TableAnchor está asignado al campo ' Game Object ' del parámetro de la función.</span><span class="sxs-lookup"><span data-stu-id="750cf-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="750cf-125">Siga las instrucciones de [conexión de la escena a recursos de Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para agregar sus credenciales del servicio de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="750cf-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="750cf-126">Para probar el módulo de uso compartido, haga clic en el botón "iniciar sesión de Azure ASA", que iniciará la sesión de anclajes espaciales de Azure y luego cree el anclaje de Azure haciendo clic en el botón "crear anclaje de Azure".</span><span class="sxs-lookup"><span data-stu-id="750cf-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="750cf-127">Espere a que se cree el delimitador de Azure.</span><span class="sxs-lookup"><span data-stu-id="750cf-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="750cf-128">Una vez creado el delimitador de Azure, haga clic en el botón "compartir el anclaje de Azure" para compartir el anclaje de Azure creado desde HoloLens.</span><span class="sxs-lookup"><span data-stu-id="750cf-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="750cf-129">Para recibir el delimitador de Azure compartido en otro HoloLens, haga clic en "iniciar sesión de Azure ASA" para empezar a trabajar en la sesión de ASA actual.</span><span class="sxs-lookup"><span data-stu-id="750cf-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="750cf-130">Haga clic en el botón "obtener anclaje de Azure" para obtener el anclaje compartido de Azure desde el otro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="750cf-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="750cf-131">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="750cf-131">Congratulations</span></span>

<span data-ttu-id="750cf-132">En esta lección, ha aprendido a integrar los nuevos delimitadores espaciales de Azure para alinear dispositivos colocalizados en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="750cf-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="750cf-133">Esto también concluye el módulo de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="750cf-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="750cf-134">Hemos aprendido a configurar una nueva cuenta de Photon, a integrar Photon y BURDO en una nueva aplicación de Unity, a configurar avatares y a objetos compartidos y, por último, a alinear varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="750cf-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
