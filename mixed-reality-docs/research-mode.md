---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens, HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507699"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="01d6d-104">Modo de investigación de HoloLens</span><span class="sxs-lookup"><span data-stu-id="01d6d-104">HoloLens Research Mode</span></span>

<span data-ttu-id="01d6d-105">El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.</span><span class="sxs-lookup"><span data-stu-id="01d6d-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="01d6d-106">El modo de investigación de HoloLens 2 conserva las capacidades de HoloLens 1, agregando acceso a secuencias adicionales:</span><span class="sxs-lookup"><span data-stu-id="01d6d-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="01d6d-107">**Cámaras de seguimiento de entornos claros visibles** : cámaras de escala de grises usadas por el sistema para el seguimiento de los cabezales y el edificio de mapas.</span><span class="sxs-lookup"><span data-stu-id="01d6d-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="01d6d-108">**Cámara de profundidad** : funciona en dos modos:</span><span class="sxs-lookup"><span data-stu-id="01d6d-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="01d6d-109">Detección de profundidad de AHAT, alta frecuencia (45 FPS) utilizada para el seguimiento manual.</span><span class="sxs-lookup"><span data-stu-id="01d6d-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="01d6d-110">De manera diferente del modo de inicio breve de la primera versión, AHAT proporciona una pseudo profundidad con ajuste de fase superior a 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="01d6d-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="01d6d-111">Detección de profundidad larga de baja frecuencia (1-5 FPS) usada por la [asignación espacial](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="01d6d-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="01d6d-112">**Dos versiones de la secuencia ir-reflectividad** : usadas por HoloLens para calcular la profundidad.</span><span class="sxs-lookup"><span data-stu-id="01d6d-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="01d6d-113">Estas imágenes se iluminan por infrarrojos y no se ven afectadas por la luz visible de ambiente.</span><span class="sxs-lookup"><span data-stu-id="01d6d-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="01d6d-114">Si usa HoloLens 2 también tiene acceso a las entradas adicionales siguientes:</span><span class="sxs-lookup"><span data-stu-id="01d6d-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="01d6d-115">**Acelerómetro** : lo usa el sistema para determinar la aceleración lineal a lo largo de los ejes X, y y Z y la gravedad.</span><span class="sxs-lookup"><span data-stu-id="01d6d-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="01d6d-116">**Gyro** : el sistema lo usa para determinar los giros.</span><span class="sxs-lookup"><span data-stu-id="01d6d-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="01d6d-117">**Magnetómetro** : lo usa el sistema para calcular la orientación absoluta.</span><span class="sxs-lookup"><span data-stu-id="01d6d-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01d6d-118">El modo de investigación está actualmente en versión preliminar pública.</span><span class="sxs-lookup"><span data-stu-id="01d6d-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="01d6d-119">Los ejemplos de HoloLens 2, los tutoriales y la documentación completa de la API estarán disponibles en [ECCV 2020](https://eccv2020.eu/
 ) en el repositorio de Git del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="01d6d-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="01d6d-120">![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="01d6d-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="01d6d-121">*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*</span><span class="sxs-lookup"><span data-stu-id="01d6d-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="01d6d-122">Uso</span><span class="sxs-lookup"><span data-stu-id="01d6d-122">Usage</span></span>

<span data-ttu-id="01d6d-123">El modo de investigación está diseñado para investigadores académicos e industriales que exploran ideas nuevas en los campos de Computer Vision y robótica.</span><span class="sxs-lookup"><span data-stu-id="01d6d-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="01d6d-124">No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través del Microsoft Store u otros canales de distribución.</span><span class="sxs-lookup"><span data-stu-id="01d6d-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="01d6d-125">Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se admitirán en futuras actualizaciones de hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="01d6d-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="01d6d-126">Sin embargo, esto no debería impedir su uso para desarrollar y probar nuevas ideas.</span><span class="sxs-lookup"><span data-stu-id="01d6d-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="01d6d-127">Seguridad y rendimiento</span><span class="sxs-lookup"><span data-stu-id="01d6d-127">Security and performance</span></span>

<span data-ttu-id="01d6d-128">Tenga en cuenta que la habilitación del modo de investigación usa más energía de la batería que el uso de HoloLens 2 en condiciones normales.</span><span class="sxs-lookup"><span data-stu-id="01d6d-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="01d6d-129">Esto es así incluso si la aplicación que usa las características de modo de investigación no se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="01d6d-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="01d6d-130">Habilitar este modo también puede reducir la seguridad general del dispositivo, ya que las aplicaciones pueden hacer uso indebido de los datos del sensor.</span><span class="sxs-lookup"><span data-stu-id="01d6d-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="01d6d-131">Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes sobre seguridad de HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="01d6d-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="01d6d-132">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="01d6d-132">Device support</span></span>
<table><span data-ttu-id="01d6d-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="01d6d-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="01d6d-134"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="01d6d-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="01d6d-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1.ª generación</strong></a></span><span class="sxs-lookup"><span data-stu-id="01d6d-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="01d6d-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="01d6d-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="01d6d-137">Cámaras de seguimiento de cabezales</span><span class="sxs-lookup"><span data-stu-id="01d6d-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="01d6d-138">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-138">✔️</span></span></td>
        <td><span data-ttu-id="01d6d-139">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="01d6d-140">Profundidad & cámara de INFRARROJOs</span><span class="sxs-lookup"><span data-stu-id="01d6d-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="01d6d-141">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-141">✔️</span></span></td>
        <td><span data-ttu-id="01d6d-142">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="01d6d-143">Acelerómetro</span><span class="sxs-lookup"><span data-stu-id="01d6d-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="01d6d-144">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="01d6d-145">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="01d6d-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="01d6d-146">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="01d6d-147">Magnetómetro</span><span class="sxs-lookup"><span data-stu-id="01d6d-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="01d6d-148">✔️</span><span class="sxs-lookup"><span data-stu-id="01d6d-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="01d6d-149">Habilitación del modo de investigación (HoloLens de la primera generación y HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="01d6d-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="01d6d-150">El modo de investigación es una extensión del modo de programador.</span><span class="sxs-lookup"><span data-stu-id="01d6d-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="01d6d-151">Antes de comenzar, las características del desarrollador del dispositivo deben estar habilitadas para tener acceso a la configuración del modo de investigación:</span><span class="sxs-lookup"><span data-stu-id="01d6d-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="01d6d-152">Abra el **menú inicio > configuración** y seleccione **actualizaciones**.</span><span class="sxs-lookup"><span data-stu-id="01d6d-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="01d6d-153">Seleccione **para desarrolladores** y habilite el **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="01d6d-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="01d6d-154">Desplázate hacia abajo y habilita **Portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="01d6d-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="01d6d-155">Una vez habilitadas las características de desarrollador, [Conéctese al portal de dispositivos](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación:</span><span class="sxs-lookup"><span data-stu-id="01d6d-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="01d6d-156">Vaya al **modo System > Research** en el **portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="01d6d-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="01d6d-157">Seleccione **permitir el acceso a la secuencia del sensor**.</span><span class="sxs-lookup"><span data-stu-id="01d6d-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="01d6d-158">Reinicie el dispositivo desde el elemento de menú de **energía** en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="01d6d-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="01d6d-159">Una vez que haya reiniciado el dispositivo, las aplicaciones que se cargan a través del **portal de dispositivos** pueden acceder a los flujos del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="01d6d-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="01d6d-160">![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="01d6d-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="01d6d-161">*Ventana del modo de investigación en el portal de dispositivos de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="01d6d-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01d6d-162">El modo de investigación de HoloLens 2 está disponible a partir de la compilación 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="01d6d-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="01d6d-163">Si necesita tener acceso en una compilación anterior, Regístrese en el programa de [versión preliminar de Insider](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="01d6d-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="01d6d-164">Uso de datos de sensor en las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="01d6d-164">Using sensor data in your apps</span></span>

<span data-ttu-id="01d6d-165">Las aplicaciones pueden tener acceso a los datos de la secuencia del sensor de la misma manera que se obtiene acceso a los flujos de cámara de fotos y vídeo a través de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="01d6d-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="01d6d-166">Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="01d6d-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="01d6d-167">En concreto, la aplicación sabe exactamente dónde se encuentra HoloLens en el espacio 6DoF en cada tiempo de captura de fotogramas del sensor.</span><span class="sxs-lookup"><span data-stu-id="01d6d-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="01d6d-168">Puede encontrar aplicaciones de ejemplo sobre cómo obtener acceso a las diversas secuencias del modo de investigación, cómo usar las [funciones intrínsecas y extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), y cómo grabar secuencias en el repositorio de [repositorios de github de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="01d6d-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="01d6d-169">En este momento, el ejemplo HoloLensForCV no funciona en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="01d6d-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="01d6d-170">Soporte técnico</span><span class="sxs-lookup"><span data-stu-id="01d6d-170">Support</span></span>

<span data-ttu-id="01d6d-171">Use el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.</span><span class="sxs-lookup"><span data-stu-id="01d6d-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="01d6d-172">Consulta también</span><span class="sxs-lookup"><span data-stu-id="01d6d-172">See also</span></span>

* [<span data-ttu-id="01d6d-173">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="01d6d-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="01d6d-174">Repositorio de GitHub de HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="01d6d-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="01d6d-175">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="01d6d-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
