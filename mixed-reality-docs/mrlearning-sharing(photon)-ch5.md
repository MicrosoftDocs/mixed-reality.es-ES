---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465200"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="24b1c-104">Azure delimitadores espacial y experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="24b1c-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="24b1c-105">En esta lección, se obtenga información sobre cómo integrar Azure espacial delimitadores (ASA) en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="24b1c-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="24b1c-106">ASA permite varios dispositivos colocados para tener una referencia común si su entorno físico es experiencias virtual delimitador forma que todos los participantes ven objetos en el mismo lugar físico.</span><span class="sxs-lookup"><span data-stu-id="24b1c-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="24b1c-107">Antes de continuar con esta lección, necesitaremos completar el módulo de aprendizaje de ASA que cubrirá sus aspectos básicos, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales que son necesarios antes de que podemos integrar ASA en nuestra experiencia compartido ASA.</span><span class="sxs-lookup"><span data-stu-id="24b1c-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="24b1c-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="24b1c-108">Objectives:</span></span>

- <span data-ttu-id="24b1c-109">Integrar ASA en una experiencia compartida para la alineación de varios dispositivo</span><span class="sxs-lookup"><span data-stu-id="24b1c-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="24b1c-110">Conozca los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia local compartido</span><span class="sxs-lookup"><span data-stu-id="24b1c-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="24b1c-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="24b1c-111">Instructions</span></span>

1. <span data-ttu-id="24b1c-112">Guarde el proyecto de la lección anterior (CTRL + S) y asígnele el nombre "HLSharedProjectMainPart5.unity" para que resulte más fácil encontrar cuando necesite de nuevo.</span><span class="sxs-lookup"><span data-stu-id="24b1c-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="24b1c-113">Seleccione el recurso prefabricado de TableAnchor debajo del objeto primario de MixedRealityPlayspace y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="24b1c-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="24b1c-115">En la vista del proyecto vaya a recursos -> recursos -> prefabricados y arrastre el prefabricado TableAnchor encima del objeto SharedPlayground convertirlo en un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="24b1c-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="24b1c-116">Expanda el objeto primario de MixedRealityPlayspace, el objeto TableAnchor y así el objeto de botones.</span><span class="sxs-lookup"><span data-stu-id="24b1c-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="24b1c-118">Ahora en la jerarquía, seleccione ShareAzureAnchorButton y mover su atención en el panel de Inaspector.</span><span class="sxs-lookup"><span data-stu-id="24b1c-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="24b1c-119">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione AnchorModuleScript y haga clic en ShareAnchorNetework().</span><span class="sxs-lookup"><span data-stu-id="24b1c-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="24b1c-121">Seleccione GetAzureAnchorButton (consulte el paso 4), y mover la atención de nuevo en el panel del Inspector.</span><span class="sxs-lookup"><span data-stu-id="24b1c-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="24b1c-122">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, AnchorModuleScript y haga clic en GetSharedAnchorNetwork() y seleccione Guardar.</span><span class="sxs-lookup"><span data-stu-id="24b1c-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="24b1c-124">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="24b1c-124">Congratulations</span></span>

<span data-ttu-id="24b1c-125">En esta lección ha aprendido a integrar eficaz nuevos espacial delimitadores de Azure para alinear dispositivos colocados en una experiencia compartido!</span><span class="sxs-lookup"><span data-stu-id="24b1c-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="24b1c-126">En esta lección también se concluye el módulo de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="24b1c-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="24b1c-127">Hemos aprendido cómo configurar una nueva cuenta Photon, integrar Photon y juego de palabras en una nueva aplicación de Unity, configurar los avatares y objetos compartidos y, por último, Alinear a varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="24b1c-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

