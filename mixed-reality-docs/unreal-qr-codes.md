---
title: Códigos QR en Unreal
description: Guía para el uso de códigos QR en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376107"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="1ed90-104">Códigos QR en Unreal</span><span class="sxs-lookup"><span data-stu-id="1ed90-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="1ed90-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="1ed90-105">Overview</span></span>

<span data-ttu-id="1ed90-106">HoloLens 2 puede ver los códigos QR en el espacio del mundo real a través de la cámara web, que los representa como hologramas empleando un sistema de coordenadas en la posición del mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="1ed90-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="1ed90-107">Además de los códigos QR únicos, HoloLens 2 también puede representar hologramas en la misma ubicación en varios dispositivos para crear una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="1ed90-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="1ed90-108">Asegúrese de seguir estos procedimientos recomendados para agregar códigos QR a las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="1ed90-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="1ed90-109">Zonas tranquilas</span><span class="sxs-lookup"><span data-stu-id="1ed90-109">Quiet zones</span></span>
- <span data-ttu-id="1ed90-110">Iluminación y fondo</span><span class="sxs-lookup"><span data-stu-id="1ed90-110">Lighting and backdrop</span></span>
- <span data-ttu-id="1ed90-111">Tamaño, distancia y posición angular</span><span class="sxs-lookup"><span data-stu-id="1ed90-111">Size, distance, and angular position</span></span>

<span data-ttu-id="1ed90-112">Preste especial atención a las [consideraciones del ambiente](environment-considerations-for-hololens.md) al colocar códigos QR en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1ed90-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="1ed90-113">Puede encontrar más información sobre cada uno de estos temas e instrucciones sobre cómo descargar el paquete de NuGet necesario en el documento principal de [seguimiento de código QR](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="1ed90-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="1ed90-114">Habilitación de la detección de QR</span><span class="sxs-lookup"><span data-stu-id="1ed90-114">Enabling QR detection</span></span>
<span data-ttu-id="1ed90-115">Como HoloLens 2 necesita usar la cámara web para ver los códigos QR, deberá habilitarla en la configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="1ed90-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="1ed90-116">Abra **Editar > Configuración del proyecto**, desplácese hasta la sección **Plataformas** y pulse en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="1ed90-117">Expanda la sección **Funcionalidades** y marque **Cámara web**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="1ed90-118">También deberá participar en el seguimiento del código QR mediante la [adición de un activo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="1ed90-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="1ed90-119">Justo antes del uso, debe habilitar manualmente el seguimiento llamando a `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span><span class="sxs-lookup"><span data-stu-id="1ed90-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span></span> <span data-ttu-id="1ed90-120">Después de terminar el seguimiento del código QR, debe deshabilitarlo mediante `UHoloLensARFunctionLibrary::StopCameraCapture()` para guardar los recursos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1ed90-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span> 

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="1ed90-121">Configuración de una imagen con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1ed90-121">Setting up a tracked image</span></span>

<span data-ttu-id="1ed90-122">Los códigos QR aparecen en el sistema de geometría con seguimiento de AR de Unreal como una imagen con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="1ed90-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="1ed90-123">Para que esto funcione, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1ed90-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="1ed90-124">Cree un plano técnico y agregue un componente **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="1ed90-126">Seleccione **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="1ed90-128">Haga clic en **+** junto a **On Add Tracked Geometry** (Al agregar geometría con seguimiento) para agregar el nodo al gráfico de eventos.</span><span class="sxs-lookup"><span data-stu-id="1ed90-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="1ed90-129">Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="1ed90-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Ejemplo de representación de QR](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="1ed90-131">Uso de una imagen con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1ed90-131">Using a tracked image</span></span>
<span data-ttu-id="1ed90-132">El gráfico de eventos de la siguiente imagen muestra el evento **OnUpdateTrackedImage** que se usa para representar un punto en el centro de un código QR e imprimir sus datos.</span><span class="sxs-lookup"><span data-stu-id="1ed90-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Ejemplo de representación de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="1ed90-134">Esto es lo que sucede:</span><span class="sxs-lookup"><span data-stu-id="1ed90-134">Here's what's going on:</span></span>
1. <span data-ttu-id="1ed90-135">En primer lugar, convierte la imagen con seguimiento en un elemento **ARTrackedQRCode** para comprobar que la imagen actualizada actual es un código QR.</span><span class="sxs-lookup"><span data-stu-id="1ed90-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="1ed90-136">Los datos codificados se recuperan de la variable **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="1ed90-137">Puede obtener la parte superior izquierda del código QR en la ubicación de **GetLocalToWorldTransform** y las dimensiones con **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="1ed90-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="1ed90-138">También puede [obtener el sistema de coordenadas para un código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) en el código.</span><span class="sxs-lookup"><span data-stu-id="1ed90-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="1ed90-139">Búsqueda del identificador único</span><span class="sxs-lookup"><span data-stu-id="1ed90-139">Finding the unique ID</span></span>
<span data-ttu-id="1ed90-140">Cada código QR tiene un id. de GUID único, que puede buscar:</span><span class="sxs-lookup"><span data-stu-id="1ed90-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="1ed90-141">Arrastrando y colocando el marcador **As ARTracked QRCode** (Como QRCode ARTracked) y buscando **Get Unique ID** (Obtener id. único).</span><span class="sxs-lookup"><span data-stu-id="1ed90-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="1ed90-143">Ocurren muchas cosas en segundo plano con los códigos QR, por lo que esto no es todo.</span><span class="sxs-lookup"><span data-stu-id="1ed90-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="1ed90-144">Asegúrese de consultar los siguientes vínculos para obtener más detalles sobre ellos.</span><span class="sxs-lookup"><span data-stu-id="1ed90-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ed90-145">Consulta también</span><span class="sxs-lookup"><span data-stu-id="1ed90-145">See also</span></span>
* [<span data-ttu-id="1ed90-146">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1ed90-146">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="1ed90-147">Hologramas</span><span class="sxs-lookup"><span data-stu-id="1ed90-147">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="1ed90-148">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="1ed90-148">Coordinate systems</span></span>](coordinate-systems.md)
