---
title: 'Caso práctico: creación HoloSketch, un diseño espacial y UX esbozo app para HoloLens'
description: HoloSketch es un diseño espacial en el dispositivo y UX esbozo herramienta para HoloLens ayudar a crear experiencias holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, esbozar, aplicación
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600137"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="d8c38-104">Caso práctico: creación HoloSketch, un diseño espacial y UX esbozo app para HoloLens</span><span class="sxs-lookup"><span data-stu-id="d8c38-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="d8c38-105">HoloSketch es un diseño espacial en el dispositivo y UX esbozo herramienta para HoloLens ayudar a crear experiencias holográficas.</span><span class="sxs-lookup"><span data-stu-id="d8c38-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="d8c38-106">HoloSketch funciona con un comandos de teclado y mouse, así como los gestos y voz de Bluetooth emparejados.</span><span class="sxs-lookup"><span data-stu-id="d8c38-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="d8c38-107">El propósito de HoloSketch es proporcionar una herramienta de diseño de experiencia de usuario sencilla para la iteración y visualización rápida.</span><span class="sxs-lookup"><span data-stu-id="d8c38-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="d8c38-108">![HoloSketch: Un diseño espacial y UX esbozo app para HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="d8c38-109">*HoloSketch: espacial diseño y UX esbozo app para HoloLens*</span><span class="sxs-lookup"><span data-stu-id="d8c38-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="d8c38-110">![Una herramienta de diseño de experiencia de usuario sencilla visualización rápida e iteración.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="d8c38-111">*Una herramienta de diseño de experiencia de usuario sencilla visualización rápida e iteración*</span><span class="sxs-lookup"><span data-stu-id="d8c38-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="d8c38-112">Características</span><span class="sxs-lookup"><span data-stu-id="d8c38-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="d8c38-113">Primitivas de estudios de rápido y creación de prototipos de escala</span><span class="sxs-lookup"><span data-stu-id="d8c38-113">Primitives for quick studies and scale-prototyping</span></span>

![Uso de primitivas formas](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="d8c38-115">Usar formas de primitivas de estudios massing rápidos y creación de prototipos de escala.</span><span class="sxs-lookup"><span data-stu-id="d8c38-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="d8c38-116">Importar objetos a través de OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8c38-116">Import objects through OneDrive</span></span>

![importar objetos](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="d8c38-118">Importar objetos 3D de FBX o de imágenes PNG o JPG (requiere empaquetado en Unity) en el espacio de realidad mixta mediante OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d8c38-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="d8c38-119">Manipular objetos</span><span class="sxs-lookup"><span data-stu-id="d8c38-119">Manipulate objects</span></span>

![manipulación de objetos](images/manipulate-objects-640px.jpg)

<span data-ttu-id="d8c38-121">Manipular objetos (mover o girar/escala) con una interfaz familiar objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="d8c38-122">Bluetooth, mouse y teclado, gestos y comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d8c38-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![es compatible con Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="d8c38-124">HoloSketch es compatible con Bluetooth mouse/teclado, gestos y comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d8c38-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="d8c38-125">Background</span><span class="sxs-lookup"><span data-stu-id="d8c38-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="d8c38-126">Importancia de experimentar el diseño en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="d8c38-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="d8c38-127">Al diseñar algo para HoloLens, es importante experimentar el diseño en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="d8c38-128">Uno de los mayores desafíos de diseño de aplicaciones de realidad mixta es que resulta difícil de obtener el sentido de escala, la posición y la profundidad, especialmente a través de dibujos 2D tradicionales.</span><span class="sxs-lookup"><span data-stu-id="d8c38-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="d8c38-129">Comunicación basada en el costo de 2D</span><span class="sxs-lookup"><span data-stu-id="d8c38-129">Cost of 2D based communication</span></span>

<span data-ttu-id="d8c38-130">Para comunicar de forma eficaz los flujos de experiencia de usuario y escenarios a otros usuarios, un diseñador puede acabar dedicar mucho tiempo en crear activos mediante las herramientas tradicionales de 2D como Illustrator, Photoshop y PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="d8c38-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="d8c38-131">Estos diseños 2D a menudo requieren un esfuerzo adicional para convertirlos en 3D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="d8c38-132">En esta traducción se pierden algunas ideas, de 2D a 3D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="d8c38-133">Proceso de implementación complejos</span><span class="sxs-lookup"><span data-stu-id="d8c38-133">Complex deployment process</span></span>

<span data-ttu-id="d8c38-134">Puesto que la realidad mixta es un nuevo lienzo para nosotros, implica una gran cantidad de iteración de diseño y de prueba y error por su naturaleza.</span><span class="sxs-lookup"><span data-stu-id="d8c38-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="d8c38-135">Diseñador que no están familiarizados con herramientas como Unity y Visual Studio, no es fácil poner algo en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8c38-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="d8c38-136">Normalmente, tendrá que pasar por el proceso siguiente para ver ilustraciones 2D o 3D en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="d8c38-137">Esto era una barrera grande para los diseñadores de iterar rápidamente en las ideas y escenarios.</span><span class="sxs-lookup"><span data-stu-id="d8c38-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="d8c38-138">![Proceso de implementación complejos](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="d8c38-139">*Proceso de implementación*</span><span class="sxs-lookup"><span data-stu-id="d8c38-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="d8c38-140">Proceso simplificado con HoloSketch</span><span class="sxs-lookup"><span data-stu-id="d8c38-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="d8c38-141">Con HoloSketch, queríamos simplificar este proceso sin necesidad de herramientas de desarrollo y el dispositivo de emparejamiento portal.</span><span class="sxs-lookup"><span data-stu-id="d8c38-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="d8c38-142">Uso de OneDrive, los usuarios pueden poner fácilmente activos 2D o 3D en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8c38-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="d8c38-143">![Proceso simplificado con HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="d8c38-144">*Proceso simplificado con HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="d8c38-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="d8c38-145">Fomento de soluciones y pensar en diseño tridimensional</span><span class="sxs-lookup"><span data-stu-id="d8c38-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="d8c38-146">Pensamos que esta herramienta le proporcionaría los diseñadores una oportunidad para explorar soluciones en un espacio tridimensional realmente y no esté bloqueado en 2D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="d8c38-147">No tienen que pensar en crear un plano 3D para su interfaz de usuario, ya que el fondo es el mundo real en el caso de Hololens.</span><span class="sxs-lookup"><span data-stu-id="d8c38-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="d8c38-148">Abre una manera para que los diseñadores explorar fácilmente el diseño 3D en Hololens HoloSketch.</span><span class="sxs-lookup"><span data-stu-id="d8c38-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="d8c38-149">Comenzar</span><span class="sxs-lookup"><span data-stu-id="d8c38-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="d8c38-150">Cómo importar imágenes en 2D (JPG/PNG) en HoloSketch</span><span class="sxs-lookup"><span data-stu-id="d8c38-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="d8c38-151">Cargar imágenes JPG/PNG en su carpeta de OneDrive ' Documentos/HoloSketch'.</span><span class="sxs-lookup"><span data-stu-id="d8c38-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="d8c38-152">En el menú de OneDrive en HoloSketch, podrá seleccionar y coloque la imagen en el entorno.</span><span class="sxs-lookup"><span data-stu-id="d8c38-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="d8c38-153">![Importación de imágenes en 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8c38-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="d8c38-154">*Importación de imágenes y objetos 3D a través de OneDrive*</span><span class="sxs-lookup"><span data-stu-id="d8c38-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="d8c38-155">Cómo importar objetos 3D en HoloSketch</span><span class="sxs-lookup"><span data-stu-id="d8c38-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="d8c38-156">Antes de cargarlo en la carpeta de OneDrive, siga los pasos siguientes para empaquetar los objetos 3D en un conjunto de activos de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8c38-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="d8c38-157">Mediante este proceso puede importar los archivos OBJ y FBX de software 3D, como Maya, cine 4D y Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d8c38-158">Actualmente, la creación de la agrupación de recursos es compatible con Unity versión 5.4.5f1.</span><span class="sxs-lookup"><span data-stu-id="d8c38-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="d8c38-159">Descargue y abra el proyecto de Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="d8c38-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="d8c38-160">Este proyecto de Unity incluye la secuencia de comandos para la generación de activos de agrupación.</span><span class="sxs-lookup"><span data-stu-id="d8c38-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="d8c38-161">Cree un nuevo GameObject.</span><span class="sxs-lookup"><span data-stu-id="d8c38-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="d8c38-162">Nombre el GameObject según el contenido.</span><span class="sxs-lookup"><span data-stu-id="d8c38-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="d8c38-163">En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro'.</span><span class="sxs-lookup"><span data-stu-id="d8c38-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="d8c38-166">Importar el archivo FBX 3D arrastrándolo al panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="d8c38-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="d8c38-167">Arrastre el objeto en el panel de la jerarquía **en su nuevo GameObject**.</span><span class="sxs-lookup"><span data-stu-id="d8c38-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Arrastre el objeto en el panel de jerarquía en su nuevo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="d8c38-169">Ajuste la dimensión colisionador si no coincide con el objeto.</span><span class="sxs-lookup"><span data-stu-id="d8c38-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="d8c38-170">Girar el objeto al que se enfrentan a **z**.</span><span class="sxs-lookup"><span data-stu-id="d8c38-170">Rotate the object to face **Z-axis**.</span></span>

   ![Ajustar la dimensión colisionador si no coincide con el objeto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="d8c38-172">Arrastre el objeto desde el panel de la jerarquía al panel de proyecto para **hacerla prefabricado**.</span><span class="sxs-lookup"><span data-stu-id="d8c38-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="d8c38-173">En la parte inferior del panel del inspector, haga clic en la lista desplegable, cree y asigne un nuevo nombre único.</span><span class="sxs-lookup"><span data-stu-id="d8c38-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="d8c38-174">Ejemplo siguiente muestra cómo agregar y asignar 'brownchair' para el nombre AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="d8c38-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![En la parte inferior del panel del inspector, haga clic en la lista desplegable y asigne un nuevo nombre único.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="d8c38-176">Preparar una imagen en miniatura para el objeto de modelo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="d8c38-177">![Arrastre una imagen en el panel de proyecto y asigne el nombre usado para el objeto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="d8c38-178">Cree una carpeta denominada 'Assetbundles' en carpeta de 'Activo' del proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8c38-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="d8c38-179">En el menú de recursos, seleccione compilar AssetBundles para generar el archivo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="d8c38-180">![En el menú de recursos, seleccione compilar AssetBundles para generar el archivo.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="d8c38-181">**Cargue el archivo generado en la carpeta /Files/Documents/HoloSketch en OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="d8c38-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="d8c38-182">Cargue el archivo asset_unique_name solo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="d8c38-183">No es necesario cargar los archivos de manifiesto o archivo AssetBundles.</span><span class="sxs-lookup"><span data-stu-id="d8c38-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="d8c38-184">![Agregar archivos a los archivos/documentos/HoloSketch/carpeta](images/holosketch-onedriveupload-1000px.png)
![, verá que se ha agregado el objeto 3D en el menú de OneDrive del HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8c38-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="d8c38-185">Cómo manipular los objetos</span><span class="sxs-lookup"><span data-stu-id="d8c38-185">How to manipulate the objects</span></span>

<span data-ttu-id="d8c38-186">HoloSketch es compatible con la interfaz tradicional que se usa ampliamente en software 3D.</span><span class="sxs-lookup"><span data-stu-id="d8c38-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="d8c38-187">Puede mover, girar, escalar los objetos con los gestos y un mouse.</span><span class="sxs-lookup"><span data-stu-id="d8c38-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="d8c38-188">Puede cambiar rápidamente entre los distintos modos con voz o el teclado.</span><span class="sxs-lookup"><span data-stu-id="d8c38-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="d8c38-189">Modos de manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="d8c38-189">Object manipulation modes</span></span>

<span data-ttu-id="d8c38-190">![Cómo manipular los objetos](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="d8c38-191">*Cómo manipular los objetos*</span><span class="sxs-lookup"><span data-stu-id="d8c38-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="d8c38-192">Menús contextuales y cinturón de herramientas</span><span class="sxs-lookup"><span data-stu-id="d8c38-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="d8c38-193">**Mediante el menú Contextual**</span><span class="sxs-lookup"><span data-stu-id="d8c38-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="d8c38-194">Pulsar en el aire dobles para abrir el menú Contextual.</span><span class="sxs-lookup"><span data-stu-id="d8c38-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="d8c38-195">Elementos de menú:</span><span class="sxs-lookup"><span data-stu-id="d8c38-195">Menu items:</span></span>
* <span data-ttu-id="d8c38-196">**Superficie de diseño:** Esto es un sistema 3D de cuadrícula donde puede distribuir varios objetos y administrarlos como un grupo.</span><span class="sxs-lookup"><span data-stu-id="d8c38-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="d8c38-197">Derivación de aire doble en la superficie de diseño para agregar objetos a él.</span><span class="sxs-lookup"><span data-stu-id="d8c38-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="d8c38-198">**Elementos primitivos:** Utilice los cubos, esferas, cilindros y conos para massing prácticos.</span><span class="sxs-lookup"><span data-stu-id="d8c38-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="d8c38-199">**OneDrive:** Abra el menú de OneDrive para importar objetos.</span><span class="sxs-lookup"><span data-stu-id="d8c38-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="d8c38-200">**Ayuda:** Muestra la pantalla de ayuda.</span><span class="sxs-lookup"><span data-stu-id="d8c38-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="d8c38-201">![Menú contextual](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="d8c38-202">*Menú contextual*</span><span class="sxs-lookup"><span data-stu-id="d8c38-202">*Contextual menu*</span></span>

<span data-ttu-id="d8c38-203">**Mediante el menú de cinturón de herramienta**</span><span class="sxs-lookup"><span data-stu-id="d8c38-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="d8c38-204">Mover, girar, escalar, guardar y cargar escena están disponibles en el menú de cinturón de herramienta.</span><span class="sxs-lookup"><span data-stu-id="d8c38-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="d8c38-205">Uso del teclado, gestos y comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d8c38-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="d8c38-206">![Teclado, gestos y comandos de voz](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d8c38-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="d8c38-207">*Teclado, gestos y comandos de voz*</span><span class="sxs-lookup"><span data-stu-id="d8c38-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="d8c38-208">Descargar la aplicación</span><span class="sxs-lookup"><span data-stu-id="d8c38-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="d8c38-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Descargue e instale la aplicación HoloSketch de forma gratuita desde la Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="d8c38-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="d8c38-210">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="d8c38-210">Known issues</span></span>
* <span data-ttu-id="d8c38-211">Actualmente se admite la creación de la agrupación de recursos con **5.4.5f1 de versión de Unity.**</span><span class="sxs-lookup"><span data-stu-id="d8c38-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="d8c38-212">Según la cantidad de datos en OneDrive, la aplicación podría aparecer como si se ha detenido al cargar el contenido de OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8c38-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="d8c38-213">Actualmente, guardar y cargar la característica solo admite objetos primitivos</span><span class="sxs-lookup"><span data-stu-id="d8c38-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="d8c38-214">Los menús de texto, sonido, vídeo y fotografías están deshabilitados en el menú contextual</span><span class="sxs-lookup"><span data-stu-id="d8c38-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="d8c38-215">El botón Reproducir en el menú herramienta cinturón borra el gizmos manipulación</span><span class="sxs-lookup"><span data-stu-id="d8c38-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="d8c38-216">Uso compartido de los dibujos</span><span class="sxs-lookup"><span data-stu-id="d8c38-216">Sharing your sketches</span></span>

<span data-ttu-id="d8c38-217">Puede usar la característica de grabación de vídeo en HoloLens diciendo: "Hola Cortana, iniciar o Detener grabación '.</span><span class="sxs-lookup"><span data-stu-id="d8c38-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="d8c38-218">Presione la tecla conjuntamente para tomar una foto del boceto de arriba/abajo del volumen.</span><span class="sxs-lookup"><span data-stu-id="d8c38-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="d8c38-219">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="d8c38-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d8c38-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d8c38-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d8c38-221">Diseñador UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d8c38-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d8c38-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="d8c38-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="d8c38-223">Para desarrolladores @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d8c38-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
