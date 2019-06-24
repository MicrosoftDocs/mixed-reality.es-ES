---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327640"
---
# <a name="setting-up-photon"></a><span data-ttu-id="6648f-104">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="6648f-104">Setting Up Photon</span></span>

<span data-ttu-id="6648f-105">En esta lección, aprenderemos cómo prepararse para la creación de una experiencia compartida importando Photon Unity a redes (juego de palabras) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="6648f-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="6648f-106">Photon es una de varias opciones de red disponibles para los desarrolladores de realidad mixta para crear experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="6648f-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="6648f-107">Se obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="6648f-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="6648f-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="6648f-108">Objectives:</span></span>

* <span data-ttu-id="6648f-109">Aprenda a crear la cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="6648f-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="6648f-110">Obtenga información sobre cómo buscar e importar Unity Photon a redes</span><span class="sxs-lookup"><span data-stu-id="6648f-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="6648f-111">Configurar un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="6648f-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="6648f-112">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="6648f-112">Setting Up Photon</span></span>

1. <span data-ttu-id="6648f-113">Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta.</span><span class="sxs-lookup"><span data-stu-id="6648f-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="6648f-114">Vaya a la página de registro Photon haciendo clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="6648f-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="6648f-115">Siga las instrucciones de la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="6648f-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="6648f-117">Una vez que se registre, haga clic en el SDK.</span><span class="sxs-lookup"><span data-stu-id="6648f-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="6648f-118">Una vez que esté en esa página, haga clic en "servidor" y asegurarse de que dice, "alojado en sí mismo."</span><span class="sxs-lookup"><span data-stu-id="6648f-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="6648f-119">A continuación, desplácese hacia abajo y haga clic en "servidor" tal como se muestra en la segunda imagen abajo.</span><span class="sxs-lookup"><span data-stu-id="6648f-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="6648f-122">Esto hará que aparezca con la etiqueta, un cuadro de texto "me lees."</span><span class="sxs-lookup"><span data-stu-id="6648f-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="6648f-123">Continúe y leerlo.</span><span class="sxs-lookup"><span data-stu-id="6648f-123">Go ahead and read it.</span></span> <span data-ttu-id="6648f-124">Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarla.</span><span class="sxs-lookup"><span data-stu-id="6648f-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="6648f-126">Haga doble clic en la carpeta una vez que termine la descarga.</span><span class="sxs-lookup"><span data-stu-id="6648f-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="6648f-127">Una vez que el Explorador de archivos abre revelar la carpeta del SDK, copie la carpeta del SDK.</span><span class="sxs-lookup"><span data-stu-id="6648f-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="6648f-128">El siguiente paso sería entrar en la unidad C: de windows y crear una nueva carpeta denominada "server".</span><span class="sxs-lookup"><span data-stu-id="6648f-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="6648f-130">Ahora abra la carpeta y pegue la carpeta del SDK que copió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6648f-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="6648f-132">Una vez que se ha completado, abra la carpeta del SDK y vaya a "implementar", a continuación, "bin_Win64", a continuación, haga doble clic en "control photon".</span><span class="sxs-lookup"><span data-stu-id="6648f-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="6648f-134">Nota: Si tiene alguna pregunta sobre la dirección IP o alguna otra pregunta similar, puede encontrar la mayor parte de su información en la barra de herramientas (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="6648f-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="6648f-136">Ahora que el servidor está configurado y se inicia, vuelva al sitio Web de Photon y asegúrese de que se inició todavía (o iniciarla, si no). Haga clic en el icono del perfil (aplicar la conversión boxing en la esquina superior derecha de la imagen siguiente) y seleccione "las aplicaciones".</span><span class="sxs-lookup"><span data-stu-id="6648f-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="6648f-138">Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".</span><span class="sxs-lookup"><span data-stu-id="6648f-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="6648f-140">Seleccione "Juego de palabras Photon" en el menú desplegable bajo "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="6648f-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="6648f-141">A continuación, asígnele un nombre, en este ejemplo, se lo denominó "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="6648f-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="6648f-142">Una vez finalizado, haga clic en el botón "Crear".</span><span class="sxs-lookup"><span data-stu-id="6648f-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="6648f-144">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="6648f-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="6648f-145">Haga clic en el identificador de aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="6648f-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="6648f-146">Pegar es en algún lugar que puede acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="6648f-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="6648f-148">Cree un nuevo proyecto de unity y asígnele el nombre "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="6648f-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="6648f-149">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="6648f-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="6648f-150">Cuando se cargue el proyecto, haga clic en la pestaña "almacén de activos", tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="6648f-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="6648f-151">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Photon 2 del juego de palabras gratuita" desde los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="6648f-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="6648f-153">Descargue e importe este activo al presionar los botones "Descargar" y "Import".</span><span class="sxs-lookup"><span data-stu-id="6648f-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6648f-155">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="6648f-155">Congratulations</span></span>

<span data-ttu-id="6648f-156">Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity.</span><span class="sxs-lookup"><span data-stu-id="6648f-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="6648f-157">El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="6648f-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="6648f-158">[Siguiente lección: Sharing(Photon) lección 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="6648f-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

