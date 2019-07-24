---
title: Habilitar la selección de ubicación de modelos 3D en el hogar
description: Cómo colocar modelos 3D desde su sitio web o aplicación en la Página principal de Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar en casa, lugar, mundo, modelado, Página principal de la realidad mixta, Web, aplicación
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829734"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="64239-104">Habilitar la selección de ubicación de modelos 3D en la Página principal de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="64239-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="64239-105">Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="64239-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="64239-106">Las versiones anteriores de Windows no son compatibles con esta característica.</span><span class="sxs-lookup"><span data-stu-id="64239-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="64239-107">La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="64239-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="64239-108">En algunos escenarios, las aplicaciones 2D (como la aplicación de hologramas) permiten colocar los modelos 3D directamente en la Página principal de la realidad mixta como decoración o para realizar más inspecciones en 3D completo.</span><span class="sxs-lookup"><span data-stu-id="64239-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="64239-109">El *Protocolo agregar modelo* le permite enviar un modelo 3D desde su sitio web o aplicación directamente a la Página principal de Windows Mixed Reality, donde se conservará como iniciadores de [aplicaciones 3D](3d-app-launcher-design-guidance.md), aplicaciones 2D y hologramas.</span><span class="sxs-lookup"><span data-stu-id="64239-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="64239-110">Por ejemplo, si está desarrollando una aplicación que muestra un catálogo de mobiliario 3D para diseñar un espacio, puede usar el *Protocolo agregar modelo* para permitir que los usuarios coloquen esos modelos de mobiliario 3D desde el catálogo.</span><span class="sxs-lookup"><span data-stu-id="64239-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="64239-111">Una vez colocado en el mundo, los usuarios pueden moverse, cambiar de tamaño y quitar estos modelos 3D igual que otros hologramas en el hogar.</span><span class="sxs-lookup"><span data-stu-id="64239-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="64239-112">En este artículo se proporciona información general sobre la implementación del *Protocolo de adición de modelos* para que pueda empezar a permitir a los usuarios decorar su mundo con objetos 3D desde la aplicación o la Web.</span><span class="sxs-lookup"><span data-stu-id="64239-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="64239-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="64239-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="64239-114"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="64239-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="64239-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="64239-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="64239-116"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="64239-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="64239-117">Agregar protocolo de modelo</span><span class="sxs-lookup"><span data-stu-id="64239-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="64239-118">✔️</span><span class="sxs-lookup"><span data-stu-id="64239-118">✔️</span></span></td>
        <td><span data-ttu-id="64239-119">✔️</span><span class="sxs-lookup"><span data-stu-id="64239-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="64239-120">Información general</span><span class="sxs-lookup"><span data-stu-id="64239-120">Overview</span></span>

<span data-ttu-id="64239-121">Hay 2 pasos para habilitar la selección de ubicación de modelos 3D en la Página principal de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="64239-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="64239-122">[Asegúrese de que el modelo 3D es compatible con la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="64239-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="64239-123">Implemente el *Protocolo de adición de modelos* en la aplicación o la página web (este artículo).</span><span class="sxs-lookup"><span data-stu-id="64239-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="64239-124">Implementación del *Protocolo Add Model*</span><span class="sxs-lookup"><span data-stu-id="64239-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="64239-125">Una vez que tenga un [modelo 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), puede implementar el *Protocolo agregar modelo* activando el URI siguiente desde cualquier página web o aplicación:</span><span class="sxs-lookup"><span data-stu-id="64239-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="64239-126">Si el URI apunta a un recurso remoto, se descargará automáticamente y se colocará en el hogar.</span><span class="sxs-lookup"><span data-stu-id="64239-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="64239-127">Los recursos locales se copiarán en la carpeta de datos de la aplicación de la Página principal de la realidad mixta antes de colocarse en el hogar.</span><span class="sxs-lookup"><span data-stu-id="64239-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="64239-128">Se recomienda diseñar su experiencia para tener en cuenta los escenarios en los que el usuario podría estar ejecutando una versión anterior de Windows que no admita esta característica ocultando el botón o deshabilitando si es posible.</span><span class="sxs-lookup"><span data-stu-id="64239-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="64239-129">Invocar el *Protocolo agregar modelo* desde una aplicación plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="64239-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="64239-130">Invocar el *Protocolo de agregar modelo* desde una página web:</span><span class="sxs-lookup"><span data-stu-id="64239-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="64239-131">Consideraciones sobre los auriculares envolventes (VR)</span><span class="sxs-lookup"><span data-stu-id="64239-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="64239-132">En el caso de los auriculares envolventes (VR), el portal de realidad mixta no tiene que estar en ejecución antes de invocar el *Protocolo de adición del modelo*.</span><span class="sxs-lookup"><span data-stu-id="64239-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="64239-133">En este caso, el *Protocolo de adición del modelo* iniciará el portal de realidad mixta y colocará el objeto directamente, donde el casco está mirando una vez que llega a la Página principal de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="64239-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="64239-134">Al invocar el *Protocolo agregar modelo* desde el escritorio con el portal de realidad mixta que ya se está ejecutando, asegúrese de que el casco esté "activo".</span><span class="sxs-lookup"><span data-stu-id="64239-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="64239-135">Si no es así, la selección de ubicación no se realizará correctamente.</span><span class="sxs-lookup"><span data-stu-id="64239-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="64239-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="64239-136">See also</span></span>

* [<span data-ttu-id="64239-137">Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="64239-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="64239-138">Desplazamiento por la página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="64239-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
