---
title: Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)
description: Cómo crear los iniciadores de aplicaciones 3D y los logotipos de Windows Mixed Reality UWP aplicaciones y juegos (que se distribuyen a través de la Microsoft Store), tanto en HoloLens e inmersivos (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, iniciador 3D, mosaico, cubo en vivo, vínculo profundo, secondarytile, mosaico secundario, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605735"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="1d0ec-104">Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)</span><span class="sxs-lookup"><span data-stu-id="1d0ec-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="1d0ec-105">Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para inmersivos y es compatible con HoloLens con Windows Update 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="1d0ec-106">Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.16299 en Inmersivos y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="1d0ec-107">Puede encontrar el SDK de Windows más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="1d0ec-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="1d0ec-108">El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="1d0ec-109">Al crear una aplicación de UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras 2D con el logotipo de su aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="1d0ec-110">Al desarrollar experiencias para Windows Mixed Reality, opcionalmente, puede definirse un iniciador 3D para invalidar el iniciador 2D predeterminado para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="1d0ec-111">En general, se recomiendan los iniciadores de 3D para iniciar aplicaciones envolventes que llevará a los usuarios fuera de Windows Mixed Reality principal, mientras que el iniciador 2D predeterminada es preferible cuando se activa la aplicación en su lugar.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="1d0ec-112">También puede crear un [vínculo profundo 3D (secondaryTile)](#3d-deep-links-secondarytiles) como un selector de 3D al contenido dentro de una aplicación para UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="1d0ec-113">Proceso de creación de una aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="1d0ec-113">3D app launcher creation process</span></span>

<span data-ttu-id="1d0ec-114">Hay 3 pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="1d0ec-115">Diseñar y concepting</span><span class="sxs-lookup"><span data-stu-id="1d0ec-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="1d0ec-116">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="1d0ec-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="1d0ec-117">La integración en la aplicación (en este artículo)</span><span class="sxs-lookup"><span data-stu-id="1d0ec-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="1d0ec-118">Recursos 3D que se usará como los iniciadores para su aplicación deben crearse mediante el [Windows Mixed Reality directrices de edición](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="1d0ec-119">Los activos que no cumplan esta especificación de creación no se representará en el inicio de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="1d0ec-120">Configurar el iniciador de 3D</span><span class="sxs-lookup"><span data-stu-id="1d0ec-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="1d0ec-121">Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="1d0ec-122">Para reemplazar este 2D representación con un modelo 3D personalizado editar el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición de mosaico predeterminado.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="1d0ec-123">Para revertir a la 2D iniciador simplemente quite la definición de MixedRealityModel del manifiesto.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="1d0ec-124">XML</span><span class="sxs-lookup"><span data-stu-id="1d0ec-124">XML</span></span>

<span data-ttu-id="1d0ec-125">En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="1d0ec-126">De forma predeterminada, el manifiesto se denominará Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="1d0ec-127">Si usa Visual Studio, a continuación, haga clic en el manifiesto en el Visor de la solución y seleccione **ver código fuente** para abrir el código xml para su edición.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="1d0ec-128">En la parte superior del manifiesto, agregue el esquema uap5 e inclúyalo como un espacio de nombres puede pasar por alto:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="1d0ec-129">A continuación, especifique el "MixedRealityModel" en el icono predeterminado para la aplicación:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="1d0ec-130">Los elementos MixedRealityModel acepta una ruta de acceso que apunta a un recurso 3D almacenado en el paquete de aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="1d0ec-131">Actualmente los modelos 3D sólo entregan mediante el formato de archivo .glb y escriben contra la [instrucciones de creación de activos 3D de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) son compatibles.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="1d0ec-132">Activos deben almacenarse en el paquete de aplicación y la animación no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="1d0ec-133">Si se deja en blanco el parámetro "Path" Windows mostrará la Pizarra 2D en lugar del iniciador de 3D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="1d0ec-134">**Nota:** .glb activo debe estar marcado como "Contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="1d0ec-135">![Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarla como "Contenido" en la configuración de compilación](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="1d0ec-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="1d0ec-136">*Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarla como "Contenido" en la configuración de compilación*</span><span class="sxs-lookup"><span data-stu-id="1d0ec-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="1d0ec-137">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="1d0ec-137">Bounding box</span></span>

<span data-ttu-id="1d0ec-138">Un cuadro de límite se puede usar para agregar, opcionalmente, una región de un búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="1d0ec-139">El cuadro de límite se especifica mediante un punto central y las extensiones que indican la distancia desde el centro del cuadro de límite para los bordes en cada eje.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="1d0ec-140">Se pueden asignar unidades para el cuadro de límite a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="1d0ec-141">Si no se proporciona un cuadro de límite, a continuación, uno se se ajustan automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="1d0ec-142">Si el rectángulo proporcionado es menor que el modelo, se ajustará para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="1d0ec-143">Compatibilidad con el atributo de cuadro de límite viene con la actualización de Windows RS4 como una propiedad en el elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="1d0ec-144">Para definir un rectángulo en primer lugar en la parte superior de la aplicación de manifiesto, agregue el esquema uap6 e inclúyalo como espacios de nombres puede pasar por alto:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="1d0ec-145">A continuación, en el MixedRealityModel establezca la propiedad SpatialBoundingBox para definir el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="1d0ec-146">Uso de Unity</span><span class="sxs-lookup"><span data-stu-id="1d0ec-146">Using Unity</span></span>

<span data-ttu-id="1d0ec-147">Cuando se trabaja con Unity el proyecto debe compilado y se abre en Visual Studio antes de que se puede editar el manifiesto de aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="1d0ec-148">Debe volver a definir el iniciador de 3D en el manifiesto al compilar e implementar una nueva solución de Visual Studio desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="1d0ec-149">3D profundo vincula (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="1d0ec-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="1d0ec-150">Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para inmersivos (VR) y como parte de la de abril de 2018 actualización (RS4) para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="1d0ec-151">Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.16299 en inmersivos (VR) y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="1d0ec-152">Puede encontrar el SDK de Windows más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="1d0ec-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d0ec-153">Vínculos profundos 3D (secondaryTiles) solo funcionan con las aplicaciones para UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="1d0ec-154">Sin embargo, puede crear un [iniciador de aplicaciones 3D](implementing-3d-app-launchers.md) para iniciar una aplicación desde el inicio de Windows Mixed Reality exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="1d0ec-155">Se pueden mejorar sus aplicaciones 2D para Windows Mixed Reality agregando la capacidad para colocar los modelos 3D de la aplicación en el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) como vínculos profundos a contenido dentro de la aplicación 2D, al igual que [secundaria 2D iconos](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) en el menú Inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="1d0ec-156">Por ejemplo, puede crear photospheres de 360° que vinculan directamente en una aplicación de Visor de fotos de 360° o que los usuarios puedan colocar contenido 3D de una colección de recursos que se abre una página de detalles acerca del autor.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="1d0ec-157">Estos son sólo un par de formas para expandir la funcionalidad de la aplicación 2D con contenido 3D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="1d0ec-158">Creación de un "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="1d0ec-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="1d0ec-159">Puede colocar contenido 3D de la aplicación mediante "secondaryTiles" mediante la definición de un modelo de realidad mixta en tiempo de creación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="1d0ec-160">Se crean modelos de realidad mixta haciendo referencia a un recurso de 3D en el paquete de aplicación y, opcionalmente, definir un rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="1d0ec-161">No se admite actualmente la creación de "secondaryTiles" desde dentro de una vista exclusiva.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="1d0ec-162">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="1d0ec-162">Bounding box</span></span>

<span data-ttu-id="1d0ec-163">Un cuadro de límite se puede usar para agregar una región de un búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="1d0ec-164">El cuadro de límite se especifica mediante un punto central y las extensiones que indican la distancia desde el centro del cuadro de límite para los bordes en cada eje.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="1d0ec-165">Se pueden asignar unidades para el cuadro de límite a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="1d0ec-166">Si no se proporciona un cuadro de límite, a continuación, uno se se ajustan automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="1d0ec-167">Si el rectángulo proporcionado es menor que el modelo, se ajustará para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="1d0ec-168">Comportamiento de activación</span><span class="sxs-lookup"><span data-stu-id="1d0ec-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="1d0ec-169">Esta característica se admitirá a partir de la actualización de Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="1d0ec-170">Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.17125 si va a usar esta característica</span><span class="sxs-lookup"><span data-stu-id="1d0ec-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="1d0ec-171">Puede definir el comportamiento de activación para un secondaryTile 3D controlar cómo reacciona cuando un usuario lo selecciona.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="1d0ec-172">Esto puede utilizarse para colocar objetos 3D en la realidad mixta principal que son purley decorativo o informativo.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="1d0ec-173">Se admiten los siguientes tipos de comportamiento de activación:</span><span class="sxs-lookup"><span data-stu-id="1d0ec-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="1d0ec-174">Default: Cuando un usuario selecciona el secondaryTile 3D se activa la aplicación</span><span class="sxs-lookup"><span data-stu-id="1d0ec-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="1d0ec-175">Ninguno: No se activa cuando el usuario selecciona el secondaryTile 3D no ocurre nada y la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="1d0ec-176">Obtener y actualizar una existente "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="1d0ec-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="1d0ec-177">Los desarrolladores pueden obtener una lista de sus iconos secundarios existentes, que incluye las propiedades que ha especificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="1d0ec-178">También puede actualizar las propiedades cambiando el valor y, a continuación, llamar a UpdateAsync().</span><span class="sxs-lookup"><span data-stu-id="1d0ec-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="1d0ec-179">Comprobando que el usuario está en Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d0ec-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="1d0ec-180">Solo se pueden crear vínculos profundos 3D (secondaryTiles) mientras se muestra la vista en auriculares de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="1d0ec-181">Cuando la vista no es que se presenta en auriculares de realidad mixta de Windows, se recomienda tratar correctamente de eso por ocultar el punto de entrada o mostrar un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="1d0ec-182">Puede comprobarlo mediante la consulta [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="1d0ec-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="1d0ec-183">Notificaciones de icono</span><span class="sxs-lookup"><span data-stu-id="1d0ec-183">Tile notifications</span></span>

<span data-ttu-id="1d0ec-184">Las notificaciones de icono no admiten actualmente enviar una actualización con un recurso de 3D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="1d0ec-185">Esto significa que los desarrolladores no podrán hacer lo siguiente</span><span class="sxs-lookup"><span data-stu-id="1d0ec-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="1d0ec-186">Notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="1d0ec-186">Push Notifications</span></span>
* <span data-ttu-id="1d0ec-187">Sondeo periódico</span><span class="sxs-lookup"><span data-stu-id="1d0ec-187">Periodic Polling</span></span>
* <span data-ttu-id="1d0ec-188">Notificaciones programadas</span><span class="sxs-lookup"><span data-stu-id="1d0ec-188">Scheduled Notifications</span></span>

<span data-ttu-id="1d0ec-189">Para obtener más información sobre los otros iconos de las características y los atributos y cómo se usan para los iconos 2D hacen referencia a la [iconos para la documentación de aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="1d0ec-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d0ec-190">Vea también</span><span class="sxs-lookup"><span data-stu-id="1d0ec-190">See also</span></span>

* <span data-ttu-id="1d0ec-191">[Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="1d0ec-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="1d0ec-192">Guía de diseño de la aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="1d0ec-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="1d0ec-193">Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d0ec-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="1d0ec-194">Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="1d0ec-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="1d0ec-195">Navegar por el inicio de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d0ec-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
