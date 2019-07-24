---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829934"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="fcab3-104">Modo de investigación de HoloLens</span><span class="sxs-lookup"><span data-stu-id="fcab3-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="fcab3-105">Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="fcab3-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="fcab3-106">El modo de investigación es una nueva funcionalidad de HoloLens que proporciona acceso a las aplicaciones a los sensores de claves en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fcab3-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="fcab3-107">Entre ellas se incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="fcab3-107">These include:</span></span>
- <span data-ttu-id="fcab3-108">Las cuatro cámaras de seguimiento del entorno utilizadas por el sistema para la creación de mapas y el seguimiento de encabezados.</span><span class="sxs-lookup"><span data-stu-id="fcab3-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="fcab3-109">Dos versiones de los datos de la cámara de profundidad: una para la detección en profundidad de alta frecuencia (30 FPS), que se usa habitualmente en el seguimiento de la mano, y la otra para la detección de la profundidad de baja frecuencia (1 FPS), usada actualmente por la asignación espacial,</span><span class="sxs-lookup"><span data-stu-id="fcab3-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="fcab3-110">Dos versiones de una secuencia de reflexión de INFRARROJOs, que usa HoloLens para calcular la profundidad, pero valiosa en su propio derecho, ya que estas imágenes se iluminan desde HoloLens y razonablemente no se ven afectadas por la luz ambiente.</span><span class="sxs-lookup"><span data-stu-id="fcab3-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="fcab3-111">![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="fcab3-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="fcab3-112">*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*</span><span class="sxs-lookup"><span data-stu-id="fcab3-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="fcab3-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="fcab3-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcab3-114"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="fcab3-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="fcab3-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcab3-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcab3-116"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcab3-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcab3-117">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="fcab3-117">Research mode</span></span></td>
        <td><span data-ttu-id="fcab3-118">✔️</span><span class="sxs-lookup"><span data-stu-id="fcab3-118">✔️</span></span></td>
        <td><span data-ttu-id="fcab3-119">❌</span><span class="sxs-lookup"><span data-stu-id="fcab3-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="fcab3-120">Antes de usar el modo de investigación</span><span class="sxs-lookup"><span data-stu-id="fcab3-120">Before using Research mode</span></span>

<span data-ttu-id="fcab3-121">El modo de investigación está bien denominado: está pensado para los investigadores académicos e industriales que prueban nuevas ideas en los campos de Computer Vision y robótica.</span><span class="sxs-lookup"><span data-stu-id="fcab3-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="fcab3-122">El modo de investigación no está pensado para las aplicaciones que se implementarán en una empresa o que estarán disponibles en el Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="fcab3-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="fcab3-123">El motivo es que el modo de investigación reduce la seguridad del dispositivo y consume mucha más energía de la batería que el funcionamiento normal.</span><span class="sxs-lookup"><span data-stu-id="fcab3-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="fcab3-124">Microsoft no se compromete a admitir este modo en ningún dispositivo futuro.</span><span class="sxs-lookup"><span data-stu-id="fcab3-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="fcab3-125">Por lo tanto, se recomienda utilizarlo para desarrollar y probar nuevas ideas; sin embargo, no podrá implementar ampliamente aplicaciones que usen el modo de investigación ni tener ninguna garantía de que seguirá funcionando en hardware futuro.</span><span class="sxs-lookup"><span data-stu-id="fcab3-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="fcab3-126">Habilitar el modo de investigación</span><span class="sxs-lookup"><span data-stu-id="fcab3-126">Enabling Research mode</span></span>

<span data-ttu-id="fcab3-127">El modo de investigación es un submodo de modo de programador.</span><span class="sxs-lookup"><span data-stu-id="fcab3-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="fcab3-128">En primer lugar, debe habilitar el modo de Desarrollador en la aplicación de configuración (**configuración > actualizar & > de seguridad para desarrolladores**):</span><span class="sxs-lookup"><span data-stu-id="fcab3-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="fcab3-129">Establezca "usar características para desarrolladores" **en activado** .</span><span class="sxs-lookup"><span data-stu-id="fcab3-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="fcab3-130">Establezca "habilitar portal de dispositivos" **en activado** .</span><span class="sxs-lookup"><span data-stu-id="fcab3-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="fcab3-131">A continuación, use un explorador Web que esté conectado a la misma red Wi-Fi que HoloLens, vaya a la dirección IP de HoloLens (obtenida a través de la **configuración > red & las propiedades de hardware de Internet > Wi-Fi >** ).</span><span class="sxs-lookup"><span data-stu-id="fcab3-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="fcab3-132">Este es el [portal de dispositivos](using-the-windows-device-portal.md)y encontrará una página "modo de investigación" en la sección "sistema" del portal:</span><span class="sxs-lookup"><span data-stu-id="fcab3-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="fcab3-133">![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="fcab3-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="fcab3-134">*Modo de investigación en el portal de dispositivos de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="fcab3-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="fcab3-135">Después de seleccionar **permitir el acceso a las secuencias del sensor**, deberá reiniciar HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fcab3-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="fcab3-136">Puede hacerlo desde el portal de dispositivos, en el elemento de menú "energía" en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="fcab3-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="fcab3-137">Una vez que se ha reiniciado el dispositivo, las aplicaciones que se han cargado a través del portal de dispositivos deben poder acceder a los flujos del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="fcab3-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="fcab3-138">Uso de datos de sensor en las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="fcab3-138">Using sensor data in your apps</span></span>

<span data-ttu-id="fcab3-139">Las aplicaciones pueden acceder a los datos de la secuencia del sensor abriendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) secuencias exactamente del mismo modo en que acceden a la secuencia de la cámara de fotos o vídeos.</span><span class="sxs-lookup"><span data-stu-id="fcab3-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="fcab3-140">Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="fcab3-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="fcab3-141">En concreto, la aplicación puede saber con exactitud si HoloLens está en el espacio de 6DoF en cada tiempo de captura de fotogramas del sensor.</span><span class="sxs-lookup"><span data-stu-id="fcab3-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="fcab3-142">Las aplicaciones de ejemplo que muestran cómo se obtiene acceso a los distintos flujos del modo de investigación, cómo usar intrínsecos y extrinsics y cómo grabar flujos están disponibles en el [repositorio de github de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="fcab3-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="fcab3-143">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="fcab3-143">Known issues</span></span>

<span data-ttu-id="fcab3-144">Vea el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="fcab3-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcab3-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="fcab3-145">See also</span></span>

* [<span data-ttu-id="fcab3-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="fcab3-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="fcab3-147">Repositorio de GitHub de HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="fcab3-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="fcab3-148">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="fcab3-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
