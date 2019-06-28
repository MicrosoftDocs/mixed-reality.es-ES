---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416126"
---
# <a name="setting-up-photon"></a><span data-ttu-id="11547-104">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="11547-104">Setting Up Photon</span></span>

<span data-ttu-id="11547-105">En esta lección, aprenderemos cómo prepararse para la creación de una experiencia compartida importando Photon Unity a redes (juego de palabras) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="11547-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="11547-106">Photon es una de varias opciones de red disponibles para los desarrolladores de realidad mixta para crear experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="11547-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="11547-107">Se obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="11547-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="11547-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="11547-108">Objectives:</span></span>

* <span data-ttu-id="11547-109">Aprenda a crear la cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="11547-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="11547-110">Obtenga información sobre cómo buscar e importar Unity Photon a redes</span><span class="sxs-lookup"><span data-stu-id="11547-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="11547-111">Configurar un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="11547-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="11547-112">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="11547-112">Setting Up Photon</span></span>

1. <span data-ttu-id="11547-113">Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta.</span><span class="sxs-lookup"><span data-stu-id="11547-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="11547-114">Vaya a la página de registro Photon haciendo clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="11547-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="11547-115">Siga las instrucciones de la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="11547-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="11547-118">Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".</span><span class="sxs-lookup"><span data-stu-id="11547-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="11547-120">Seleccione "Juego de palabras Photon" en el menú desplegable bajo "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="11547-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="11547-121">A continuación, asígnele un nombre, en este ejemplo, se lo denominó "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="11547-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="11547-122">Una vez finalizado, haga clic en el botón "Crear".</span><span class="sxs-lookup"><span data-stu-id="11547-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="11547-124">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="11547-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="11547-125">Haga clic en el identificador de aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="11547-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="11547-126">Pegar es en algún lugar que puede acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="11547-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="11547-128">Cree un nuevo proyecto de unity y asígnele el nombre "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="11547-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="11547-129">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="11547-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="11547-130">Cuando se cargue el proyecto, haga clic en la pestaña "almacén de activos", tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="11547-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="11547-131">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Juego de palabras 2 - Photon libre" de los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="11547-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="11547-133">Descargue e importe este activo al presionar los botones "Descargar" y "Import".</span><span class="sxs-lookup"><span data-stu-id="11547-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="11547-135">Cuando Photon se haya completado el proceso de importación, aparecerá el Asistente de juego de palabras.</span><span class="sxs-lookup"><span data-stu-id="11547-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="11547-136">Tome el identificador de aplicación (que debe estar en el Portapapeles) del paso 4 y péguelo en el cuadro de AppID y presione el botón "Setup Project".</span><span class="sxs-lookup"><span data-stu-id="11547-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="11547-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="11547-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="11547-138">Después de agregar correctamente el AppID, vaya a "Photon"->"PhotonUnityNetworking" -> "Recursos" -> "PhotonServerSettings" en los activos.</span><span class="sxs-lookup"><span data-stu-id="11547-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="11547-139">Seleccione la opción "Servidor de nombres de uso" y establezca la región fija a "nosotros" o la región del servicio photon.</span><span class="sxs-lookup"><span data-stu-id="11547-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="11547-141">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="11547-141">Congratulations</span></span>

<span data-ttu-id="11547-142">Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity.</span><span class="sxs-lookup"><span data-stu-id="11547-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="11547-143">El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="11547-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="11547-144">[Siguiente lección: Sharing(Photon) lección 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="11547-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

