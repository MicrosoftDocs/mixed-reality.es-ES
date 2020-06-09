---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533107"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="1d63a-104">Modo de investigación de HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d63a-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="1d63a-105">Información general</span><span class="sxs-lookup"><span data-stu-id="1d63a-105">Overview</span></span>

<span data-ttu-id="1d63a-106">El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.</span><span class="sxs-lookup"><span data-stu-id="1d63a-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="1d63a-107">Ahora puede recopilar datos de las siguientes entradas:</span><span class="sxs-lookup"><span data-stu-id="1d63a-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="1d63a-108">**Cámaras de seguimiento de entornos claros visibles** : utilizadas por el sistema para el seguimiento de los cabezales y el edificio de mapas.</span><span class="sxs-lookup"><span data-stu-id="1d63a-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="1d63a-109">**Cámara de profundidad** : funciona en dos modos:</span><span class="sxs-lookup"><span data-stu-id="1d63a-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="1d63a-110">Detección de breves y de alta frecuencia (30 FPS) de profundidad usada para el [seguimiento manual](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="1d63a-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="1d63a-111">Detección de profundidad larga de baja frecuencia (1-5 FPS) usada por la [asignación espacial](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="1d63a-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="1d63a-112">**Dos versiones de la secuencia ir-reflectividad** : usadas por HoloLens para calcular la profundidad.</span><span class="sxs-lookup"><span data-stu-id="1d63a-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="1d63a-113">Estas imágenes se iluminan por infrarrojos y no se ven afectadas por la luz visible de ambiente.</span><span class="sxs-lookup"><span data-stu-id="1d63a-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="1d63a-114">Si usa una HoloLens 2, también podrá acceder a las siguientes entradas:</span><span class="sxs-lookup"><span data-stu-id="1d63a-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="1d63a-115">**Acelerómetro** : lo usa el sistema para determinar la aceleración lineal a lo largo de los ejes X, y y Z y la gravedad.</span><span class="sxs-lookup"><span data-stu-id="1d63a-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="1d63a-116">**Gyro** : el sistema lo usa para determinar los giros.</span><span class="sxs-lookup"><span data-stu-id="1d63a-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="1d63a-117">**Magnetómetro** : lo usa el sistema para calcular la orientación absoluta.</span><span class="sxs-lookup"><span data-stu-id="1d63a-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="1d63a-118">![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d63a-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="1d63a-119">*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*</span><span class="sxs-lookup"><span data-stu-id="1d63a-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="1d63a-120">La característica de modo de investigación se ha agregado como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="1d63a-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="1d63a-121">Uso</span><span class="sxs-lookup"><span data-stu-id="1d63a-121">Usage</span></span>

<span data-ttu-id="1d63a-122">El modo de investigación está diseñado para investigadores académicos e industriales que exploran ideas nuevas en los campos de Computer Vision y robótica.</span><span class="sxs-lookup"><span data-stu-id="1d63a-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="1d63a-123">No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través del Microsoft Store u otros canales de distribución.</span><span class="sxs-lookup"><span data-stu-id="1d63a-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="1d63a-124">Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se admitirán en futuras actualizaciones de hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="1d63a-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="1d63a-125">Sin embargo, esto no debería impedir su uso para desarrollar y probar nuevas ideas.</span><span class="sxs-lookup"><span data-stu-id="1d63a-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="1d63a-126">Seguridad y rendimiento</span><span class="sxs-lookup"><span data-stu-id="1d63a-126">Security and performance</span></span>

<span data-ttu-id="1d63a-127">Tenga en cuenta que la habilitación del modo de investigación usa más energía de la batería que el uso de HoloLens 2 en condiciones normales.</span><span class="sxs-lookup"><span data-stu-id="1d63a-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="1d63a-128">Esto es así incluso si la aplicación que usa las características de modo de investigación no se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="1d63a-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="1d63a-129">Habilitar este modo también puede reducir la seguridad general del dispositivo, ya que las aplicaciones pueden hacer uso indebido de los datos del sensor.</span><span class="sxs-lookup"><span data-stu-id="1d63a-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="1d63a-130">Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes sobre seguridad de HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="1d63a-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="1d63a-131">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1d63a-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="1d63a-132"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="1d63a-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1d63a-133"><a href="hololens-hardware-details.md"><strong>La primera generación de HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1d63a-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="1d63a-134">Cámaras de seguimiento de cabezales</span><span class="sxs-lookup"><span data-stu-id="1d63a-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="1d63a-135">✔️</span><span class="sxs-lookup"><span data-stu-id="1d63a-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1d63a-136">Profundidad & cámara de INFRARROJOs</span><span class="sxs-lookup"><span data-stu-id="1d63a-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="1d63a-137">✔️</span><span class="sxs-lookup"><span data-stu-id="1d63a-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1d63a-138">Acelerómetro</span><span class="sxs-lookup"><span data-stu-id="1d63a-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1d63a-139">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="1d63a-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1d63a-140">Magnetómetro</span><span class="sxs-lookup"><span data-stu-id="1d63a-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="1d63a-141">Se espera que la compatibilidad con el modo de investigación de HoloLens 2 esté disponible en versión preliminar pública en julio de 2020 y incluirá todas las características indicadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d63a-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="1d63a-142">Vuelva a consultar para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="1d63a-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="1d63a-143">Habilitar el modo de investigación</span><span class="sxs-lookup"><span data-stu-id="1d63a-143">Enabling Research mode</span></span>

<span data-ttu-id="1d63a-144">El modo de investigación es una extensión del modo de programador.</span><span class="sxs-lookup"><span data-stu-id="1d63a-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="1d63a-145">Antes de comenzar, las características del desarrollador del dispositivo deben estar habilitadas para tener acceso a la configuración del modo de investigación:</span><span class="sxs-lookup"><span data-stu-id="1d63a-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="1d63a-146">Abra el **menú inicio > configuración** y seleccione **actualizaciones**.</span><span class="sxs-lookup"><span data-stu-id="1d63a-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="1d63a-147">Seleccione **para desarrolladores** y habilite el **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="1d63a-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="1d63a-148">Desplácese hacia abajo y habilite el **portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="1d63a-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="1d63a-149">Una vez habilitadas las características de desarrollador, [Conéctese al portal de dispositivos](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="1d63a-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="1d63a-150">En la *primera generación de HoloLens*:</span><span class="sxs-lookup"><span data-stu-id="1d63a-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="1d63a-151">Vaya al **modo System > Research** en el **portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="1d63a-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="1d63a-152">Seleccione **permitir el acceso a la secuencia del sensor**.</span><span class="sxs-lookup"><span data-stu-id="1d63a-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="1d63a-153">Reinicie el dispositivo desde el elemento de menú de **energía** en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="1d63a-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="1d63a-154">Una vez que haya reiniciado el dispositivo, las aplicaciones que se cargan a través del **portal de dispositivos** pueden acceder a los flujos del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="1d63a-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="1d63a-155">![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="1d63a-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="1d63a-156">*Ventana del modo de investigación en el portal de dispositivos de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="1d63a-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="1d63a-157">Uso de datos de sensor en las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="1d63a-157">Using sensor data in your apps</span></span>

<span data-ttu-id="1d63a-158">*La primera generación de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="1d63a-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="1d63a-159">Las aplicaciones pueden tener acceso a los datos de la secuencia del sensor de la misma manera que se obtiene acceso a los flujos de cámara de fotos y vídeo a través de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="1d63a-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="1d63a-160">Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="1d63a-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="1d63a-161">En concreto, la aplicación sabe exactamente dónde se encuentra HoloLens en el espacio 6DoF en cada tiempo de captura de fotogramas del sensor.</span><span class="sxs-lookup"><span data-stu-id="1d63a-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="1d63a-162">Puede encontrar aplicaciones de ejemplo sobre cómo obtener acceso a las diversas secuencias del modo de investigación, cómo usar las [funciones intrínsecas y extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), y cómo grabar secuencias en el repositorio de [repositorios de github de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="1d63a-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="1d63a-163">En este momento, el ejemplo HoloLensForCV no funciona en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d63a-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="1d63a-164">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="1d63a-164">Known issues</span></span>

<span data-ttu-id="1d63a-165">Puede usar el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV para seguir los problemas conocidos.</span><span class="sxs-lookup"><span data-stu-id="1d63a-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d63a-166">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="1d63a-166">See also</span></span>

* [<span data-ttu-id="1d63a-167">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="1d63a-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="1d63a-168">Repositorio de GitHub de HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="1d63a-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="1d63a-169">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="1d63a-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
