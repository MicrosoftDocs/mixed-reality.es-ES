---
title: 'Tutoriales sobre las funcionalidades multiusuario: 1. Configuración de Photon Unity Networking'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031332"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="8dd5a-105">1. Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="8dd5a-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="8dd5a-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="8dd5a-106">Overview</span></span>

<span data-ttu-id="8dd5a-107">En este tutorial, aprenderás a preparar la creación de una experiencia compartida. Para hacerlo, importarás Photon Unity Networking (PUN) en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="8dd5a-108">Photon es una de las diversas opciones de redes disponibles para que los desarrolladores de Mixed Reality creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="8dd5a-109">Aprenderás a crear una cuenta de Photon, a importar Photon y a crear un servidor local opcional.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="8dd5a-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8dd5a-110">Objectives</span></span>

* <span data-ttu-id="8dd5a-111">Aprender a crear una cuenta de Photon</span><span class="sxs-lookup"><span data-stu-id="8dd5a-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="8dd5a-112">Aprender a buscar e importar Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="8dd5a-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="8dd5a-113">Configurar un servidor local de Photon</span><span class="sxs-lookup"><span data-stu-id="8dd5a-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8dd5a-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8dd5a-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="8dd5a-115">Si aún no has completado los [tutoriales de introducción](mrlearning-base.md) y los [tutoriales de introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="8dd5a-116">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8dd5a-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8dd5a-117">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="8dd5a-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8dd5a-118">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="8dd5a-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="8dd5a-119">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="8dd5a-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="8dd5a-120">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="8dd5a-121">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="8dd5a-122">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="8dd5a-122">Setting up Photon</span></span>

1. <span data-ttu-id="8dd5a-123">Configura una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="8dd5a-124">Ve a la página de registro de Photon. Para ello, haz clic en [este vínculo](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="8dd5a-125">Sigue las instrucciones de la página de registro para crear la cuenta.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="8dd5a-128">Crea un identificador de aplicación haciendo clic en el botón Create a New App (Crear una nueva aplicación).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="8dd5a-130">Selecciona Photon PUN en el menú desplegable, bajo Photon Type (Tipo de Photon).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="8dd5a-131">A continuación, asígnale un nombre.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-131">Then give it a name.</span></span> <span data-ttu-id="8dd5a-132">En este ejemplo, se denomina HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="8dd5a-133">Al finalizar, haz clic en el botón Crear.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="8dd5a-135">Vuelve a la página de aplicaciones. Deberías ver algo parecido a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="8dd5a-136">Haz clic en el id. de aplicación y cópialo.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-136">Click the application ID and copy it.</span></span> <span data-ttu-id="8dd5a-137">Ponlo en algún lugar al que puedas acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="8dd5a-139">Crea un nuevo proyecto de Unity llamado HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="8dd5a-140">Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulta [la sección "Crear proyecto de Unity" del módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="8dd5a-141">Una vez cargado el proyecto, haz clic en la pestaña Assets Store (Almacén de recursos), como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="8dd5a-142">A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escribe PUN y selecciona el recurso Photon PUN 2 - FREE (Photon PUN 2 - GRATUITO) en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="8dd5a-144">Descarga e importa este recurso presionando los botones Download (Descargar) e Import (Importar).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="8dd5a-146">Cuando Photon complete el proceso de importación, aparecerá el asistente de PUN.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="8dd5a-147">Usa el identificador de la aplicación (debe estar en el portapapeles) del paso 4, pégalo en el cuadro AppID y presiona el botón Setup Project (Configurar proyecto).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="8dd5a-149">Después de agregar correctamente AppID, desplázate a Photon -> PhotonUnityNetworking -> Resources (Recursos) -> PhotonServerSettings en Assets (Recursos).</span><span class="sxs-lookup"><span data-stu-id="8dd5a-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="8dd5a-150">Selecciona la opción de Use Name Server (Usar servidor de nombres) y establece la región fija en US (EE. UU.) o en tu región de servicio de Photon.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="8dd5a-152">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8dd5a-152">Congratulations</span></span>

<span data-ttu-id="8dd5a-153">Has creado correctamente una cuenta de Photon, has configurado un servidor de Photon local y has importado PUN a Unity.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="8dd5a-154">El siguiente paso consiste en configurar el proyecto y permitir las conexiones con otros usuarios para que varios usuarios puedan ver tu trabajo.</span><span class="sxs-lookup"><span data-stu-id="8dd5a-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="8dd5a-155">[Tutorial siguiente: 2. Preparación de Unity para desarrollo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="8dd5a-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
