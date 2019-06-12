---
title: Modo de investigación de HoloLens
description: Utiliza el modo de investigación en HoloLens, una aplicación puede tener acceso a secuencias de sensor de clave de dispositivo (profundidad, el entorno de seguimiento y reflexión de infrarrojos).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, cv, rs4, visión de equipo, la investigación, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829934"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="1fcc5-104">Modo de investigación de HoloLens</span><span class="sxs-lookup"><span data-stu-id="1fcc5-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="1fcc5-105">Esta característica se agregó como parte de la [Windows 10 de abril de 2018 Update](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="1fcc5-106">Modo de investigación es una nueva funcionalidad de HoloLens que proporciona acceso a las aplicaciones a los sensores de clave en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="1fcc5-107">Entre ellos se incluyen los siguientes:</span><span class="sxs-lookup"><span data-stu-id="1fcc5-107">These include:</span></span>
- <span data-ttu-id="1fcc5-108">Los cuatro cámaras utilizadas por el sistema para la compilación de mapa y seguimiento principal de seguimiento del entorno.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="1fcc5-109">Dos versiones de los datos de cámara de profundidad, uno para la alta frecuencia (30 FPS) cerca de la profundidad de detección usados en la mano de seguimiento y otro para frecuencia inferior (1 FPS) lejano profundidad detección, se usan actualmente mediante la asignación espacial,</span><span class="sxs-lookup"><span data-stu-id="1fcc5-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="1fcc5-110">Dos versiones de un flujo de reflexión de infrarrojos, usada por el HoloLens para calcular la profundidad, pero valioso en sí misma como estas imágenes son iluminada desde el HoloLens y razonablemente se ven afectados por esta luz ambiente.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="1fcc5-111">![Captura de pantalla de aplicación de modo de investigación](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="1fcc5-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="1fcc5-112">*Una captura de realidad mixta de una aplicación de prueba que muestra las secuencias de ocho sensores disponibles en el modo de investigación*</span><span class="sxs-lookup"><span data-stu-id="1fcc5-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="1fcc5-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1fcc5-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1fcc5-114"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="1fcc5-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1fcc5-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1fcc5-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1fcc5-116"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="1fcc5-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1fcc5-117">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="1fcc5-117">Research mode</span></span></td>
        <td><span data-ttu-id="1fcc5-118">✔️</span><span class="sxs-lookup"><span data-stu-id="1fcc5-118">✔️</span></span></td>
        <td><span data-ttu-id="1fcc5-119">❌</span><span class="sxs-lookup"><span data-stu-id="1fcc5-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="1fcc5-120">Antes de usar el modo de investigación</span><span class="sxs-lookup"><span data-stu-id="1fcc5-120">Before using Research mode</span></span>

<span data-ttu-id="1fcc5-121">También se denomina modo de investigación: está destinado a los investigadores industriales y académicos probando nuevas ideas en los campos de Computer Vision y robótica.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="1fcc5-122">Modo de investigación no está diseñado para aplicaciones que se implementará en una empresa o están disponibles en la Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="1fcc5-123">La razón de esto es que el modo de investigación reduce la seguridad del dispositivo y consume mucho más energía de batería que el funcionamiento normal.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="1fcc5-124">Microsoft no está confirmando que admiten este modo en todos los futuros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="1fcc5-125">Por lo tanto, se recomienda que usarla para desarrollar y probar nuevas ideas; Sin embargo, no podrá implementar ampliamente las aplicaciones que utiliza el modo de investigación o tienen cualquier garantía de que seguirán funcionando en hardware en el futuro.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="1fcc5-126">Habilitar el modo de investigación</span><span class="sxs-lookup"><span data-stu-id="1fcc5-126">Enabling Research mode</span></span>

<span data-ttu-id="1fcc5-127">Modo de investigación es un secundario del modo de programador.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="1fcc5-128">Primero debe habilitar el modo de desarrollador en la aplicación de configuración (**configuración > actualización y seguridad > para los desarrolladores**):</span><span class="sxs-lookup"><span data-stu-id="1fcc5-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="1fcc5-129">Establezca "Usar características del desarrollador" en **en**</span><span class="sxs-lookup"><span data-stu-id="1fcc5-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="1fcc5-130">Establece la opción "Habilitar el Portal del dispositivo" en **en**</span><span class="sxs-lookup"><span data-stu-id="1fcc5-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="1fcc5-131">A continuación, mediante un explorador web que está conectado a la misma red Wi-Fi como su HoloLens, vaya a la dirección IP de su HoloLens (obtenido a través de **configuración > red e Internet > Wi-Fi > Propiedades de Hardware**).</span><span class="sxs-lookup"><span data-stu-id="1fcc5-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="1fcc5-132">Se trata de la [Device Portal](using-the-windows-device-portal.md), y encontrará una página de "Modo de investigación" en la sección "Sistema" del portal:</span><span class="sxs-lookup"><span data-stu-id="1fcc5-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="1fcc5-133">![Ficha de modo de investigación del Portal de dispositivo HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="1fcc5-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="1fcc5-134">*Modo de investigación en el Portal de dispositivo HoloLens*</span><span class="sxs-lookup"><span data-stu-id="1fcc5-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="1fcc5-135">Después de seleccionar **permitir el acceso a secuencias de sensor**, tendrá que reiniciar HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="1fcc5-136">Puede hacerlo desde el Portal de dispositivo, en el elemento de menú "Power" en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="1fcc5-137">Una vez que se ha reiniciado el dispositivo, las aplicaciones que se han cargado a través del Portal de dispositivos deben ser capaz de obtener acceso a secuencias de modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="1fcc5-138">Uso de datos del sensor en las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="1fcc5-138">Using sensor data in your apps</span></span>

<span data-ttu-id="1fcc5-139">Las aplicaciones pueden tener acceso a datos del sensor de la secuencia abriendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) secuencias de exactamente la misma manera que acceden a la secuencia de la cámara de fotografías y vídeo.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="1fcc5-140">Todas las API que funcionan para el desarrollo de HoloLens también están disponibles en el modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="1fcc5-141">En concreto, la aplicación puede saber exactamente donde HoloLens de 6GDL espacio en cada momento de captura de fotogramas del sensor.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="1fcc5-142">Aplicaciones de ejemplo que muestra cómo tener acceso a los distintos flujos de modo Research, cómo usar las funciones intrínsecas y extrinsics y cómo grabar secuencias están disponibles en el [repositorio de HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="1fcc5-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="1fcc5-143">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="1fcc5-143">Known issues</span></span>

<span data-ttu-id="1fcc5-144">Consulte la [issue tracker de](https://github.com/Microsoft/HololensForCV/issues) en el repositorio HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="1fcc5-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fcc5-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="1fcc5-145">See also</span></span>

* [<span data-ttu-id="1fcc5-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="1fcc5-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="1fcc5-147">Repositorio de HoloLensForCV GitHub</span><span class="sxs-lookup"><span data-stu-id="1fcc5-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="1fcc5-148">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="1fcc5-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
