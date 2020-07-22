---
title: 'Tutoriales de la nube de Azure: 3. Integración de Azure Custom Vision'
description: Complete este curso para aprender a implementar Azure Custom Vision con la aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens, hololens 2, azure custom vision, azure cognitive services
ms.localizationpriority: high
ms.openlocfilehash: c3ba5a715b0e77d7869d598a472341cd390c2d23
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306125"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="32cb6-105">3. Integración de Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="32cb6-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="32cb6-106">En este tutorial, aprenderá a usar **Azure Custom Vision**. Cargará un conjunto de fotos para asociarlo a un *objeto con seguimiento*, las cargará en el servicio **Custom Vision** y comenzará el proceso de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="32cb6-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="32cb6-107">A continuación, usará el servicio para detectar el *objeto con seguimiento* al capturar las fotos de la fuente de la cámara web.</span><span class="sxs-lookup"><span data-stu-id="32cb6-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="32cb6-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="32cb6-108">Objectives</span></span>

* <span data-ttu-id="32cb6-109">Aprender los aspectos básicos de Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="32cb6-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="32cb6-110">Aprender a configurar la escena para usar Custom Vision en este proyecto.</span><span class="sxs-lookup"><span data-stu-id="32cb6-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="32cb6-111">Aprender a integrar, cargar, entrenar y detectar imágenes</span><span class="sxs-lookup"><span data-stu-id="32cb6-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="32cb6-112">Descripción de Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="32cb6-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="32cb6-113">**Azure Custom Vision** forma parte de la familia **Cognitive Services** y se usa para entrenar clasificadores de imágenes.</span><span class="sxs-lookup"><span data-stu-id="32cb6-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="32cb6-114">El clasificador de imágenes es un servicio de IA que usa el modelo entrenado para aplicar etiquetas coincidentes.</span><span class="sxs-lookup"><span data-stu-id="32cb6-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="32cb6-115">Nuestra aplicación usará esta característica de clasificación para detectar *objetos con seguimiento*.</span><span class="sxs-lookup"><span data-stu-id="32cb6-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="32cb6-116">Más información sobre [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="32cb6-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="32cb6-117">Preparación de Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="32cb6-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="32cb6-118">Antes de empezar, tiene que crear un proyecto de Custom Vision, la manera más rápida es usar el portal web.</span><span class="sxs-lookup"><span data-stu-id="32cb6-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="32cb6-119">Siga este [tutorial de inicio rápido](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) para configurar la cuenta y el proyecto hasta la sección *Carga y etiquetado de imágenes*.</span><span class="sxs-lookup"><span data-stu-id="32cb6-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="32cb6-120">Para entrenar un modelo, debe tener al menos 2 etiquetas y 5 imágenes por etiqueta.</span><span class="sxs-lookup"><span data-stu-id="32cb6-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="32cb6-121">Para usar esta aplicación, debe crear al menos una etiqueta con 5 imágenes, de modo que el proceso de entrenamiento no genere errores más adelante.</span><span class="sxs-lookup"><span data-stu-id="32cb6-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="32cb6-122">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="32cb6-122">Preparing the scene</span></span>

<span data-ttu-id="32cb6-123">En la ventana Proyecto, navega hasta la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="32cb6-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="32cb6-125">Desde ahí, arrastre el recurso prefabricado **ObjectDetectionManager** hasta la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="32cb6-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="32cb6-127">En la ventana Hierarchy (Jerarquía), busque el objeto **ObjectDetectionManager** y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="32cb6-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="32cb6-128">El recurso prefabricado **ObjectDetectionManager** contiene el componente **ObjectDetectionManager (script)** y, como puede ver en la ventana Inspector, depende de varios valores.</span><span class="sxs-lookup"><span data-stu-id="32cb6-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="32cb6-129">Recuperación de credenciales de recursos de API de Azure</span><span class="sxs-lookup"><span data-stu-id="32cb6-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="32cb6-130">Las credenciales necesarias para la configuración de **ObjectDetectionManager (script)** se pueden recuperar de Azure Portal y del portal de Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="32cb6-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="32cb6-131">Azure Portal</span><span class="sxs-lookup"><span data-stu-id="32cb6-131">Azure Portal</span></span>

<span data-ttu-id="32cb6-132">Busque el recurso personalizado de Custom Vision de tipo **Cognitive Services** que ha creado en la sección *Preparación de la escena* de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="32cb6-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="32cb6-133">Haga clic en *Keys and Endpoint* (Claves y punto de conexión) para recuperar las credenciales necesarias.</span><span class="sxs-lookup"><span data-stu-id="32cb6-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="32cb6-134">Panel de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="32cb6-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="32cb6-135">En el panel de [Custom Vision](https://www.customvision.ai/projects), abra el proyecto que ha creado para este tutorial y haga clic en la esquina superior derecha de la página en el icono de engranaje para abrir la página de configuración.</span><span class="sxs-lookup"><span data-stu-id="32cb6-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="32cb6-136">Aquí, en la sección *Resources* (Recursos) de la derecha encontrará las credenciales necesarias.</span><span class="sxs-lookup"><span data-stu-id="32cb6-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="32cb6-137">Ahora con **ObjectDetectionManager (script)** configurado correctamente, busque el objeto de **SceneController** en la jerarquía de escenas y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="32cb6-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="32cb6-139">Se ve que el campo *Object Detection Manager* (Administrador de detección de objetos) en el componente **SceneController** está vacío, arrastre **ObjectDetectionManager** desde la jerarquía hasta ese campo y guarde la escena.</span><span class="sxs-lookup"><span data-stu-id="32cb6-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="32cb6-141">Toma y carga de imágenes</span><span class="sxs-lookup"><span data-stu-id="32cb6-141">Take and upload images</span></span>

<span data-ttu-id="32cb6-142">Ejecute la escena y haga clic en **Set Object** (Establecer objeto), escriba el nombre de uno de los **objetos con seguimiento** que ha creado en la [lección anterior](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="32cb6-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="32cb6-143">Ahora, haga clic en el botón **Computer Vision** (Visión de equipo) que se encuentra en la parte inferior de la **Object Card** (Tarjeta de objeto).</span><span class="sxs-lookup"><span data-stu-id="32cb6-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="32cb6-144">Se abrirá una nueva ventana en la que tendrá que tomar seis fotos para entrenar el modelo para el reconocimiento de imágenes.</span><span class="sxs-lookup"><span data-stu-id="32cb6-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="32cb6-145">Haga clic en el botón **Camera** (Cámara) y realice una pulsación en el aire al mirar el objeto del que desea realizar un seguimiento, haga esto seis veces.</span><span class="sxs-lookup"><span data-stu-id="32cb6-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="32cb6-146">Para mejorar el entrenamiento del modelo, intente tomar cada imagen desde distintos ángulos y con distintas condiciones de iluminación.</span><span class="sxs-lookup"><span data-stu-id="32cb6-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="32cb6-147">Una vez que tenga suficientes imágenes, haga clic en el botón **Train** (Entrenar) para iniciar el proceso de entrenamiento del modelo en la nube.</span><span class="sxs-lookup"><span data-stu-id="32cb6-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="32cb6-148">Al activar el entrenamiento se cargarán todas las imágenes y, luego, comenzará el entrenamiento, lo que puede tardar un minuto o más.</span><span class="sxs-lookup"><span data-stu-id="32cb6-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="32cb6-149">Un mensaje dentro del menú indica el progreso actual y, una vez que indica la finalización, puede detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="32cb6-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="32cb6-150">**ObjectDetectionManager (script)** carga directamente las imágenes tomadas en el servicio Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="32cb6-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="32cb6-151">Como alternativa, Custom Vision API acepta las direcciones URL de las imágenes; como ejercicio, puede modificar **ObjectDetectionManager (script)** para que cargue las imágenes en un almacenamiento de blobs en su lugar.</span><span class="sxs-lookup"><span data-stu-id="32cb6-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="32cb6-152">Detección de objetos</span><span class="sxs-lookup"><span data-stu-id="32cb6-152">Detect objects</span></span>

<span data-ttu-id="32cb6-153">Ahora puede poner a prueba el modelo entrenado; ejecute la aplicación y, en el *menú principal* haga clic en **Search Object** (Buscar objeto) y escriba el nombre del **objeto con seguimiento** en cuestión.</span><span class="sxs-lookup"><span data-stu-id="32cb6-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="32cb6-154">Aparecerá **Object Card** (Tarjeta de objeto) y haga clic en el botón **Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="32cb6-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="32cb6-155">Desde aquí, **ObjectDetectionManager** comenzará a tomar capturas de imagen en segundo plano desde la cámara, y el progreso se indicará en el menú.</span><span class="sxs-lookup"><span data-stu-id="32cb6-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="32cb6-156">Apunte la cámara al objeto que usó para entrenar el modelo y verá que, después de un breve lapso, detectará el objeto.</span><span class="sxs-lookup"><span data-stu-id="32cb6-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="32cb6-157">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="32cb6-157">Congratulations</span></span>

<span data-ttu-id="32cb6-158">En este tutorial ha aprendido cómo se puede usar Azure Custom Vision para entrenar imágenes y usar el servicio de clasificación para detectar imágenes que coincidan con el **objeto con seguimiento** asociado.</span><span class="sxs-lookup"><span data-stu-id="32cb6-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="32cb6-159">En el siguiente tutorial aprenderá a usar Azure Spatial Anchors para vincular un *objeto con seguimiento* a una ubicación en el mundo físico y a mostrar una flecha que le devolverá al usuario a la ubicación vinculada del objeto con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="32cb6-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

[<span data-ttu-id="32cb6-160">Tutorial siguiente: 4. Integración de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="32cb6-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
