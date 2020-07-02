---
title: Streaming en Unreal
description: Guía de streaming de Unreal a HoloLens 2
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, realidad mixta, streaming, PC, control remoto de aplicaciones holográficas, Holographic Remoting Player, documentación
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888916"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="a36ee-104">Streaming en Unreal</span><span class="sxs-lookup"><span data-stu-id="a36ee-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a36ee-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="a36ee-105">Overview</span></span>
<span data-ttu-id="a36ee-106">El streaming de un equipo a HoloLens ofrece dos ventajas principales:</span><span class="sxs-lookup"><span data-stu-id="a36ee-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="a36ee-107">Permite que la aplicación de realidad mixta aproveche la eficacia de cálculo de los equipos.</span><span class="sxs-lookup"><span data-stu-id="a36ee-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="a36ee-108">Ayuda a acelerar el tiempo de iteración de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="a36ee-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="a36ee-109">Para empezar, deberá descargar [Holographic Remoting Player](holographic-remoting-player.md) en su dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a36ee-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="a36ee-110">Esta descarga permitirá que la aplicación transmita directamente al reproductor de control remoto en HoloLens desde los orígenes siguientes:</span><span class="sxs-lookup"><span data-stu-id="a36ee-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="a36ee-111">Editor Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="a36ee-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="a36ee-112">Ejecutable de Windows empaquetado</span><span class="sxs-lookup"><span data-stu-id="a36ee-112">A packaged Windows executable</span></span> 

<span data-ttu-id="a36ee-113">Durante el streaming, tiene acceso prácticamente a las mismas funcionalidades de HoloLens que cuando se ejecuta una aplicación en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a36ee-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="a36ee-114">Esto incluye [seguimiento de articulación de la mano](unreal-hand-tracking.md) (si utiliza HoloLens 2), [asignación espacial](unreal-spatial-mapping.md) y [delimitadores espaciales](unreal-spatial-anchors.md), pero descarta las características de esta [lista de limitaciones](holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="a36ee-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="a36ee-115">La calidad de streaming depende en gran medida de la intensidad de la señal de su red WiFi.</span><span class="sxs-lookup"><span data-stu-id="a36ee-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>

## <a name="device-support"></a><span data-ttu-id="a36ee-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a36ee-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a36ee-117"><strong>Origen</strong></span><span class="sxs-lookup"><span data-stu-id="a36ee-117"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="a36ee-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1.ª generación</strong></a></span><span class="sxs-lookup"><span data-stu-id="a36ee-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="a36ee-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="a36ee-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="a36ee-120"><strong>Cascos envolventes</strong></span><span class="sxs-lookup"><span data-stu-id="a36ee-120"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a36ee-121">Editor de Unreal</span><span class="sxs-lookup"><span data-stu-id="a36ee-121">Unreal editor</span></span></td>
        <td><span data-ttu-id="a36ee-122">✔</span><span class="sxs-lookup"><span data-stu-id="a36ee-122">✔</span></span></td>
        <td><span data-ttu-id="a36ee-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a36ee-123">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="a36ee-124">Paquetes de Windows</span><span class="sxs-lookup"><span data-stu-id="a36ee-124">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a36ee-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a36ee-125">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="a36ee-126">Streaming desde el editor de Unreal</span><span class="sxs-lookup"><span data-stu-id="a36ee-126">Streaming from the Unreal editor</span></span>

<span data-ttu-id="a36ee-127">Como desarrollador, descubrirá que el streaming desde el editor de Unreal a su dispositivo HoloLens proporciona grandes ventajas al realizar pruebas; por ejemplo, ya no tiene que esperar a que la aplicación se compile e implemente antes de probar las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="a36ee-127">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="a36ee-128">Puede encontrar instrucciones detalladas sobre el [streaming desde el editor de Unreal](unreal-uxt-ch6.md#device-only-streaming) en la última sección de la Introducción a la serie de tutoriales de Unreal.</span><span class="sxs-lookup"><span data-stu-id="a36ee-128">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="a36ee-129">Streaming desde un ejecutable de Windows empaquetado</span><span class="sxs-lookup"><span data-stu-id="a36ee-129">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="a36ee-130">A partir de Unreal 4.25.1, puede transmitir la aplicación a un dispositivo HoloLens 2 desde un ejecutable de Windows empaquetado siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a36ee-130">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="a36ee-131">Vaya a **File > Package Project > Windows** (Archivo > Proyecto de paquete > Windows) en el menú del editor.</span><span class="sxs-lookup"><span data-stu-id="a36ee-131">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="a36ee-132">Elija una ubicación donde guardar el paquete y haga clic en **Select Folder** (Seleccionar carpeta).</span><span class="sxs-lookup"><span data-stu-id="a36ee-132">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="a36ee-133">Una vez que el paquete termine de compilarse, abra **Holographic Remoting Player** en HoloLens 2 y tome nota de la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a36ee-133">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="a36ee-134">Deje **Holographic Remoting Player** abierto y en el símbolo del sistema:</span><span class="sxs-lookup"><span data-stu-id="a36ee-134">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="a36ee-135">Invoque cd en el directorio local donde guardó el paquete.</span><span class="sxs-lookup"><span data-stu-id="a36ee-135">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="a36ee-136">Escriba el comando siguiente: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="a36ee-136">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="a36ee-137">El nombre de la aplicación en la configuración del proyecto debe usarse automáticamente para crear el paquete de Windows.</span><span class="sxs-lookup"><span data-stu-id="a36ee-137">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="a36ee-138">Si por alguna razón son diferentes, utilice el nombre del ejecutable de Windows en el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="a36ee-138">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="a36ee-139">Presione Entrar y observe que la aplicación inicia el streaming.</span><span class="sxs-lookup"><span data-stu-id="a36ee-139">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="a36ee-140">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a36ee-140">See also</span></span>
* [<span data-ttu-id="a36ee-141">Historial de versiones de Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="a36ee-141">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="a36ee-142">Escritura de una aplicación de reproductor de control remoto de holografías personalizada</span><span class="sxs-lookup"><span data-stu-id="a36ee-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a36ee-143">Establecimiento de una conexión segura con Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="a36ee-143">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
