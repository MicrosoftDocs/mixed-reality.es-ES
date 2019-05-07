---
title: Entrada MR 210 - mirada
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de mirada conceptos de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, mirada tutorial, academy,
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993551"
---
>[!NOTE]
><span data-ttu-id="c65be-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="c65be-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c65be-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c65be-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c65be-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="c65be-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c65be-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="c65be-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c65be-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c65be-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c65be-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="c65be-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="c65be-110">Entrada MR 210: Mirada</span><span class="sxs-lookup"><span data-stu-id="c65be-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="c65be-111">[Observación](gaze.md) es el primer formulario de entrada y revela el reconocimiento y la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="c65be-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="c65be-112">El Sr. entrada 210 (también conocido como el Explorador de proyectos) es una profundización en los conceptos relacionados con la mirada para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c65be-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="c65be-113">Iremos agregando reconocimiento contextual a nuestro cursor y hologramas, si quiere aprovechar lo que la aplicación conoce mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="c65be-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="c65be-114">Tenemos un astronautas descriptivo que le ayudarán a aprender los conceptos de mirada.</span><span class="sxs-lookup"><span data-stu-id="c65be-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="c65be-115">En [MR Fundamentos 101](holograms-101.md), tuvimos un cursor sencillo que simplemente seguir su mirada.</span><span class="sxs-lookup"><span data-stu-id="c65be-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="c65be-116">Hoy nos estamos trasladando un paso más allá de los cursores simples:</span><span class="sxs-lookup"><span data-stu-id="c65be-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="c65be-117">Estamos haciendo el cursor y nuestro hologramas basadas en la mirada: ambos cambiará en función de donde el usuario examina - o cuando el usuario es *no* buscando.</span><span class="sxs-lookup"><span data-stu-id="c65be-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="c65be-118">Esto hace que sean compatibles con el contexto.</span><span class="sxs-lookup"><span data-stu-id="c65be-118">This makes them context-aware.</span></span>
* <span data-ttu-id="c65be-119">Comentarios, agregaremos a nuestro cursor y hologramas para proporcionar al usuario obtener más contexto sobre lo que está usando como objetivo.</span><span class="sxs-lookup"><span data-stu-id="c65be-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="c65be-120">Estos comentarios pueden audio y visuales.</span><span class="sxs-lookup"><span data-stu-id="c65be-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="c65be-121">Le mostraremos destinatarios técnicas para ayudar a los usuarios a destinos más pequeños de posicionamiento.</span><span class="sxs-lookup"><span data-stu-id="c65be-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="c65be-122">Le mostraremos cómo atraer la atención del usuario a sus hologramas con un indicador de dirección.</span><span class="sxs-lookup"><span data-stu-id="c65be-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="c65be-123">Podrá mostrarle las técnicas para aprovechar sus hologramas con el usuario mientras se desplaza en torno a su mundo.</span><span class="sxs-lookup"><span data-stu-id="c65be-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c65be-124">Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c65be-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="c65be-125">Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="c65be-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="c65be-126">Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.</span><span class="sxs-lookup"><span data-stu-id="c65be-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="c65be-127">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="c65be-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c65be-128">Curso</span><span class="sxs-lookup"><span data-stu-id="c65be-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c65be-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c65be-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c65be-130"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="c65be-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c65be-131">Entrada MR 210: Mirada</span><span class="sxs-lookup"><span data-stu-id="c65be-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="c65be-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c65be-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c65be-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c65be-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c65be-134">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="c65be-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c65be-135">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c65be-135">Prerequisites</span></span>

* <span data-ttu-id="c65be-136">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c65be-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c65be-137">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="c65be-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c65be-138">Debe haber completado [MR Fundamentos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="c65be-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c65be-139">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c65be-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c65be-140">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="c65be-140">Project files</span></span>

* <span data-ttu-id="c65be-141">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c65be-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="c65be-142"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c65be-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="c65be-143">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="c65be-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c65be-144">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="c65be-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c65be-145">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="c65be-145">Errata and Notes</span></span>

* <span data-ttu-id="c65be-146">En Visual Studio, debe ser "Solo mi código" deshabilitado (desactivado) en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="c65be-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="c65be-147">Capítulo 1: instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="c65be-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="c65be-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-148">Objectives</span></span>

* <span data-ttu-id="c65be-149">Optimizar el desarrollo de HoloLens Unity.</span><span class="sxs-lookup"><span data-stu-id="c65be-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="c65be-150">Importar recursos y configuración de la escena.</span><span class="sxs-lookup"><span data-stu-id="c65be-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="c65be-151">Ver a los astronautas en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c65be-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="c65be-152">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c65be-152">Instructions</span></span>

1. <span data-ttu-id="c65be-153">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="c65be-153">Start Unity.</span></span>
2. <span data-ttu-id="c65be-154">Seleccione **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="c65be-154">Select **New Project**.</span></span>
3. <span data-ttu-id="c65be-155">Denomine el proyecto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="c65be-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="c65be-156">Escriba la ubicación que el **que mirar** carpeta que anteriormente no archivados.</span><span class="sxs-lookup"><span data-stu-id="c65be-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="c65be-157">Asegúrese de que el proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="c65be-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="c65be-158">Haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="c65be-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="c65be-159">Configuración de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="c65be-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="c65be-160">Es necesario informar a Unity que se debe crear la aplicación que estamos intentando exportar una [vista envolvente](app-views.md) en lugar de una vista 2D.</span><span class="sxs-lookup"><span data-stu-id="c65be-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="c65be-161">Para hacerlo mediante la adición de HoloLens como un dispositivo de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="c65be-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="c65be-162">Vaya a **Editar > configuración del proyecto > Reproductor**.</span><span class="sxs-lookup"><span data-stu-id="c65be-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="c65be-163">En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.</span><span class="sxs-lookup"><span data-stu-id="c65be-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="c65be-164">Expanda el **configuración XR** grupo.</span><span class="sxs-lookup"><span data-stu-id="c65be-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="c65be-165">En el **representación** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **SDK de realidad Virtual** lista.</span><span class="sxs-lookup"><span data-stu-id="c65be-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="c65be-166">Compruebe que **Windows Mixed Reality** aparece en la lista.</span><span class="sxs-lookup"><span data-stu-id="c65be-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="c65be-167">Si no, seleccione el **+** situado en la parte inferior de la lista y elija **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="c65be-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="c65be-168">A continuación, se debe establecer nuestro back-end de scripting a. NET.</span><span class="sxs-lookup"><span data-stu-id="c65be-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="c65be-169">Vaya a **Editar > configuración del proyecto > Reproductor** (todavía puede tener esta en el paso anterior).</span><span class="sxs-lookup"><span data-stu-id="c65be-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="c65be-170">En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.</span><span class="sxs-lookup"><span data-stu-id="c65be-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="c65be-171">En el **otra configuración** configuración sección, asegúrese de que **back-end de Scripting** está establecido en **.NET**</span><span class="sxs-lookup"><span data-stu-id="c65be-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="c65be-172">Por último, actualizaremos nuestra configuración de calidad para lograr un rendimiento rápido en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c65be-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="c65be-173">Vaya a **Editar > configuración del proyecto > calidad**.</span><span class="sxs-lookup"><span data-stu-id="c65be-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="c65be-174">Haga clic en la flecha hacia abajo en la **predeterminado** fila bajo el icono de Windows Store.</span><span class="sxs-lookup"><span data-stu-id="c65be-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="c65be-175">Seleccione **muy baja** para **Windows Store Apps**.</span><span class="sxs-lookup"><span data-stu-id="c65be-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="c65be-176">Importar los recursos del proyecto</span><span class="sxs-lookup"><span data-stu-id="c65be-176">Import project assets</span></span>

1. <span data-ttu-id="c65be-177">Haga clic en el **activos** carpeta en el **proyecto** panel.</span><span class="sxs-lookup"><span data-stu-id="c65be-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="c65be-178">Haga clic en **Importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="c65be-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="c65be-179">Vaya a los archivos del proyecto descargado y haga clic en **ModelExplorer.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="c65be-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="c65be-180">Haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="c65be-180">Click **Open**.</span></span>
5. <span data-ttu-id="c65be-181">Después de carga el paquete, haga clic en el **importación** botón.</span><span class="sxs-lookup"><span data-stu-id="c65be-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="c65be-182">Programa de instalación de la escena</span><span class="sxs-lookup"><span data-stu-id="c65be-182">Setup the scene</span></span>

1. <span data-ttu-id="c65be-183">En la jerarquía, elimine el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="c65be-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="c65be-184">En el **HoloToolkit** carpeta, abra el **entrada** carpeta, a continuación, abra el **prefabricados** carpeta.</span><span class="sxs-lookup"><span data-stu-id="c65be-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="c65be-185">Arrastre y coloque el **MixedRealityCameraParent** prefabricado desde el **prefabricados** carpeta en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="c65be-186">Haga clic en el **luz direccional** en la jerarquía y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="c65be-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="c65be-187">En el **hologramas** carpeta, arrastre y coloque los recursos siguientes en la raíz de la **jerarquía**:</span><span class="sxs-lookup"><span data-stu-id="c65be-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="c65be-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="c65be-188">**AstroMan**</span></span>
    * <span data-ttu-id="c65be-189">**luces**</span><span class="sxs-lookup"><span data-stu-id="c65be-189">**Lights**</span></span>
    * <span data-ttu-id="c65be-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="c65be-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="c65be-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="c65be-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="c65be-192">Iniciar **reproducir modo** ▶ para ver los astronautas.</span><span class="sxs-lookup"><span data-stu-id="c65be-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="c65be-193">Haga clic en **reproducir modo** ▶ nuevamente a **detener**.</span><span class="sxs-lookup"><span data-stu-id="c65be-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="c65be-194">En el **hologramas** carpeta, busque el **Fitbox** activo y arrástrelo a la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="c65be-195">Seleccione el **Fitbox** en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="c65be-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="c65be-196">Arrastre el **AstroMan** colección desde la **jerarquía** a la **holograma colección** propiedad de la Fitbox en el **Inspector** panel.</span><span class="sxs-lookup"><span data-stu-id="c65be-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="c65be-197">Guarde el proyecto</span><span class="sxs-lookup"><span data-stu-id="c65be-197">Save the project</span></span>

1. <span data-ttu-id="c65be-198">Guarde la nueva escena: **Archivo > Guardar escena como**.</span><span class="sxs-lookup"><span data-stu-id="c65be-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="c65be-199">Haga clic en **nueva carpeta** y el nombre de la carpeta **escenas**.</span><span class="sxs-lookup"><span data-stu-id="c65be-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="c65be-200">Nombre del archivo "**ModelExplorer**" y guárdela en el **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="c65be-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="c65be-201">Compilar el proyecto</span><span class="sxs-lookup"><span data-stu-id="c65be-201">Build the project</span></span>

1. <span data-ttu-id="c65be-202">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="c65be-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c65be-203">Haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="c65be-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c65be-204">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="c65be-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="c65be-205">Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c65be-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c65be-206">En caso contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c65be-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="c65be-207">Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="c65be-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="c65be-208">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="c65be-208">Click **Build**.</span></span>
7. <span data-ttu-id="c65be-209">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="c65be-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="c65be-210">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="c65be-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="c65be-211">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="c65be-211">Press **Select Folder**.</span></span>

<span data-ttu-id="c65be-212">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="c65be-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c65be-213">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="c65be-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="c65be-214">Abra el **ModelExplorer Visual Studio solución**.</span><span class="sxs-lookup"><span data-stu-id="c65be-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c65be-215">Si la implementación en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c65be-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c65be-216">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="c65be-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c65be-217">Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="c65be-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c65be-218">Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**.</span><span class="sxs-lookup"><span data-stu-id="c65be-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c65be-219">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="c65be-219">Click **Select**.</span></span> <span data-ttu-id="c65be-220">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="c65be-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c65be-221">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c65be-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c65be-222">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="c65be-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="c65be-223">Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.</span><span class="sxs-lookup"><span data-stu-id="c65be-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="c65be-224">Si la implementación en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="c65be-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c65be-225">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="c65be-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c65be-226">Asegúrese de que el destino de implementación se establece en **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="c65be-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c65be-227">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c65be-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="c65be-228">Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="c65be-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="c65be-229">Capítulo 2: comentarios del Cursor y de destino</span><span class="sxs-lookup"><span data-stu-id="c65be-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="c65be-230">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-230">Objectives</span></span>

* <span data-ttu-id="c65be-231">Diseño visual del cursor y el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="c65be-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="c65be-232">Comentarios del cursor basado en la mirada.</span><span class="sxs-lookup"><span data-stu-id="c65be-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="c65be-233">Comentarios en función de mirada holograma.</span><span class="sxs-lookup"><span data-stu-id="c65be-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="c65be-234">Vamos a basar nuestra labor en algunos principios de diseño de cursor, a saber:</span><span class="sxs-lookup"><span data-stu-id="c65be-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="c65be-235">El cursor siempre está presente.</span><span class="sxs-lookup"><span data-stu-id="c65be-235">The cursor is always present.</span></span>
* <span data-ttu-id="c65be-236">No permita que el cursor obtener demasiado pequeña o grande.</span><span class="sxs-lookup"><span data-stu-id="c65be-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="c65be-237">Evite obstrucción de contenido.</span><span class="sxs-lookup"><span data-stu-id="c65be-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="c65be-238">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c65be-238">Instructions</span></span>

1. <span data-ttu-id="c65be-239">En el **HoloToolkit\Input\Prefabs** carpeta, busque la **InputManager** activo.</span><span class="sxs-lookup"><span data-stu-id="c65be-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="c65be-240">Arrastre y coloque el **InputManager** hasta la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="c65be-241">En el **HoloToolkit\Input\Prefabs** carpeta, busque la **Cursor** activo.</span><span class="sxs-lookup"><span data-stu-id="c65be-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="c65be-242">Arrastre y coloque el **Cursor** hasta la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="c65be-243">Seleccione el **InputManager** objeto en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="c65be-244">Arrastre el **Cursor** objeto desde el **jerarquía** en el InputManager **SimpleSinglePointerSelector**del **Cursor** campo, en el parte inferior de la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c65be-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configuración de Selector de puntero único simple](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="c65be-246">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="c65be-246">Build and Deploy</span></span>

1. <span data-ttu-id="c65be-247">Vuelva a compilar la aplicación de **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="c65be-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="c65be-248">Abra el **carpeta aplicación**.</span><span class="sxs-lookup"><span data-stu-id="c65be-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="c65be-249">Abra el **ModelExplorer Visual Studio solución**.</span><span class="sxs-lookup"><span data-stu-id="c65be-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="c65be-250">Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c65be-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="c65be-251">Observe cómo se dibuja el cursor, y cómo cambia de apariencia si toca un holograma.</span><span class="sxs-lookup"><span data-stu-id="c65be-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="c65be-252">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c65be-252">Instructions</span></span>

1. <span data-ttu-id="c65be-253">En el **jerarquía** del panel, expanda el **AstroMan**->**GEO_G**->**Back_Center** objeto.</span><span class="sxs-lookup"><span data-stu-id="c65be-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="c65be-254">Haga doble clic en **Interactible.cs** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c65be-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="c65be-255">Comentarios de las líneas en el **IFocusable.OnFocusEnter()** y **IFocusable.OnFocusExit()** devoluciones de llamada en **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="c65be-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="c65be-256">Se denominan por InputManager Mixed Reality del Kit de herramientas cuando el foco (ya sea mediante la mirada o controlador señalando) entra y sale colisionador del GameObject específico.</span><span class="sxs-lookup"><span data-stu-id="c65be-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="c65be-257">Usamos `EnableKeyword` y `DisableKeyword` anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c65be-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="c65be-258">Para hacer que el uso de estas opciones en su propia aplicación con el sombreador de este Kit de herramientas estándar, deberá seguir el [directrices de Unity para tener acceso a materiales a través de la secuencia de comandos](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="c65be-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="c65be-259">En este caso, ya hemos incluido la [tres variantes de material resaltado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necesarios en la carpeta de recursos (busque los materiales con resaltado en el nombre de tres).</span><span class="sxs-lookup"><span data-stu-id="c65be-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c65be-260">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="c65be-260">Build and Deploy</span></span>

1. <span data-ttu-id="c65be-261">Como antes, compile el proyecto e implemente en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c65be-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="c65be-262">Observe lo que sucede cuando la mirada está destinado a un objeto y cuando no lo es.</span><span class="sxs-lookup"><span data-stu-id="c65be-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="c65be-263">Capítulo 3: técnicas de destinatarios</span><span class="sxs-lookup"><span data-stu-id="c65be-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="c65be-264">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-264">Objectives</span></span>

* <span data-ttu-id="c65be-265">Facilitar hologramas de destino.</span><span class="sxs-lookup"><span data-stu-id="c65be-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="c65be-266">Estabilizar movimientos principales naturales.</span><span class="sxs-lookup"><span data-stu-id="c65be-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="c65be-267">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c65be-267">Instructions</span></span>

1. <span data-ttu-id="c65be-268">En el **jerarquía** panel, seleccione el **InputManager** objeto.</span><span class="sxs-lookup"><span data-stu-id="c65be-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="c65be-269">En el **Inspector** panel, busque el **que mirar estabilizador** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="c65be-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="c65be-270">Haga clic en él para abrirlo en Visual Studio, si desea echar un vistazo.</span><span class="sxs-lookup"><span data-stu-id="c65be-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="c65be-271">Este script recorre en iteración las muestras de datos Raycast y ayuda a estabilizar la mirada del usuario para dirigirse a la precisión.</span><span class="sxs-lookup"><span data-stu-id="c65be-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="c65be-272">En el **Inspector**, puede editar el **almacenados estabilidad ejemplos** valor.</span><span class="sxs-lookup"><span data-stu-id="c65be-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="c65be-273">Este valor representa el número de muestras que el estabilizador itera a calcular el valor estabilizado.</span><span class="sxs-lookup"><span data-stu-id="c65be-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="c65be-274">Capítulo 4: indicador de dirección</span><span class="sxs-lookup"><span data-stu-id="c65be-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="c65be-275">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-275">Objectives</span></span>

* <span data-ttu-id="c65be-276">Agregar un indicador de dirección en el cursor para ayudar a encontrar hologramas.</span><span class="sxs-lookup"><span data-stu-id="c65be-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="c65be-277">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c65be-277">Instructions</span></span>

<span data-ttu-id="c65be-278">Vamos a usar el **DirectionIndicator.cs** archivo, que:</span><span class="sxs-lookup"><span data-stu-id="c65be-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="c65be-279">Mostrar el indicador de dirección si el usuario no es gazing en el hologramas.</span><span class="sxs-lookup"><span data-stu-id="c65be-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="c65be-280">Si el usuario es gazing en el hologramas, ocultar el indicador de dirección.</span><span class="sxs-lookup"><span data-stu-id="c65be-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="c65be-281">Actualice el indicador de dirección para que apunte a la hologramas.</span><span class="sxs-lookup"><span data-stu-id="c65be-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="c65be-282">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="c65be-282">Let's get started.</span></span>

1. <span data-ttu-id="c65be-283">Haga clic en el **AstroMan** objeto en el **jerarquía** panel y **haga clic en la flecha** para expandirlo.</span><span class="sxs-lookup"><span data-stu-id="c65be-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="c65be-284">En el **jerarquía** panel, seleccione el **DirectionalIndicator** objeto bajo **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="c65be-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="c65be-285">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="c65be-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="c65be-286">En el menú, escriba en el cuadro de búsqueda **indicador de dirección**.</span><span class="sxs-lookup"><span data-stu-id="c65be-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="c65be-287">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c65be-287">Select the search result.</span></span>
5. <span data-ttu-id="c65be-288">En el **jerarquía** panel, arrastre y coloque el **Cursor** objeto en el **Cursor** propiedad en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c65be-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="c65be-289">En el **proyecto** panel el **hologramas** carpeta, arrastre y coloque el **DirectionalIndicator** activo hasta la **indicadores direccionales**propiedad en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c65be-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="c65be-290">Compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c65be-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="c65be-291">Vea cómo el objeto de indicadores direccionales le ayuda a encontrar a los astronautas.</span><span class="sxs-lookup"><span data-stu-id="c65be-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="c65be-292">Capítulo 5: vallas publicitarias</span><span class="sxs-lookup"><span data-stu-id="c65be-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="c65be-293">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-293">Objectives</span></span>

* <span data-ttu-id="c65be-294">Usar vallas publicitarias para hologramas hacia TI se enfrentan a siempre.</span><span class="sxs-lookup"><span data-stu-id="c65be-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="c65be-295">Vamos a usar el **Billboard.cs** archivo para mantener un GameObject orientada a servicios, que es accesible desde el usuario en todo momento.</span><span class="sxs-lookup"><span data-stu-id="c65be-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="c65be-296">En el **jerarquía** panel, seleccione el **AstroMan** objeto.</span><span class="sxs-lookup"><span data-stu-id="c65be-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="c65be-297">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="c65be-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="c65be-298">En el menú, escriba en el cuadro de búsqueda **cartelera**.</span><span class="sxs-lookup"><span data-stu-id="c65be-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="c65be-299">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c65be-299">Select the search result.</span></span>
4. <span data-ttu-id="c65be-300">En el **Inspector** establecer el **Pivot eje** a **Y**.</span><span class="sxs-lookup"><span data-stu-id="c65be-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="c65be-301">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="c65be-301">Try it!</span></span> <span data-ttu-id="c65be-302">Compile e implemente la aplicación como antes.</span><span class="sxs-lookup"><span data-stu-id="c65be-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="c65be-303">Vea Cómo enfrenta el objeto cartelera independientemente de cómo se puede cambiar el punto de vista.</span><span class="sxs-lookup"><span data-stu-id="c65be-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="c65be-304">Elimine el script desde el **AstroMan** por ahora.</span><span class="sxs-lookup"><span data-stu-id="c65be-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="c65be-305">Capítulo 6: Tag-Along</span><span class="sxs-lookup"><span data-stu-id="c65be-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="c65be-306">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c65be-306">Objectives</span></span>

* <span data-ttu-id="c65be-307">Usar Tag-Along para que nuestro hologramas Síganos en torno a la sala de reuniones.</span><span class="sxs-lookup"><span data-stu-id="c65be-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="c65be-308">Mientras se trabaja en este problema, se le guiará por las restricciones de diseño siguientes:</span><span class="sxs-lookup"><span data-stu-id="c65be-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="c65be-309">Contenido siempre debe ser un solo vistazo ausente.</span><span class="sxs-lookup"><span data-stu-id="c65be-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="c65be-310">No debe ser el contenido de la forma.</span><span class="sxs-lookup"><span data-stu-id="c65be-310">Content should not be in the way.</span></span>
* <span data-ttu-id="c65be-311">Contenido principal de bloqueo es incómodo.</span><span class="sxs-lookup"><span data-stu-id="c65be-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="c65be-312">La solución que se usa aquí es usar un enfoque de "tag-along".</span><span class="sxs-lookup"><span data-stu-id="c65be-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="c65be-313">Un objeto tag-along totalmente nunca deja la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="c65be-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="c65be-314">Se puede considerar el un tag-along como un objeto asociado al encabezado del usuario bandas de goma.</span><span class="sxs-lookup"><span data-stu-id="c65be-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="c65be-315">Cuando el usuario se mueve, se mantendrá el contenido dentro de un solo vistazo fácil desplazando hacia el borde de la vista sin salir completamente.</span><span class="sxs-lookup"><span data-stu-id="c65be-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="c65be-316">Cuando el usuario gazes hacia el objeto tag-along, resulta más completa en la vista.</span><span class="sxs-lookup"><span data-stu-id="c65be-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="c65be-317">Vamos a usar el **SimpleTagalong.cs** archivo, que:</span><span class="sxs-lookup"><span data-stu-id="c65be-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="c65be-318">Determine si el objeto Tag-Along dentro de los límites de la cámara.</span><span class="sxs-lookup"><span data-stu-id="c65be-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="c65be-319">Si no es así en frustum de visualización, colocar el Tag-Along a parcialmente dentro del frustum de vista.</span><span class="sxs-lookup"><span data-stu-id="c65be-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="c65be-320">En caso contrario, coloque el Tag-Along a una distancia predeterminada del usuario.</span><span class="sxs-lookup"><span data-stu-id="c65be-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="c65be-321">Para ello, primero debemos cambiar el **Interactible.cs** script para llamar a la **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="c65be-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="c65be-322">Editar **Interactible.cs** completando codificación ejercicio 6.a (84 a 87 quitando los comentarios de líneas).</span><span class="sxs-lookup"><span data-stu-id="c65be-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="c65be-323">El **InteractibleAction.cs** secuencia de comandos, emparejada con **Interactible.cs** realiza acciones personalizadas cuando pulse en hologramas.</span><span class="sxs-lookup"><span data-stu-id="c65be-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="c65be-324">En este caso, vamos a usar otro específicamente para tag-along.</span><span class="sxs-lookup"><span data-stu-id="c65be-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="c65be-325">En el **Scripts** carpeta, haga clic en **TagalongAction.cs** activos para abrir en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c65be-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="c65be-326">Completar el ejercicio de codificación o cámbielo a esto:</span><span class="sxs-lookup"><span data-stu-id="c65be-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="c65be-327">En la parte superior de la **jerarquía**, en el tipo de barra de búsqueda **ChestButton_Center** y seleccione el resultado.</span><span class="sxs-lookup"><span data-stu-id="c65be-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="c65be-328">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="c65be-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="c65be-329">En el menú, escriba en el cuadro de búsqueda **acción sean**.</span><span class="sxs-lookup"><span data-stu-id="c65be-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="c65be-330">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c65be-330">Select the search result.</span></span>
  * <span data-ttu-id="c65be-331">En **hologramas** Buscar carpeta la **sean** activo.</span><span class="sxs-lookup"><span data-stu-id="c65be-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="c65be-332">Seleccione el **ChestButton_Center** objeto en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c65be-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="c65be-333">Arrastrar y colocar la **sean** objeto desde el **proyecto** panel en el **Inspector** en el **objeto a sean** propiedad.</span><span class="sxs-lookup"><span data-stu-id="c65be-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="c65be-334">Arrastre el **acción sean** objeto desde el **Inspector** en el **acción Interactible** campo el **Interactible** script.</span><span class="sxs-lookup"><span data-stu-id="c65be-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="c65be-335">Haga doble clic en el **TagalongAction** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c65be-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Instalación interactible](images/holograms210-interactible.png)

<span data-ttu-id="c65be-337">Se debe agregar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c65be-337">We need to add the following:</span></span>

* <span data-ttu-id="c65be-338">Agregar funcionalidad a la función PerformAction en el script TagalongAction (heredado de InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="c65be-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="c65be-339">Agregue vallas publicitarias para el objeto gazed tras y establezca el eje pivot en XY.</span><span class="sxs-lookup"><span data-stu-id="c65be-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="c65be-340">A continuación, agregue Tag-Along simple al objeto.</span><span class="sxs-lookup"><span data-stu-id="c65be-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="c65be-341">Aquí está nuestra solución, de **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="c65be-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="c65be-342">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="c65be-342">Try it!</span></span> <span data-ttu-id="c65be-343">Compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c65be-343">Build and deploy the app.</span></span>
* <span data-ttu-id="c65be-344">Vea cómo el contenido sigue el centro del punto de mirada, pero no continuamente y sin bloquearla.</span><span class="sxs-lookup"><span data-stu-id="c65be-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
