---
title: 'Caso práctico: creación de HoloSketch, un diseño espacial y una aplicación de boceto de experiencia de usuario para HoloLens'
description: HoloSketch es un diseño espacial en el dispositivo y una herramienta de boceto de la experiencia del usuario para HoloLens que ayuda a crear experiencias holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, boceto, aplicación
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524548"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="c1b66-104">Caso práctico: creación de HoloSketch, un diseño espacial y una aplicación de boceto de experiencia de usuario para HoloLens</span><span class="sxs-lookup"><span data-stu-id="c1b66-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="c1b66-105">HoloSketch es un diseño espacial en el dispositivo y una herramienta de boceto de la experiencia del usuario para HoloLens que ayuda a crear experiencias holográficas.</span><span class="sxs-lookup"><span data-stu-id="c1b66-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="c1b66-106">HoloSketch funciona con un teclado y un mouse Bluetooth emparejados, así como con comandos de gestos y voz.</span><span class="sxs-lookup"><span data-stu-id="c1b66-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="c1b66-107">El objetivo de HoloSketch es proporcionar una sencilla herramienta de diseño de la experiencia de usuario para la visualización y la iteración rápidas.</span><span class="sxs-lookup"><span data-stu-id="c1b66-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="c1b66-108">![HoloSketch: Una aplicación de diseño espacial y de boceto de la experiencia de usuario para HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="c1b66-109">*HoloSketch: aplicación de diseño espacial y de boceto de la experiencia de usuario para HoloLens*</span><span class="sxs-lookup"><span data-stu-id="c1b66-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="c1b66-110">![Una herramienta de diseño de experiencia de usuario sencilla para una visualización rápida e iteración.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="c1b66-111">*Una herramienta de diseño de experiencia de usuario sencilla para una visualización rápida e iteración*</span><span class="sxs-lookup"><span data-stu-id="c1b66-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="c1b66-112">Características</span><span class="sxs-lookup"><span data-stu-id="c1b66-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="c1b66-113">Primitivas para estudios rápidos y creación de prototipos de escalado</span><span class="sxs-lookup"><span data-stu-id="c1b66-113">Primitives for quick studies and scale-prototyping</span></span>

![Usar formas primitivas](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="c1b66-115">Use formas primitivas para los estudios y la creación de prototipos de escalado rápido.</span><span class="sxs-lookup"><span data-stu-id="c1b66-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="c1b66-116">Importar objetos a través de OneDrive</span><span class="sxs-lookup"><span data-stu-id="c1b66-116">Import objects through OneDrive</span></span>

![importar objetos](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="c1b66-118">Importe imágenes PNG/JPG o objetos FBX 3D (requiere empaquetado en Unity) en el espacio de realidad mixta a través de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="c1b66-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="c1b66-119">Manipular objetos</span><span class="sxs-lookup"><span data-stu-id="c1b66-119">Manipulate objects</span></span>

![manipular objetos](images/manipulate-objects-640px.jpg)

<span data-ttu-id="c1b66-121">Manipular objetos (Move/Rotate/Scale) con una interfaz de objeto 3D conocida.</span><span class="sxs-lookup"><span data-stu-id="c1b66-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="c1b66-122">Bluetooth, Mouse/teclado, gestos y comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c1b66-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![admite Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="c1b66-124">HoloSketch admite comandos de mouse/teclado, gestos y comandos de voz de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="c1b66-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="c1b66-125">Background</span><span class="sxs-lookup"><span data-stu-id="c1b66-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="c1b66-126">Importancia de experimentar el diseño en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="c1b66-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="c1b66-127">Al diseñar algo para HoloLens, es importante experimentar el diseño en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c1b66-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="c1b66-128">Uno de los mayores desafíos en el diseño de aplicaciones de realidad mixta es que es difícil obtener el sentido de la escala, la posición y la profundidad, especialmente a través de los bocetos 2D tradicionales.</span><span class="sxs-lookup"><span data-stu-id="c1b66-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="c1b66-129">Costo de la comunicación basada en 2D</span><span class="sxs-lookup"><span data-stu-id="c1b66-129">Cost of 2D based communication</span></span>

<span data-ttu-id="c1b66-130">Para comunicar de forma eficaz los flujos y escenarios de la experiencia de usuario a otros, un diseñador puede acabar invirtiendo mucho tiempo en crear recursos mediante herramientas tradicionales de 2D como Illustrator, Photoshop y PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="c1b66-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="c1b66-131">Estos diseños 2D suelen requerir un esfuerzo adicional para convertirlos en 3D.</span><span class="sxs-lookup"><span data-stu-id="c1b66-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="c1b66-132">En esta traducción se pierden algunas ideas de 2D a 3D.</span><span class="sxs-lookup"><span data-stu-id="c1b66-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="c1b66-133">Proceso de implementación complejo</span><span class="sxs-lookup"><span data-stu-id="c1b66-133">Complex deployment process</span></span>

<span data-ttu-id="c1b66-134">Dado que la realidad mixta es un nuevo lienzo para nosotros, implica una gran cantidad de iteración de diseño y de prueba y error por su naturaleza.</span><span class="sxs-lookup"><span data-stu-id="c1b66-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="c1b66-135">En el caso de los diseñadores que no están familiarizados con herramientas como Unity y Visual Studio, no es fácil poner nada en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c1b66-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="c1b66-136">Normalmente tiene que seguir el proceso siguiente para ver la ilustración 2D/3D en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c1b66-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="c1b66-137">Esta era una gran barrera para diseñadores que recorren ideas y escenarios rápidamente.</span><span class="sxs-lookup"><span data-stu-id="c1b66-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="c1b66-138">![Proceso de implementación complejo](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="c1b66-139">*Proceso de implementación*</span><span class="sxs-lookup"><span data-stu-id="c1b66-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="c1b66-140">Proceso simplificado con HoloSketch</span><span class="sxs-lookup"><span data-stu-id="c1b66-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="c1b66-141">Con HoloSketch, queríamos simplificar este proceso sin involucrar las herramientas de desarrollo y el emparejamiento del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c1b66-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="c1b66-142">Con OneDrive, los usuarios pueden colocar fácilmente activos 2D/3D en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c1b66-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="c1b66-143">![Proceso simplificado con HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="c1b66-144">*Proceso simplificado con HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="c1b66-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="c1b66-145">Fomento de soluciones y pensamiento de diseño de tres dimensiones</span><span class="sxs-lookup"><span data-stu-id="c1b66-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="c1b66-146">Pensamos que esta herramienta proporciona a los diseñadores una oportunidad para explorar soluciones en un espacio realmente tridimensional y no estar atascadas en 2D.</span><span class="sxs-lookup"><span data-stu-id="c1b66-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="c1b66-147">No tienen que preocuparse por crear un fondo 3D para su interfaz de usuario, ya que el fondo es el mundo real en el caso de Hololens.</span><span class="sxs-lookup"><span data-stu-id="c1b66-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="c1b66-148">HoloSketch abre una forma para que los diseñadores exploren fácilmente el diseño 3D en Hololens.</span><span class="sxs-lookup"><span data-stu-id="c1b66-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="c1b66-149">Comenzar</span><span class="sxs-lookup"><span data-stu-id="c1b66-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="c1b66-150">Cómo importar imágenes 2D (JPG/PNG) en HoloSketch</span><span class="sxs-lookup"><span data-stu-id="c1b66-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="c1b66-151">Cargue imágenes JPG/PNG en la carpeta de OneDrive "Documents/HoloSketch".</span><span class="sxs-lookup"><span data-stu-id="c1b66-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="c1b66-152">En el menú de OneDrive de HoloSketch, podrá seleccionar y colocar la imagen en el entorno.</span><span class="sxs-lookup"><span data-stu-id="c1b66-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="c1b66-153">![Importar imágenes 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1b66-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="c1b66-154">*Importación de imágenes y objetos 3D a través de OneDrive*</span><span class="sxs-lookup"><span data-stu-id="c1b66-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="c1b66-155">Cómo importar objetos 3D en HoloSketch</span><span class="sxs-lookup"><span data-stu-id="c1b66-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="c1b66-156">Antes de cargar en su carpeta de OneDrive, siga los pasos que se indican a continuación para empaquetar los objetos 3D en un paquete de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="c1b66-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="c1b66-157">Con este proceso puede importar los archivos FBX/OBJ del software 3D, como Maya, Cinema 4D y Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="c1b66-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c1b66-158">Actualmente, la creación de paquetes de activos es compatible con la versión de Unity 5.4.5 F1.</span><span class="sxs-lookup"><span data-stu-id="c1b66-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="c1b66-159">Descargue y abra el proyecto de Unity ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="c1b66-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="c1b66-160">Este proyecto de Unity incluye el script para la generación de recursos de agrupación.</span><span class="sxs-lookup"><span data-stu-id="c1b66-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="c1b66-161">Cree un nuevo GameObject.</span><span class="sxs-lookup"><span data-stu-id="c1b66-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="c1b66-162">Asigne el nombre GameObject a la base de contenido.</span><span class="sxs-lookup"><span data-stu-id="c1b66-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="c1b66-163">En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador '.</span><span class="sxs-lookup"><span data-stu-id="c1b66-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador '](images/holosketch-10a-assetbundles-1000px.png)
   
   ![En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador ' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="c1b66-166">Importe el archivo FBX 3D arrastrándolo al panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="c1b66-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="c1b66-167">Arrastre el objeto al panel jerarquía **bajo el nuevo GameObject**.</span><span class="sxs-lookup"><span data-stu-id="c1b66-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Arrastre el objeto al panel jerarquía bajo el nuevo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="c1b66-169">Ajuste la dimensión del Colisionador si no coincide con el objeto.</span><span class="sxs-lookup"><span data-stu-id="c1b66-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="c1b66-170">Gire el objeto al **eje Z de**la esfera.</span><span class="sxs-lookup"><span data-stu-id="c1b66-170">Rotate the object to face **Z-axis**.</span></span>

   ![Ajuste la dimensión del Colisionador si no coincide con el objeto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="c1b66-172">Arrastre el objeto desde el panel jerarquía hasta el panel Proyecto para **convertirlo en recurso prefabricado**.</span><span class="sxs-lookup"><span data-stu-id="c1b66-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="c1b66-173">En la parte inferior del panel Inspector, haga clic en la lista desplegable, crear y asignar un nuevo nombre único.</span><span class="sxs-lookup"><span data-stu-id="c1b66-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="c1b66-174">En el ejemplo siguiente se muestra cómo agregar y asignar ' brownchair ' para el nombre de AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="c1b66-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![En la parte inferior del panel Inspector, haga clic en la lista desplegable y asigne un nuevo nombre único.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="c1b66-176">Preparar una imagen en miniatura para el objeto de modelo.</span><span class="sxs-lookup"><span data-stu-id="c1b66-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="c1b66-177">![Arrastre una imagen al panel Proyecto y asigne el nombre usado para el objeto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="c1b66-178">Cree una carpeta denominada ' Assetbundles ' en la carpeta ' Asset ' del proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="c1b66-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="c1b66-179">En el menú activos, seleccione ' compilar AssetBundles ' para generar el archivo.</span><span class="sxs-lookup"><span data-stu-id="c1b66-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="c1b66-180">![En el menú activos, seleccione ' compilar AssetBundles ' para generar el archivo.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="c1b66-181">**Cargue el archivo generado en la carpeta/Files/Documents/HoloSketch en OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="c1b66-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="c1b66-182">Cargue solo el archivo asset_unique_name.</span><span class="sxs-lookup"><span data-stu-id="c1b66-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="c1b66-183">No es necesario cargar los archivos de manifiesto o el archivo AssetBundles.</span><span class="sxs-lookup"><span data-stu-id="c1b66-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="c1b66-184">![Agregar archivos a archivos/documentos/HoloSketch/carpeta](images/holosketch-onedriveupload-1000px.png)
![verá el objeto 3D agregado en el menú de OneDrive de HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1b66-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="c1b66-185">Cómo manipular los objetos</span><span class="sxs-lookup"><span data-stu-id="c1b66-185">How to manipulate the objects</span></span>

<span data-ttu-id="c1b66-186">HoloSketch admite la interfaz tradicional que se usa ampliamente en el software 3D.</span><span class="sxs-lookup"><span data-stu-id="c1b66-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="c1b66-187">Puede usar la acción de desplazar, girar y escalar los objetos con gestos y un mouse.</span><span class="sxs-lookup"><span data-stu-id="c1b66-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="c1b66-188">Puede cambiar rápidamente entre diferentes modos con voz o teclado.</span><span class="sxs-lookup"><span data-stu-id="c1b66-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="c1b66-189">Modos de manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="c1b66-189">Object manipulation modes</span></span>

<span data-ttu-id="c1b66-190">![Cómo manipular los objetos](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="c1b66-191">*Cómo manipular los objetos*</span><span class="sxs-lookup"><span data-stu-id="c1b66-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="c1b66-192">Menús contextuales y cinturón de herramientas</span><span class="sxs-lookup"><span data-stu-id="c1b66-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="c1b66-193">**Usar el menú contextual**</span><span class="sxs-lookup"><span data-stu-id="c1b66-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="c1b66-194">Doble aire Puntee para abrir el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="c1b66-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="c1b66-195">Elementos de menú:</span><span class="sxs-lookup"><span data-stu-id="c1b66-195">Menu items:</span></span>
* <span data-ttu-id="c1b66-196">**Superficie de diseño:** Se trata de un sistema de cuadrícula 3D en el que puede diseñar varios objetos y administrarlos como un grupo.</span><span class="sxs-lookup"><span data-stu-id="c1b66-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="c1b66-197">Haga doble punteo en la superficie de diseño para agregarle objetos.</span><span class="sxs-lookup"><span data-stu-id="c1b66-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="c1b66-198">**Primitives** Use cubos, esferas, cilindros y conos para estudios en masa.</span><span class="sxs-lookup"><span data-stu-id="c1b66-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="c1b66-199">**OneDrive:** Abra el menú de OneDrive para importar objetos.</span><span class="sxs-lookup"><span data-stu-id="c1b66-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="c1b66-200">**Ayuda:** Muestra la pantalla de ayuda.</span><span class="sxs-lookup"><span data-stu-id="c1b66-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="c1b66-201">![Menú contextual](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="c1b66-202">*Menú contextual*</span><span class="sxs-lookup"><span data-stu-id="c1b66-202">*Contextual menu*</span></span>

<span data-ttu-id="c1b66-203">**Usar el menú de la herramienta cinturón**</span><span class="sxs-lookup"><span data-stu-id="c1b66-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="c1b66-204">La escena de movimiento, giro, escala, guardado y carga está disponible en el menú de cinturón de herramientas.</span><span class="sxs-lookup"><span data-stu-id="c1b66-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="c1b66-205">Usar comandos de teclado, gestos y voz</span><span class="sxs-lookup"><span data-stu-id="c1b66-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="c1b66-206">![Comandos de teclado, gestos y voz](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c1b66-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="c1b66-207">*Teclado, gestos y comandos de voz*</span><span class="sxs-lookup"><span data-stu-id="c1b66-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="c1b66-208">Descarga de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c1b66-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="c1b66-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Descargue e instale la aplicación HoloSketch gratuitamente desde el Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="c1b66-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="c1b66-210">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="c1b66-210">Known issues</span></span>
* <span data-ttu-id="c1b66-211">Actualmente se admite la creación de paquetes de activos con la **versión de Unity 5.4.5 F1.**</span><span class="sxs-lookup"><span data-stu-id="c1b66-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="c1b66-212">En función de la cantidad de datos en OneDrive, la aplicación podría aparecer como si se hubiera detenido mientras se cargaba el contenido de OneDrive</span><span class="sxs-lookup"><span data-stu-id="c1b66-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="c1b66-213">Actualmente, la característica de guardar y cargar solo admite objetos primitivos</span><span class="sxs-lookup"><span data-stu-id="c1b66-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="c1b66-214">Los menús texto, sonido, vídeo y foto están deshabilitados en el menú contextual</span><span class="sxs-lookup"><span data-stu-id="c1b66-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="c1b66-215">El botón reproducir del menú del cinturón de herramientas borra la Gizmos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="c1b66-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="c1b66-216">Compartir bocetos</span><span class="sxs-lookup"><span data-stu-id="c1b66-216">Sharing your sketches</span></span>

<span data-ttu-id="c1b66-217">Puede usar la característica de grabación de vídeo de HoloLens diciendo "Hola Cortana, iniciar/detener grabación".</span><span class="sxs-lookup"><span data-stu-id="c1b66-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="c1b66-218">Presione la tecla subir/bajar volumen para tomar una foto del boceto.</span><span class="sxs-lookup"><span data-stu-id="c1b66-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="c1b66-219">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="c1b66-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c1b66-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="c1b66-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c1b66-221">Diseñador de la experiencia del usuario@Microsoft</span><span class="sxs-lookup"><span data-stu-id="c1b66-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c1b66-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="c1b66-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="c1b66-223">Desarrollador@Microsoft</span><span class="sxs-lookup"><span data-stu-id="c1b66-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
