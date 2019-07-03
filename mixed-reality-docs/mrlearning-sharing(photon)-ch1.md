---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523292"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="b7966-104">Configurar redes de Unity Photon</span><span class="sxs-lookup"><span data-stu-id="b7966-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="b7966-105">En este tutorial, se obtenga información sobre cómo prepararse para la creación de una experiencia compartida importando Photon Unity a redes (juego de palabras) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="b7966-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="b7966-106">Photon es una de varias opciones de red disponibles para los desarrolladores de realidad mixta para crear experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="b7966-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="b7966-107">Se obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="b7966-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="b7966-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="b7966-108">Objectives:</span></span>

* <span data-ttu-id="b7966-109">Obtenga información sobre cómo crear una cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="b7966-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="b7966-110">Obtenga información sobre cómo buscar e importar Unity Photon a redes</span><span class="sxs-lookup"><span data-stu-id="b7966-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="b7966-111">Configurar un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="b7966-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="b7966-112">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="b7966-112">Setting up Photon</span></span>

1. <span data-ttu-id="b7966-113">Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta.</span><span class="sxs-lookup"><span data-stu-id="b7966-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="b7966-114">Vaya a la página de registro Photon haciendo clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="b7966-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="b7966-115">Siga las instrucciones de la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="b7966-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="b7966-118">Crear un identificador de aplicación, haga clic en crear un botón de nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="b7966-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="b7966-120">Seleccione el juego de palabras Photon en el menú desplegable bajo tipo Photon.</span><span class="sxs-lookup"><span data-stu-id="b7966-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="b7966-121">A continuación, asígnele un nombre.</span><span class="sxs-lookup"><span data-stu-id="b7966-121">Then give it a name.</span></span> <span data-ttu-id="b7966-122">En este ejemplo, se lo denominó HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="b7966-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="b7966-123">Una vez finalizado, haga clic en el botón Crear.</span><span class="sxs-lookup"><span data-stu-id="b7966-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="b7966-125">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="b7966-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="b7966-126">Haga clic en el identificador de aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="b7966-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="b7966-127">Pegar es en algún lugar que puede acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="b7966-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="b7966-129">Cree un nuevo proyecto de unity y asígnele el nombre HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="b7966-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="b7966-130">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="b7966-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="b7966-131">Cuando se cargue el proyecto, haga clic en la pestaña activos Store, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="b7966-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="b7966-132">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en el juego de palabras y seleccione el 2 de juego de palabras Photon - FRE"recurso de los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="b7966-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="b7966-134">Descargue e importe este activo al presionar los botones de la descarga e importación.</span><span class="sxs-lookup"><span data-stu-id="b7966-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="b7966-136">Cuando Photon se haya completado el proceso de importación, aparece el Asistente de juego de palabras.</span><span class="sxs-lookup"><span data-stu-id="b7966-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="b7966-137">Tome el identificador de aplicación (que debe estar en el Portapapeles) del paso 4 y péguelo en el cuadro de AppID y presione el botón del proyecto de instalación.</span><span class="sxs-lookup"><span data-stu-id="b7966-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="b7966-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="b7966-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="b7966-139">Después de agregar correctamente el AppID, vaya a Photon -> PhotonUnityNetworking -> recursos -> PhotonServerSettings en activos.</span><span class="sxs-lookup"><span data-stu-id="b7966-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="b7966-140">Seleccione la opción de servidor de nombres de uso y establezca la zona fija para nosotros o yourPphoton servicio de región.</span><span class="sxs-lookup"><span data-stu-id="b7966-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="b7966-142">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="b7966-142">Congratulations</span></span>

<span data-ttu-id="b7966-143">Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity.</span><span class="sxs-lookup"><span data-stu-id="b7966-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="b7966-144">El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="b7966-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="b7966-145">[Tutorial siguiente: Cómo prepararse para el desarrollo de Unity](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="b7966-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

