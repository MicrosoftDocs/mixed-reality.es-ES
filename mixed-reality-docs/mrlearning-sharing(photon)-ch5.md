---
title: Módulo de uso compartido de aprendizaje MR para HoloLens 2
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293624"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="a19cb-104">Anclajes espaciales y experiencias compartidas de Azure</span><span class="sxs-lookup"><span data-stu-id="a19cb-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="a19cb-105">En esta lección, aprenderá a integrar anclajes espaciales de Azure (ASA) en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="a19cb-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="a19cb-106">ASA permite que varios dispositivos colocalizados tengan una referencia común si su entorno físico va a delimitar experiencias virtuales de forma que todos los participantes vean objetos en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="a19cb-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="a19cb-107">Antes de continuar con esta lección, es necesario completar el módulo de aprendizaje de ASA, que tratará los conceptos básicos de ASA, la creación de cuentas y recursos de Azure y otros bloques de edificios fundamentales necesarios antes de que podamos integrar ASA en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="a19cb-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="a19cb-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a19cb-108">Objectives:</span></span>

- <span data-ttu-id="a19cb-109">Integre ASA en una experiencia compartida para la alineación de varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a19cb-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="a19cb-110">Conozca los aspectos básicos de cómo funciona ASA en el contexto de una experiencia compartida local.</span><span class="sxs-lookup"><span data-stu-id="a19cb-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="a19cb-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="a19cb-111">Instructions</span></span>

1. <span data-ttu-id="a19cb-112">Guarde el proyecto de la lección anterior (control + S) y asígnele el nombre "HLSharedProjectMainPart5. Unity" para que sea más fácil de encontrar cuando lo necesite de nuevo.</span><span class="sxs-lookup"><span data-stu-id="a19cb-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="a19cb-113">Seleccione TableAnchor recurso prefabricado bajo el objeto primario MixedRealityPlayspace y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="a19cb-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="a19cb-115">En la vista de proyecto, vaya a activos-> Resources-> Prefabs y arrastre el recurso prefabricado TableAnchor sobre el objeto SharedPlayground para convertirlo en un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="a19cb-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="a19cb-116">Expanda el objeto primario MixedRealityPlayspace, el objeto TableAnchor y expanda también el objeto botones.</span><span class="sxs-lookup"><span data-stu-id="a19cb-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="a19cb-118">Ahora, en la jerarquía, seleccione ShareAzureAnchorButton y desplace su atención al panel inestable.</span><span class="sxs-lookup"><span data-stu-id="a19cb-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="a19cb-119">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione AnchorModuleScript y haga clic en ShareAnchorNetework ().</span><span class="sxs-lookup"><span data-stu-id="a19cb-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="a19cb-121">Seleccione GetAzureAnchorButton (consulte el paso 4) y vuelva a llamar al panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="a19cb-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="a19cb-122">Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione AnchorModuleScript, y haga clic en GetSharedAnchorNetwork () y en guardar.</span><span class="sxs-lookup"><span data-stu-id="a19cb-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="a19cb-124">Para probar el módulo de uso compartido, haga clic en el botón "iniciar sesión de Azure ASA", que iniciará la sesión de anclajes espaciales de Azure y, después, cree el anclaje de Azure haciendo clic en el botón "crear anclaje de Azure" y espere unos minutos para que se cree el delimitador de Azure.</span><span class="sxs-lookup"><span data-stu-id="a19cb-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="a19cb-125">Una vez creado el delimitador de Azure, haga clic en el botón "compartir el anclaje de Azure" para compartir el delimitador de Azure creado desde HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a19cb-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="a19cb-126">Para recibir el delimitador de Azure compartido en otro HoloLens, haga clic en "iniciar sesión de Azure ASA" para empezar a trabajar en la sesión de ASA actual y haga clic en el botón "obtener el anclaje de Azure" para obtener el anclaje compartido de Azure desde el otro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a19cb-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="a19cb-127">Nota: Todos los detalles de las acciones correspondientes en los botones individuales se mostrarán en la ventana Depurar.</span><span class="sxs-lookup"><span data-stu-id="a19cb-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a19cb-128">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a19cb-128">Congratulations</span></span>

<span data-ttu-id="a19cb-129">En esta lección ha aprendido a integrar los nuevos delimitadores espaciales de Azure para alinear dispositivos colocalizados en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="a19cb-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="a19cb-130">En esta lección también se concluye el módulo de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="a19cb-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="a19cb-131">Hemos aprendido a configurar una nueva cuenta de Photon, a integrar Photon y BURDO en una nueva aplicación de Unity, a configurar avatares y objetos compartidos, y, por último, a alinear varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="a19cb-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

