---
title: Permitir la colocación de los modelos 3D en la página principal
description: Cómo colocar los modelos 3D del sitio Web o aplicación en el inicio de Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar en la página principal, lugar, mundo, modelado, realidad mixta doméstica, web, aplicación
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605768"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="83e73-104">Permitir la colocación de los modelos 3D en la realidad mixta principal</span><span class="sxs-lookup"><span data-stu-id="83e73-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="83e73-105">Esta característica se agregó como parte de la [Windows 10 de abril de 2018 Update](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="83e73-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="83e73-106">Las versiones anteriores de Windows no son compatibles con esta característica.</span><span class="sxs-lookup"><span data-stu-id="83e73-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="83e73-107">El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="83e73-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="83e73-108">En algunos escenarios, las aplicaciones 2D (por ejemplo, la aplicación hologramas) permiten la colocación de los modelos 3D directamente en la página principal de realidad mixta como adornos, o para que lo inspeccione en 3D.</span><span class="sxs-lookup"><span data-stu-id="83e73-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="83e73-109">El *Agregar modelo protocolo* le permite enviar un modelo 3D desde su sitio Web o aplicación directamente en el hogar de Windows Mixed Reality donde conservará como [los iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md), aplicaciones 2D y hologramas.</span><span class="sxs-lookup"><span data-stu-id="83e73-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="83e73-110">Por ejemplo, si está desarrollando una aplicación que muestre un catálogo de muebles 3D para el diseño de un espacio, puede usar el *Agregar modelo protocolo* para permitir que los usuarios que coloquen esos modelos 3D muebles desde el catálogo.</span><span class="sxs-lookup"><span data-stu-id="83e73-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="83e73-111">Una vez colocado en el mundo, los usuarios pueden mover, cambiar el tamaño y quitar estos modelos 3D, al igual que otros hologramas en la página principal.</span><span class="sxs-lookup"><span data-stu-id="83e73-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="83e73-112">Este artículo proporciona información general de la implementación de la *Agregar modelo protocolo* para que pueda empezar permitiendo a los usuarios decorar su mundo con objetos 3D de la aplicación o la web.</span><span class="sxs-lookup"><span data-stu-id="83e73-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="83e73-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="83e73-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="83e73-114">Característica</span><span class="sxs-lookup"><span data-stu-id="83e73-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="83e73-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="83e73-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="83e73-116"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="83e73-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="83e73-117">Agregue el protocolo del modelo</span><span class="sxs-lookup"><span data-stu-id="83e73-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="83e73-118">✔️</span><span class="sxs-lookup"><span data-stu-id="83e73-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="83e73-119">✔️</span><span class="sxs-lookup"><span data-stu-id="83e73-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="83e73-120">Información general</span><span class="sxs-lookup"><span data-stu-id="83e73-120">Overview</span></span>

<span data-ttu-id="83e73-121">Hay 2 pasos para habilitar la colocación de los modelos 3D en Windows Mixed Reality principal:</span><span class="sxs-lookup"><span data-stu-id="83e73-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="83e73-122">[Asegúrese de que el modelo en 3D es compatible con el inicio de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="83e73-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="83e73-123">Implemente el *Agregar modelo protocolo* en su aplicación o página Web (en este artículo).</span><span class="sxs-lookup"><span data-stu-id="83e73-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="83e73-124">Implementar el *Agregar protocolo del modelo*</span><span class="sxs-lookup"><span data-stu-id="83e73-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="83e73-125">Una vez que tenga un [modelo 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), puede implementar la *Agregar modelo protocolo* activando el siguiente URI desde cualquier página Web o aplicación:</span><span class="sxs-lookup"><span data-stu-id="83e73-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="83e73-126">Si el URI apunta a un recurso remoto, a continuación, automáticamente se descargan y coloca en la página principal.</span><span class="sxs-lookup"><span data-stu-id="83e73-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="83e73-127">Los recursos locales se copiará en la carpeta de datos de aplicación de la casa de realidad mixta antes de que se va a colocar en la página principal.</span><span class="sxs-lookup"><span data-stu-id="83e73-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="83e73-128">Se recomienda diseñar su experiencia a la cuenta para escenarios donde el usuario podría estar ejecutando una versión anterior de Windows que no es compatible con esta característica mediante el botón de ocultación o deshabilitación de, si es posible.</span><span class="sxs-lookup"><span data-stu-id="83e73-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="83e73-129">Invocar el *Agregar modelo protocolo* desde una aplicación de plataforma Universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="83e73-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="83e73-130">Invocar el *Agregar modelo protocolo* desde una página Web:</span><span class="sxs-lookup"><span data-stu-id="83e73-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="83e73-131">Consideraciones para inmersivos (VR)</span><span class="sxs-lookup"><span data-stu-id="83e73-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="83e73-132">Para inmersivos (VR), el Portal de realidad mixta no tiene que estar ejecutándose antes de invocar el *Agregar modelo protocolo*.</span><span class="sxs-lookup"><span data-stu-id="83e73-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="83e73-133">En este caso, el *Agregar modelo protocolo* iniciará el Portal de realidad mixta y colocar el objeto directamente donde los auriculares está buscando una vez que llegue a la realidad mixta principal.</span><span class="sxs-lookup"><span data-stu-id="83e73-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="83e73-134">Al invocar el *Agregar modelo protocolo* desde el escritorio con el Portal de realidad mixta ya está ejecutando, asegúrese de que los auriculares está "activo".</span><span class="sxs-lookup"><span data-stu-id="83e73-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="83e73-135">Si no es así, la selección de ubicación no se realizará correctamente.</span><span class="sxs-lookup"><span data-stu-id="83e73-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="83e73-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="83e73-136">See also</span></span>

* [<span data-ttu-id="83e73-137">Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="83e73-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="83e73-138">Navegar por el inicio de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="83e73-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
