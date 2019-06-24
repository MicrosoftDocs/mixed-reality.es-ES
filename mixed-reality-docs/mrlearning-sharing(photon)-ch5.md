---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326875"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="b5b03-104">Azure delimitadores espaciales y experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="b5b03-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="b5b03-105">En esta lección, se obtendrá información sobre cómo integrar Azure espacial delimitadores (ASA) en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="b5b03-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="b5b03-106">ASA permite varios dispositivos comparten ubicación para tener una comprensión común si su entorno físico para delimitar virtual experiencias de modo que todos los participantes ven objetos en el mismo lugar físico.</span><span class="sxs-lookup"><span data-stu-id="b5b03-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="b5b03-107">Antes de continuar con esta lección, necesitaremos completar el módulo de aprendizaje de ASA que cubrirá sus aspectos básicos, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales que son necesarios antes de que podemos integrar ASA en nuestra experiencia compartido ASA.</span><span class="sxs-lookup"><span data-stu-id="b5b03-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="b5b03-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="b5b03-108">Objectives:</span></span>

- <span data-ttu-id="b5b03-109">Integrar ASA en una experiencia compartida para la alineación de varios dispositivo</span><span class="sxs-lookup"><span data-stu-id="b5b03-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="b5b03-110">Conozca los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia local compartido</span><span class="sxs-lookup"><span data-stu-id="b5b03-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="b5b03-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b5b03-111">Instructions</span></span>

1. <span data-ttu-id="b5b03-112">Guarde el proyecto de la lección anterior (CTRL + S) y asígnele el nombre "HLSharedProjectMainPart5.unity" para que resulte más fácil encontrar cuando necesite de nuevo.</span><span class="sxs-lookup"><span data-stu-id="b5b03-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="b5b03-113">Seleccione el recurso prefabricado de TableAnchor debajo del objeto primario de "MixedRealityPlayspace" y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="b5b03-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="b5b03-115">Al igual que algunas de las lecciones anteriores, importar un nuevo paquete personalizado que se puede obtener [aquí.](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="b5b03-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="b5b03-117">Una vez importado, agarre el delimitador de la tabla recién actualizado (desde el paquete de unity que se importan en el paso anterior) desde la carpeta "prefabricados" en el panel de proyecto y colóquelo en el objeto primario "MixedRealityPlayspace."</span><span class="sxs-lookup"><span data-stu-id="b5b03-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="b5b03-119">Expanda el objeto primario "MixedRealityPlayspace" y, a continuación, el objeto "TableAnchor" y así el objeto de "botones".</span><span class="sxs-lookup"><span data-stu-id="b5b03-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="b5b03-121">Ahora en la jerarquía, seleccione el "ShareAzureAnchorButton" y mueva su atención en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="b5b03-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="b5b03-122">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione "AnchorModuleScript" y haga clic en "ShareAnchorNetework()".</span><span class="sxs-lookup"><span data-stu-id="b5b03-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="b5b03-124">Como paso 6, seleccione el "GetAzureAnchorButton" y desplazar la atención de nuevo en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="b5b03-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="b5b03-125">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione "AnchorModuleScript" y haga clic en "GetSharedAnchorNetwork()".</span><span class="sxs-lookup"><span data-stu-id="b5b03-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="b5b03-126">A continuación, guarde.</span><span class="sxs-lookup"><span data-stu-id="b5b03-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="b5b03-128">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="b5b03-128">Congratulations</span></span>

<span data-ttu-id="b5b03-129">En esta lección ha aprendido a integrar eficaz nuevos espacial delimitadores de Azure para alinear dispositivos colocados en una experiencia compartido!</span><span class="sxs-lookup"><span data-stu-id="b5b03-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="b5b03-130">En esta lección también se concluye el módulo de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="b5b03-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="b5b03-131">Hemos aprendido cómo configurar una nueva cuenta Photon, integrar Photon y juego de palabras en una nueva aplicación de Unity, configurar los avatares y objetos compartidos y, por último, Alinear a varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="b5b03-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

