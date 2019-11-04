---
title: 'Tutoriales de funcionalidades para varios usuarios: 1. Configuración de redes Photon Unity'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c6a2bea3d50669000e81cad7c83ae6a69b8a847f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437747"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="2c1a3-105">1. configuración de redes Photon Unity</span><span class="sxs-lookup"><span data-stu-id="2c1a3-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="2c1a3-106">En este tutorial, obtendrá información sobre cómo prepararse para crear una experiencia compartida mediante la importación de Photon Unity Networking (BURDO) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-106">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="2c1a3-107">Photon es una de las diversas opciones de red disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="2c1a3-108">Obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-108">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="2c1a3-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2c1a3-109">Objectives</span></span>

* <span data-ttu-id="2c1a3-110">Obtenga información sobre cómo crear una cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="2c1a3-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="2c1a3-111">Obtenga información sobre cómo buscar e importar Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="2c1a3-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="2c1a3-112">Configuración de un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="2c1a3-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="2c1a3-113">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="2c1a3-113">Setting up Photon</span></span>

1. <span data-ttu-id="2c1a3-114">Configure una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="2c1a3-114">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="2c1a3-115">Para ir a la página de registro de Photon, haga clic en [este vínculo](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="2c1a3-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="2c1a3-116">Siga las instrucciones que aparecen en la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="2c1a3-119">Cree un identificador de aplicación haciendo clic en el botón crear una nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="2c1a3-121">Seleccione Photon BURDO en el menú desplegable en Photon tipo.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="2c1a3-122">A continuación, asígnele un nombre.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-122">Then give it a name.</span></span> <span data-ttu-id="2c1a3-123">En este ejemplo, se denomina HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="2c1a3-124">Una vez finalizado, haga clic en el botón crear.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="2c1a3-126">Vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-126">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="2c1a3-127">Haga clic en el identificador de la aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-127">Click the application ID and copy it.</span></span> <span data-ttu-id="2c1a3-128">Péguelo en un lugar en el que pueda acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="2c1a3-130">Cree un nuevo proyecto de Unity y asígnele el nombre HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="2c1a3-131">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [la sección "creación de un proyecto de Unity" del módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="2c1a3-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="2c1a3-132">Una vez que se cargue el proyecto, haga clic en la pestaña almacén de activos, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-132">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="2c1a3-133">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba BURDO y seleccione el recurso Photon BURDO 2-FREE "en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="2c1a3-135">Descargue e importe este recurso presionando los botones descargar e importar.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="2c1a3-137">Una vez que Photon haya completado el proceso de importación, aparecerá el Asistente para burdo.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="2c1a3-138">Tome el identificador de la aplicación (que debe estar en el portapapeles) del paso 4, péguelo en el cuadro AppID y presione el botón instalar proyecto.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-138">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="2c1a3-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2c1a3-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="2c1a3-140">Después de agregar correctamente el AppID, vaya a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="2c1a3-141">Seleccione la opción usar servidor de nombres y establezca la región fija en US o en su región de servicio de Photon.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="2c1a3-143">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2c1a3-143">Congratulations</span></span>

<span data-ttu-id="2c1a3-144">Ha creado correctamente una cuenta de Photon, ha configurado un servidor de Photon local y ha importado BURDO en Unity.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="2c1a3-145">El siguiente paso consiste en configurar el proyecto y permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="2c1a3-145">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="2c1a3-146">[Siguiente tutorial: 2. obtener Unity listo para el desarrollo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="2c1a3-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

