---
title: Módulo de uso compartido de aprendizaje MR para HoloLens 2
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e40cd50f75ca509c601d215cb865161ea3596565
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293644"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="2266f-104">Configuración de redes Photon Unity</span><span class="sxs-lookup"><span data-stu-id="2266f-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="2266f-105">En este tutorial, aprenderá a preparar la creación de una experiencia compartida mediante la importación de Photon Unity Networking (BURDO) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="2266f-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="2266f-106">Photon es una de las diversas opciones de red disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="2266f-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="2266f-107">Veremos cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="2266f-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="2266f-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2266f-108">Objectives:</span></span>

* <span data-ttu-id="2266f-109">Obtenga información sobre cómo crear una cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="2266f-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="2266f-110">Obtenga información sobre cómo buscar e importar Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="2266f-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="2266f-111">Configuración de un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="2266f-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="2266f-112">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="2266f-112">Setting up Photon</span></span>

1. <span data-ttu-id="2266f-113">Configure una cuenta de [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="2266f-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="2266f-114">Para ir a la página de registro de Photon, haga clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="2266f-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="2266f-115">Siga las instrucciones que aparecen en la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="2266f-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="2266f-118">Cree un identificador de aplicación haciendo clic en el botón crear una nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="2266f-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="2266f-120">Seleccione Photon BURDO en el menú desplegable en Photon tipo.</span><span class="sxs-lookup"><span data-stu-id="2266f-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="2266f-121">A continuación, asígnele un nombre.</span><span class="sxs-lookup"><span data-stu-id="2266f-121">Then give it a name.</span></span> <span data-ttu-id="2266f-122">En este ejemplo, se denomina HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="2266f-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="2266f-123">Una vez finalizado, haga clic en el botón crear.</span><span class="sxs-lookup"><span data-stu-id="2266f-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="2266f-125">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="2266f-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="2266f-126">Haga clic en el identificador de la aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="2266f-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="2266f-127">Péguelo en un lugar en el que pueda acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="2266f-127">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="2266f-129">Cree un nuevo proyecto de Unity y asígnele el nombre HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="2266f-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="2266f-130">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [la sección "creación de un proyecto de Unity" del módulo base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="2266f-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="2266f-131">Una vez que se cargue el proyecto, haga clic en la pestaña almacén de activos, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="2266f-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="2266f-132">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba BURDO y seleccione el recurso Photon BURDO 2-FREE "en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="2266f-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="2266f-134">Descargue e importe este recurso presionando los botones descargar e importar.</span><span class="sxs-lookup"><span data-stu-id="2266f-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="2266f-136">Una vez que Photon haya completado el proceso de importación, aparecerá el Asistente para burdo.</span><span class="sxs-lookup"><span data-stu-id="2266f-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="2266f-137">Tome el identificador de la aplicación (que debe estar en el portapapeles) del paso 4 y péguelo en el cuadro AppID y presione el botón instalar proyecto.</span><span class="sxs-lookup"><span data-stu-id="2266f-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="2266f-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2266f-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="2266f-139">Después de agregar correctamente el AppID, vaya a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="2266f-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="2266f-140">Seleccione la opción usar servidor de nombres y establezca la región fija en US o en su región de servicio de Photon.</span><span class="sxs-lookup"><span data-stu-id="2266f-140">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="2266f-142">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2266f-142">Congratulations</span></span>

<span data-ttu-id="2266f-143">Ha creado correctamente una cuenta de Photon, ha configurado un servidor de Photon local y ha importado BURDO en Unity.</span><span class="sxs-lookup"><span data-stu-id="2266f-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="2266f-144">El siguiente paso consiste en configurar el proyecto y, a continuación, permitir conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="2266f-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="2266f-145">[Siguiente tutorial: Preparación de Unity para desarrollo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="2266f-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

