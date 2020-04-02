---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)
description: Cómo crear iniciadores de aplicaciones 3D y logotipos para aplicaciones y juegos UWP de Windows Mixed Reality (distribuidos a través de la Microsoft Store), tanto en los auriculares HoloLens como envolventes (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, selector 3D, mosaico, cubo activo, vínculo profundo, secondarytile, icono secundario, UWP
ms.openlocfilehash: 0a2e2177ffa7e381c461a58f373c818c9c5e72c4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549388"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="f3645-104">Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)</span><span class="sxs-lookup"><span data-stu-id="f3645-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="f3645-105">Esta característica se agregó como parte de la actualización de 2017 Fall Creators Update (RS3) para los auriculares más envolventes y es compatible con HoloLens con la actualización de Windows 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="f3645-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="f3645-106">Asegúrese de que la aplicación tiene como destino una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f3645-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="f3645-107">Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="f3645-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="f3645-108">La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f3645-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="f3645-109">Al crear una aplicación para UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras bidimensionales con el logotipo de su aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="f3645-110">Al desarrollar experiencias para Windows Mixed Reality, opcionalmente se puede definir un selector 3D para invalidar el iniciador de 2D predeterminado de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="f3645-111">En general, los iniciadores 3D se recomiendan para iniciar aplicaciones envolventes que sacan provecho de la Página principal de Windows Mixed Reality, mientras que el selector de 2D predeterminado es preferible cuando la aplicación se activa en su lugar.</span><span class="sxs-lookup"><span data-stu-id="f3645-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="f3645-112">También puede crear un [vínculo profundo en 3D (secondaryTile)](#3d-deep-links-secondarytiles) como un selector 3D para el contenido de una aplicación de UWP en 2D.</span><span class="sxs-lookup"><span data-stu-id="f3645-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="f3645-113">proceso de creación del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="f3645-113">3D app launcher creation process</span></span>

<span data-ttu-id="f3645-114">Hay tres pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="f3645-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="f3645-115">Diseño y concepto</span><span class="sxs-lookup"><span data-stu-id="f3645-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="f3645-116">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="f3645-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="f3645-117">Integrarlo en la aplicación (este artículo)</span><span class="sxs-lookup"><span data-stu-id="f3645-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="f3645-118">los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las [directrices de creación de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="f3645-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="f3645-119">Los recursos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f3645-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="f3645-120">Configurar el iniciador 3D</span><span class="sxs-lookup"><span data-stu-id="f3645-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="f3645-121">Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="f3645-122">Para reemplazar esta representación 2D por un modelo 3D personalizado, edite el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición del mosaico predeterminado.</span><span class="sxs-lookup"><span data-stu-id="f3645-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="f3645-123">Para revertir al iniciador de 2D, solo tiene que quitar la definición de MixedRealityModel del manifiesto.</span><span class="sxs-lookup"><span data-stu-id="f3645-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="f3645-124">XML</span><span class="sxs-lookup"><span data-stu-id="f3645-124">XML</span></span>

<span data-ttu-id="f3645-125">En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual.</span><span class="sxs-lookup"><span data-stu-id="f3645-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="f3645-126">De forma predeterminada, el manifiesto se denominará package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="f3645-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="f3645-127">Si usa Visual Studio, haga clic con el botón derecho en el manifiesto en el visor de soluciones y seleccione **Ver código fuente** para abrir el código XML y editarlo.</span><span class="sxs-lookup"><span data-stu-id="f3645-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="f3645-128">En la parte superior del manifiesto, agregue el esquema uap5 e inclúyalo como un espacio de nombres que se va a omitir:</span><span class="sxs-lookup"><span data-stu-id="f3645-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="f3645-129">A continuación, especifique "MixedRealityModel" en el icono predeterminado de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="f3645-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="f3645-130">Los elementos MixedRealityModel aceptan una ruta de acceso de archivo que apunta a un recurso 3D almacenado en el paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="f3645-131">Actualmente solo se admiten los modelos 3D que se entregan con el formato de archivo. glb y se crean con las [instrucciones de creación de recursos de Windows Mixed Reality 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) .</span><span class="sxs-lookup"><span data-stu-id="f3645-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="f3645-132">Los recursos deben almacenarse en el paquete de la aplicación y la animación no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="f3645-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="f3645-133">Si el parámetro "path" se deja en blanco, Windows mostrará la pizarra 2D en lugar del iniciador 3D.</span><span class="sxs-lookup"><span data-stu-id="f3645-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="f3645-134">**Nota:** el recurso. glb debe estar marcado como "contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="f3645-135">![seleccione. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="f3645-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="f3645-136">*Seleccione el. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación.*</span><span class="sxs-lookup"><span data-stu-id="f3645-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="f3645-137">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="f3645-137">Bounding box</span></span>

<span data-ttu-id="f3645-138">Un cuadro de límite se puede usar para agregar opcionalmente una región de búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="f3645-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="f3645-139">El cuadro de límite se especifica utilizando un punto central y extensiones que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje.</span><span class="sxs-lookup"><span data-stu-id="f3645-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="f3645-140">Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="f3645-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="f3645-141">Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="f3645-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="f3645-142">Si el cuadro de límite proporcionado es menor que el modelo, se cambiará el tamaño para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="f3645-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="f3645-143">La compatibilidad con el atributo de cuadro de límite incluirá la actualización de RS4 de Windows como una propiedad en el elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="f3645-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="f3645-144">Para definir un cuadro de límite primero en la parte superior del manifiesto de la aplicación, agregue el esquema uap6 e inclúyalo como espacios de nombres que se puedan omitir:</span><span class="sxs-lookup"><span data-stu-id="f3645-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="f3645-145">A continuación, en MixedRealityModel, establezca la propiedad SpatialBoundingBox para definir el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="f3645-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="f3645-146">Uso de Unity</span><span class="sxs-lookup"><span data-stu-id="f3645-146">Using Unity</span></span>

<span data-ttu-id="f3645-147">Al trabajar con Unity, el proyecto se debe compilar y abrir en Visual Studio para poder editar el manifiesto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3645-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="f3645-148">El iniciador 3D debe volver a definirse en el manifiesto al compilar e implementar una nueva solución de Visual Studio desde Unity.</span><span class="sxs-lookup"><span data-stu-id="f3645-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="f3645-149">vínculos profundos 3D (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="f3645-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="f3645-150">Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para auriculares envolventes (VR) y como parte de la actualización de abril de 2018 (RS4) para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f3645-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="f3645-151">Asegúrese de que la aplicación esté destinada a una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo (VR) y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f3645-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="f3645-152">Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="f3645-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="f3645-153">los vínculos profundos 3D (secondaryTiles) solo funcionan con aplicaciones UWP de 2D.</span><span class="sxs-lookup"><span data-stu-id="f3645-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="f3645-154">Sin embargo, puede crear un [iniciador de aplicaciones 3D](implementing-3d-app-launchers.md) para iniciar una aplicación exclusiva desde la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f3645-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="f3645-155">Las aplicaciones 2D se pueden mejorar para Windows Mixed Reality agregando la capacidad de colocar modelos 3D desde la aplicación en la [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) como vínculos profundos al contenido dentro de la aplicación 2D, al igual que los [mosaicos secundarios 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) en el menú Inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="f3645-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="f3645-156">Por ejemplo, puede crear fotoesferas 360 ° que se vinculan directamente a una aplicación de visor de fotos de 360 °, o bien permitir que los usuarios coloquen contenido 3D de una colección de recursos que abre una página de detalles sobre el autor.</span><span class="sxs-lookup"><span data-stu-id="f3645-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="f3645-157">Se trata de un par de formas de ampliar la funcionalidad de la aplicación 2D con contenido 3D.</span><span class="sxs-lookup"><span data-stu-id="f3645-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="f3645-158">Crear un "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="f3645-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="f3645-159">Puede colocar contenido 3D de la aplicación mediante "secondaryTiles" definiendo un modelo de realidad mixta en el momento de la creación.</span><span class="sxs-lookup"><span data-stu-id="f3645-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="f3645-160">Los modelos de realidad mixta se crean haciendo referencia a un recurso 3D en el paquete de la aplicación y definiendo opcionalmente un cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="f3645-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="f3645-161">Actualmente no se admite la creación de "secondaryTiles" desde una vista exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f3645-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="f3645-162">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="f3645-162">Bounding box</span></span>

<span data-ttu-id="f3645-163">Un cuadro de límite se puede usar para agregar una región de búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="f3645-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="f3645-164">El cuadro de límite se especifica utilizando un punto central y extensiones que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje.</span><span class="sxs-lookup"><span data-stu-id="f3645-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="f3645-165">Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="f3645-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="f3645-166">Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="f3645-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="f3645-167">Si el cuadro de límite proporcionado es menor que el modelo, se cambiará el tamaño para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="f3645-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="f3645-168">Comportamiento de activación</span><span class="sxs-lookup"><span data-stu-id="f3645-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="f3645-169">Esta característica se admitirá a partir de la actualización de RS4 de Windows.</span><span class="sxs-lookup"><span data-stu-id="f3645-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="f3645-170">Asegúrese de que la aplicación tenga como destino una versión de la Windows SDK mayor o igual que 10.0.17125 si tiene previsto usar esta característica.</span><span class="sxs-lookup"><span data-stu-id="f3645-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="f3645-171">Puede definir el comportamiento de activación de un secondaryTile de 3D para controlar cómo reacciona cuando un usuario lo selecciona.</span><span class="sxs-lookup"><span data-stu-id="f3645-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="f3645-172">Se puede usar para colocar objetos 3D en la Página principal de la realidad mixta que son meramente informativas o decorativas.</span><span class="sxs-lookup"><span data-stu-id="f3645-172">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="f3645-173">Se admiten los siguientes tipos de comportamiento de activación:</span><span class="sxs-lookup"><span data-stu-id="f3645-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="f3645-174">Valor predeterminado: cuando un usuario selecciona el secondaryTile 3D, se activa la aplicación</span><span class="sxs-lookup"><span data-stu-id="f3645-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="f3645-175">Ninguno: cuando los usuarios seleccionan el secondaryTile 3D, no sucede nada y la aplicación no está activada.</span><span class="sxs-lookup"><span data-stu-id="f3645-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="f3645-176">Obtener y actualizar un "secondaryTile" existente</span><span class="sxs-lookup"><span data-stu-id="f3645-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="f3645-177">Los desarrolladores pueden volver a obtener una lista de los mosaicos secundarios existentes, que incluye las propiedades especificadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f3645-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="f3645-178">También pueden actualizar las propiedades cambiando el valor y llamando a UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="f3645-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="f3645-179">Comprobar que el usuario está en Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3645-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="f3645-180">solo se pueden crear vínculos profundos 3D (secondaryTiles) mientras la vista se muestra en un casco de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="f3645-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="f3645-181">Cuando la vista no se presenta en un casco de realidad mixta de Windows, se recomienda controlarlo correctamente ocultando el punto de entrada o mostrando un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="f3645-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="f3645-182">Para comprobarlo, consulte [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="f3645-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="f3645-183">Notificaciones de icono</span><span class="sxs-lookup"><span data-stu-id="f3645-183">Tile notifications</span></span>

<span data-ttu-id="f3645-184">Las notificaciones de icono no admiten actualmente el envío de una actualización con un recurso 3D.</span><span class="sxs-lookup"><span data-stu-id="f3645-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="f3645-185">Esto significa que los desarrolladores no podrán hacer lo siguiente</span><span class="sxs-lookup"><span data-stu-id="f3645-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="f3645-186">Notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="f3645-186">Push Notifications</span></span>
* <span data-ttu-id="f3645-187">Sondeo periódico</span><span class="sxs-lookup"><span data-stu-id="f3645-187">Periodic Polling</span></span>
* <span data-ttu-id="f3645-188">Notificaciones programadas</span><span class="sxs-lookup"><span data-stu-id="f3645-188">Scheduled Notifications</span></span>

<span data-ttu-id="f3645-189">Para obtener más información sobre los demás iconos y características, y cómo se usan para los mosaicos de 2D, consulte la [documentación de iconos de aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="f3645-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3645-190">Vea también</span><span class="sxs-lookup"><span data-stu-id="f3645-190">See also</span></span>

* <span data-ttu-id="f3645-191">[Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="f3645-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="f3645-192">Guía de diseño del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="f3645-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="f3645-193">Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3645-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f3645-194">Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="f3645-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="f3645-195">Desplazamiento por la página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3645-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
