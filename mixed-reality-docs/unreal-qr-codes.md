---
title: Códigos QR en Unreal
description: Guía para el uso de códigos QR en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342663"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="f6e81-104">Códigos QR en Unreal</span><span class="sxs-lookup"><span data-stu-id="f6e81-104">QR codes in Unreal</span></span>

<span data-ttu-id="f6e81-105">HoloLens puede colocar códigos QR en un área del mundo para representar hologramas en posiciones conocidas del mundo real.</span><span class="sxs-lookup"><span data-stu-id="f6e81-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="f6e81-106">También se puede usar para representar hologramas en varios dispositivos en la misma ubicación para crear una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="f6e81-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="f6e81-107">Para habilitar la detección de QR en HoloLens, asegúrate de que la funcionalidad "Webcam" esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades).</span><span class="sxs-lookup"><span data-stu-id="f6e81-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="f6e81-108">Para participar en el seguimiento de códigos QR en Unreal, inicia una sesión ARSession mediante la función StartARSession.</span><span class="sxs-lookup"><span data-stu-id="f6e81-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="f6e81-109">Los códigos QR se muestran en el sistema de geometría supervisado de AR de Unreal como imagen con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="f6e81-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="f6e81-110">Para usar esta característica, agrega un componente AR Trackable Notify (Notificación de seguimiento de AR) a un actor de Blueprint:</span><span class="sxs-lookup"><span data-stu-id="f6e81-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="f6e81-112">A continuación, ve a los detalles del componente y haz clic en el botón verde "+" de los eventos que se van a supervisar.</span><span class="sxs-lookup"><span data-stu-id="f6e81-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="f6e81-114">Aquí, nos hemos suscrito a OnUpdateTrackedImage para representar un punto en el centro de un código QR e imprimir los datos codificados del código QR.</span><span class="sxs-lookup"><span data-stu-id="f6e81-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![Ejemplo de representación de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="f6e81-116">En primer lugar, convierte la imagen de la que se realiza el seguimiento en ARTrackedQRCode para comprobar que la imagen actualizada actual es un código QR.</span><span class="sxs-lookup"><span data-stu-id="f6e81-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="f6e81-117">Después, los datos codificados se pueden recuperar con la variable QRCode.</span><span class="sxs-lookup"><span data-stu-id="f6e81-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="f6e81-118">La parte superior izquierda del código QR se puede recuperar desde la ubicación de GetLocalToWorldTransform.</span><span class="sxs-lookup"><span data-stu-id="f6e81-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="f6e81-119">Las dimensiones se pueden recuperar con GetEstimateSize.</span><span class="sxs-lookup"><span data-stu-id="f6e81-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="f6e81-120">Cada código QR también tiene un identificador GUID único:</span><span class="sxs-lookup"><span data-stu-id="f6e81-120">Every QR code also has a unique guid ID:</span></span> 

![GUID de QR](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="f6e81-122">Consulta también</span><span class="sxs-lookup"><span data-stu-id="f6e81-122">See also</span></span>
* [<span data-ttu-id="f6e81-123">Seguimiento de códigos QR</span><span class="sxs-lookup"><span data-stu-id="f6e81-123">QR code tracking</span></span>](qr-code-tracking.md)
