---
title: 'Tutoriales de funcionalidades para varios usuarios: 1. Configuración de redes Photon Unity'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553823"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="db03d-105">1. configuración de redes Photon Unity</span><span class="sxs-lookup"><span data-stu-id="db03d-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="db03d-106">Información general</span><span class="sxs-lookup"><span data-stu-id="db03d-106">Overview</span></span>

<span data-ttu-id="db03d-107">En este tutorial, obtendrá información sobre cómo prepararse para crear una experiencia compartida mediante la importación de Photon Unity Networking (BURDO) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="db03d-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="db03d-108">Photon es una de las diversas opciones de red disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="db03d-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="db03d-109">Obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="db03d-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="db03d-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db03d-110">Objectives</span></span>

* <span data-ttu-id="db03d-111">Obtenga información sobre cómo crear una cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="db03d-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="db03d-112">Obtenga información sobre cómo buscar e importar Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="db03d-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="db03d-113">Configuración de un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="db03d-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db03d-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="db03d-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="db03d-115">Si aún no ha completado los [tutoriales de introducción](mrlearning-base.md) y la serie de tutoriales de los [delimitadores espaciales de Azure](mrlearning-asa-ch1.md) , se recomienda que complete los tutoriales en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="db03d-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="db03d-116">Un equipo Windows 10 configurado con las [herramientas instaladas](install-the-tools.md) correctas</span><span class="sxs-lookup"><span data-stu-id="db03d-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="db03d-117">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="db03d-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="db03d-118">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="db03d-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="db03d-119">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="db03d-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="db03d-120">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="db03d-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="db03d-121">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="db03d-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="db03d-122">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="db03d-122">Setting up Photon</span></span>

1. <span data-ttu-id="db03d-123">Configure una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="db03d-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="db03d-124">Para ir a la página de registro de Photon, haga clic en [este vínculo](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="db03d-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="db03d-125">Siga las instrucciones que aparecen en la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="db03d-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="db03d-128">Cree un identificador de aplicación haciendo clic en el botón crear una nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="db03d-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="db03d-130">Seleccione Photon BURDO en el menú desplegable en Photon tipo.</span><span class="sxs-lookup"><span data-stu-id="db03d-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="db03d-131">A continuación, asígnele un nombre.</span><span class="sxs-lookup"><span data-stu-id="db03d-131">Then give it a name.</span></span> <span data-ttu-id="db03d-132">En este ejemplo, se denomina HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="db03d-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="db03d-133">Una vez finalizado, haga clic en el botón crear.</span><span class="sxs-lookup"><span data-stu-id="db03d-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="db03d-135">Vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="db03d-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="db03d-136">Haga clic en el identificador de la aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="db03d-136">Click the application ID and copy it.</span></span> <span data-ttu-id="db03d-137">Péguelo en un lugar en el que pueda acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="db03d-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="db03d-139">Cree un nuevo proyecto de Unity y asígnele el nombre HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="db03d-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="db03d-140">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [la sección "creación de un proyecto de Unity" del módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="db03d-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="db03d-141">Una vez que se cargue el proyecto, haga clic en la pestaña almacén de activos, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="db03d-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="db03d-142">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba BURDO y seleccione el recurso Photon BURDO 2-FREE "en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="db03d-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="db03d-144">Descargue e importe este recurso presionando los botones descargar e importar.</span><span class="sxs-lookup"><span data-stu-id="db03d-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="db03d-146">Una vez que Photon haya completado el proceso de importación, aparecerá el Asistente para burdo.</span><span class="sxs-lookup"><span data-stu-id="db03d-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="db03d-147">Tome el identificador de la aplicación (que debe estar en el portapapeles) del paso 4, péguelo en el cuadro AppID y presione el botón instalar proyecto.</span><span class="sxs-lookup"><span data-stu-id="db03d-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="db03d-149">Después de agregar correctamente el AppID, vaya a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="db03d-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="db03d-150">Seleccione la opción usar servidor de nombres y establezca la región fija en US o en su región de servicio de Photon.</span><span class="sxs-lookup"><span data-stu-id="db03d-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="db03d-152">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="db03d-152">Congratulations</span></span>

<span data-ttu-id="db03d-153">Ha creado correctamente una cuenta de Photon, ha configurado un servidor de Photon local y ha importado BURDO en Unity.</span><span class="sxs-lookup"><span data-stu-id="db03d-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="db03d-154">El siguiente paso consiste en configurar el proyecto y permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.</span><span class="sxs-lookup"><span data-stu-id="db03d-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="db03d-155">[Siguiente tutorial: 2. obtener Unity listo para el desarrollo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="db03d-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
