---
title: 'Tutoriales de la nube de Azure: 4. Integración de Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 468ba0d8e9fca85dc266b662f402f5c956dc94bb
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376447"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="139d3-105">4. Integración de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="139d3-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="139d3-106">En este tutorial, aprenderá a usar **Azure Spatial Anchors**.</span><span class="sxs-lookup"><span data-stu-id="139d3-106">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="139d3-107">Almacenará la ubicación de un **objeto del que realiza un seguimiento** como un anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="139d3-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="139d3-108">A continuación, realizará una consulta al usuario y le mostrará una flecha que apuntará a la ubicación.</span><span class="sxs-lookup"><span data-stu-id="139d3-108">Then you will query and present the user with a guiding arrow pointing to the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="139d3-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="139d3-109">Objectives</span></span>

* <span data-ttu-id="139d3-110">Conocer los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="139d3-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="139d3-111">Aprender a configurar la escena para usar Azure Spatial Anchors en este proyecto.</span><span class="sxs-lookup"><span data-stu-id="139d3-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="139d3-112">Aprender a integrar el almacenamiento y la consulta de ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="139d3-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="139d3-113">Descripción de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="139d3-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="139d3-114">**Azure Spatial Anchors** forma parte de la familia de servicios en la nube de Azure y se usa para guardar las ubicaciones de anclaje.</span><span class="sxs-lookup"><span data-stu-id="139d3-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="139d3-115">Las ubicaciones de anclaje guardadas se pueden recuperar en función del *identificador de anclaje* de la nube.</span><span class="sxs-lookup"><span data-stu-id="139d3-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="139d3-116">Para compartir y acceder a dicha ubicación de anclaje, se pueden usar dispositivos multiplataforma, como HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="139d3-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="139d3-117">Obtenga más información sobre [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="139d3-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="139d3-118">Preparación de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="139d3-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="139d3-119">Antes de empezar, tiene que crear un recurso de anclaje espacial en Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="139d3-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="139d3-120">Obtenga información sobre cómo crear un [recurso de anclaje espacial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="139d3-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="139d3-121">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="139d3-121">Preparing the scene</span></span>

<span data-ttu-id="139d3-122">En esta sección, aprenderá a configurar la escena y realizar los cambios necesarios.</span><span class="sxs-lookup"><span data-stu-id="139d3-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="139d3-123">En la ventana Proyecto, navegue a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager** (Recursos > MRTK.Tutorials.AzureCloudServices > Objetos prefabricados > Administrador).</span><span class="sxs-lookup"><span data-stu-id="139d3-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="139d3-125">En la carpeta **Manager** (Administrador), arrastre y coloque el objeto prefabricado **Anchor Manager** (Administrador de anclajes) en la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="139d3-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="139d3-126">Seleccione el objeto Game (Juego) de **Anchor Manager** (Administrador de anclajes) en la jerarquía y, en la sección Inspector, encontrará la opción **Spatial Anchor Manager** (Script) (Administrador de anclajes espacial [script]).</span><span class="sxs-lookup"><span data-stu-id="139d3-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="139d3-127">Busque el campo del identificador de la cuenta y la clave y agregue las credenciales que creó en el requisito previo de la fase anterior.</span><span class="sxs-lookup"><span data-stu-id="139d3-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="139d3-129">Ahora, busque el objeto **Scene Controller** (Controlador de escenas) en la jerarquía de escenas y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="139d3-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="139d3-130">Verá **Scene Controller** (Controlador de escenas) en la sección de Inspector.</span><span class="sxs-lookup"><span data-stu-id="139d3-130">You will see the **Scene Controller** Inspector.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="139d3-132">Observará que el campo **Anchor Manager** (Administrador de anclajes) del componente **Scene Controller** (Controlador de escenas) está vacío. Arrastre y coloque el elemento **Anchor Manager** (Administrador de anclajes) de la jerarquía de escenas en ese campo y guarde la escena.</span><span class="sxs-lookup"><span data-stu-id="139d3-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="139d3-133">Compilación e implementación de la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="139d3-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="139d3-134">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="139d3-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="139d3-135">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="139d3-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="139d3-136">Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="139d3-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="139d3-137">Creación de un anclaje para almacenar una ubicación</span><span class="sxs-lookup"><span data-stu-id="139d3-137">Create an anchor to store a location</span></span>

<span data-ttu-id="139d3-138">En esta sección, verá cómo guardar la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="139d3-139">Ejecute la aplicación y haga clic en **Set Object** (Establecer objeto) en el menú principal de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="139d3-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="139d3-140">Asigne el **nombre** del objeto que quiera guardar y haga clic en **Set Object** (Establecer objeto) para continuar.</span><span class="sxs-lookup"><span data-stu-id="139d3-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="139d3-141">Para agregar más información sobre el objeto, seleccione la **imagen**y describa el objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-141">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="139d3-142">Para guardar la ubicación, haga clic en **Sabe Location** (Guardar ubicación).</span><span class="sxs-lookup"><span data-stu-id="139d3-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="139d3-143">Verá un **puntero de anclaje** que puede desplazar y colocar en la ubicación que quiera guardar.</span><span class="sxs-lookup"><span data-stu-id="139d3-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="139d3-144">Después, se le mostrará una ventana emergente de confirmación.</span><span class="sxs-lookup"><span data-stu-id="139d3-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="139d3-145">Si quiere confirmar y guardar la ubicación, haga clic en **Sí**. De lo contrario, puede cambiar la ubicación haciendo clic en **No** y seleccionándola de nuevo.</span><span class="sxs-lookup"><span data-stu-id="139d3-145">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="139d3-146">Una vez haya hecho clic en **Sí** para confirmar la ubicación, dicha ubicación y el identificador de anclaje se guardarán en el almacenamiento en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="139d3-146">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="139d3-147">Una vez guardados, verá la **etiqueta del objeto** en el anclaje con el nombre del objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="139d3-148">Ahora la ubicación del objeto se ha guardado correctamente.</span><span class="sxs-lookup"><span data-stu-id="139d3-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="139d3-149">Consulta para buscar una ubicación de anclaje</span><span class="sxs-lookup"><span data-stu-id="139d3-149">Query for finding an anchor location</span></span>

<span data-ttu-id="139d3-150">Una vez que haya guardado correctamente la ubicación del anclaje, podrá buscar su ubicación. Para ello, seleccione **Search Object** (Buscar objeto) en el menú principal.</span><span class="sxs-lookup"><span data-stu-id="139d3-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="139d3-151">Después de hacer clic en **Search Object** (Buscar objeto), aparecerá una nueva ventana en la que deberá proporcionar el nombre del objeto que quiere buscar.</span><span class="sxs-lookup"><span data-stu-id="139d3-151">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="139d3-152">Escríbalo y haga clic en **Search Object** (Buscar objeto).</span><span class="sxs-lookup"><span data-stu-id="139d3-152">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="139d3-153">Si el objeto se guarda previamente y se encuentra en la base de datos, obtendrá la tarjeta del objeto con todos los detalles de este que haya guardado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="139d3-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="139d3-154">Ahora puede hacer clic en **Show Location** (Mostrar ubicación) para buscar el objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="139d3-155">Una vez que haga clic en **Show Location** (Mostrar ubicación) , el sistema consultará la dirección del objeto en el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="139d3-155">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="139d3-156">Después de recuperar correctamente la ubicación, una **flecha** le dirigirá hacia la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="139d3-157">Siga la marca de la flecha hasta que encuentre la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="139d3-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="139d3-158">Una vez que lo encuentre, su nombre aparecerá en la parte superior y la marca de la flecha desaparecerá. A continuación, podrá hacer clic en la **etiqueta del objeto** para ver sus detalles.</span><span class="sxs-lookup"><span data-stu-id="139d3-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="139d3-159">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="139d3-159">Congratulations</span></span>

<span data-ttu-id="139d3-160">En este tutorial, ha aprendido a guardar y recuperar la ubicación del objeto con Azure Spatial Anchors en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="139d3-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="139d3-161">En el tutorial final, aprenderá a usar **Azure Bot Service** para agregar lenguaje natural como un nuevo método de interacción para nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="139d3-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

[<span data-ttu-id="139d3-162">Tutorial siguiente: 5. Integración de Azure Bot Service con LUIS</span><span class="sxs-lookup"><span data-stu-id="139d3-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
