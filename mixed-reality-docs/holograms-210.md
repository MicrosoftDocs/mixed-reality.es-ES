---
title: Entrada MR 210-mirada
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de la mirada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, mira fijamente
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434684"
---
>[!NOTE]
><span data-ttu-id="8efed-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="8efed-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8efed-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8efed-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8efed-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8efed-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8efed-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="8efed-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8efed-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8efed-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="8efed-109">Entrada MR 210: mirada</span><span class="sxs-lookup"><span data-stu-id="8efed-109">MR Input 210: Gaze</span></span>

<span data-ttu-id="8efed-110">[Mira](gaze-and-commit.md) la primera forma de entrada y revela la intención y el reconocimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="8efed-110">[Gaze](gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="8efed-111">La entrada MR 210 (también conocido como Project Explorer) es un análisis profundo de los conceptos relacionados con la mirada para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8efed-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="8efed-112">Agregaremos reconocimiento contextual a nuestro cursor y a los hologramas, aprovechando al máximo lo que la aplicación conoce sobre la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="8efed-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="8efed-113">Tenemos un Astronaut descriptivo aquí para ayudarle a conocer los conceptos de la mirada.</span><span class="sxs-lookup"><span data-stu-id="8efed-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="8efed-114">En los [principios de MR 101](holograms-101.md), teníamos un cursor sencillo que acaba de hacer una mirada.</span><span class="sxs-lookup"><span data-stu-id="8efed-114">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="8efed-115">Hoy vamos a mover un paso más allá del cursor simple:</span><span class="sxs-lookup"><span data-stu-id="8efed-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="8efed-116">Estamos haciendo el cursor y nuestros hologramas con atención rápida: ambos cambiarán en función de dónde esté buscando el usuario o de dónde *no* esté buscando el usuario.</span><span class="sxs-lookup"><span data-stu-id="8efed-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="8efed-117">Esto hace que sean compatibles con el contexto.</span><span class="sxs-lookup"><span data-stu-id="8efed-117">This makes them context-aware.</span></span>
* <span data-ttu-id="8efed-118">Agregaremos comentarios a nuestro cursor y a los hologramas para proporcionar al usuario más contexto sobre lo que se va a dirigir.</span><span class="sxs-lookup"><span data-stu-id="8efed-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="8efed-119">Estos comentarios pueden ser audio y objetos visuales.</span><span class="sxs-lookup"><span data-stu-id="8efed-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="8efed-120">Le mostraremos las técnicas de destino para ayudar a los usuarios a alcanzar destinos más pequeños.</span><span class="sxs-lookup"><span data-stu-id="8efed-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="8efed-121">Le mostraremos cómo atraer la atención del usuario a sus hologramas con un indicador direccional.</span><span class="sxs-lookup"><span data-stu-id="8efed-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="8efed-122">Le enseñaremos técnicas para tomar sus hologramas con el usuario a medida que se desplaza por su mundo.</span><span class="sxs-lookup"><span data-stu-id="8efed-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="8efed-123">Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8efed-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8efed-124">Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="8efed-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="8efed-125">Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.</span><span class="sxs-lookup"><span data-stu-id="8efed-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="8efed-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="8efed-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8efed-127">Recurso</span><span class="sxs-lookup"><span data-stu-id="8efed-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8efed-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8efed-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8efed-129"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="8efed-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8efed-130">Entrada MR 210: mirada</span><span class="sxs-lookup"><span data-stu-id="8efed-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="8efed-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8efed-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8efed-132">✔️</span><span class="sxs-lookup"><span data-stu-id="8efed-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8efed-133">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="8efed-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8efed-134">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8efed-134">Prerequisites</span></span>

* <span data-ttu-id="8efed-135">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8efed-135">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="8efed-136">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="8efed-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8efed-137">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="8efed-137">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="8efed-138">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="8efed-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8efed-139">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="8efed-139">Project files</span></span>

* <span data-ttu-id="8efed-140">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8efed-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="8efed-141"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="8efed-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="8efed-142">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="8efed-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="8efed-143">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="8efed-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="8efed-144">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="8efed-144">Errata and Notes</span></span>

* <span data-ttu-id="8efed-145">En Visual Studio, "Solo mi código" debe estar deshabilitado (desactivado) en herramientas-> Opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="8efed-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="8efed-146">Capítulo 1: configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="8efed-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="8efed-147">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-147">Objectives</span></span>

* <span data-ttu-id="8efed-148">Optimizar Unity para el desarrollo de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8efed-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="8efed-149">Importar recursos y configurar la escena.</span><span class="sxs-lookup"><span data-stu-id="8efed-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="8efed-150">Vea el Astronaut en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8efed-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="8efed-151">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8efed-151">Instructions</span></span>

1. <span data-ttu-id="8efed-152">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="8efed-152">Start Unity.</span></span>
2. <span data-ttu-id="8efed-153">Seleccione **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="8efed-153">Select **New Project**.</span></span>
3. <span data-ttu-id="8efed-154">Asigne al proyecto el nombre **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="8efed-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="8efed-155">Escriba ubicación como la carpeta de **miras** que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="8efed-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="8efed-156">Asegúrate de que el proyecto esté establecido en **3D** (3D).</span><span class="sxs-lookup"><span data-stu-id="8efed-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="8efed-157">Haz clic en **Create Project** (Crear proyecto).</span><span class="sxs-lookup"><span data-stu-id="8efed-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="8efed-158">Configuración de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="8efed-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="8efed-159">Necesitamos que Unity sepa que la aplicación que se está intentando exportar debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D.</span><span class="sxs-lookup"><span data-stu-id="8efed-159">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="8efed-160">Lo hacemos agregando HoloLens como un dispositivo de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="8efed-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="8efed-161">Vaya a **editar > configuración del proyecto > Player**.</span><span class="sxs-lookup"><span data-stu-id="8efed-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="8efed-162">En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="8efed-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="8efed-163">Expanda el grupo de **configuración de XR** .</span><span class="sxs-lookup"><span data-stu-id="8efed-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="8efed-164">En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **SDK de realidad virtual** .</span><span class="sxs-lookup"><span data-stu-id="8efed-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="8efed-165">Compruebe que **Windows Mixed Reality** aparece en la lista.</span><span class="sxs-lookup"><span data-stu-id="8efed-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="8efed-166">Si no es así, seleccione el botón **+** situado en la parte inferior de la lista y elija **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="8efed-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="8efed-167">A continuación, es necesario establecer nuestro back-end de scripting en .NET.</span><span class="sxs-lookup"><span data-stu-id="8efed-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="8efed-168">Vaya a **editar > configuración del proyecto > Player** (es posible que todavía lo tenga en el paso anterior).</span><span class="sxs-lookup"><span data-stu-id="8efed-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="8efed-169">En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="8efed-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="8efed-170">En la sección configuración de **otros valores** , asegúrese de que el **back-end de scripting** está establecido en **.net.**</span><span class="sxs-lookup"><span data-stu-id="8efed-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="8efed-171">Por último, actualizaremos la configuración de calidad para lograr un rendimiento rápido en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8efed-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="8efed-172">Vaya a **editar > configuración del proyecto > calidad**.</span><span class="sxs-lookup"><span data-stu-id="8efed-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="8efed-173">Haga clic en la flecha hacia abajo de la fila **predeterminada** bajo el icono de la tienda Windows.</span><span class="sxs-lookup"><span data-stu-id="8efed-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="8efed-174">Seleccione **muy bajo** para **aplicaciones de la tienda Windows**.</span><span class="sxs-lookup"><span data-stu-id="8efed-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="8efed-175">Importar recursos del proyecto</span><span class="sxs-lookup"><span data-stu-id="8efed-175">Import project assets</span></span>

1. <span data-ttu-id="8efed-176">Haga clic con el botón secundario en la carpeta **activos** del panel **proyecto** .</span><span class="sxs-lookup"><span data-stu-id="8efed-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="8efed-177">Haga clic en **importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="8efed-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="8efed-178">Navegue hasta los archivos de proyecto que descargó y haga clic en **ModelExplorer. unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="8efed-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="8efed-179">Haz clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="8efed-179">Click **Open**.</span></span>
5. <span data-ttu-id="8efed-180">Una vez cargado el paquete, haga clic en el botón **importar** .</span><span class="sxs-lookup"><span data-stu-id="8efed-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="8efed-181">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="8efed-181">Setup the scene</span></span>

1. <span data-ttu-id="8efed-182">En la jerarquía, elimine la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="8efed-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="8efed-183">En la carpeta **HoloToolkit** , abra la carpeta **Input** y, a continuación, abra la carpeta **Prefabs** .</span><span class="sxs-lookup"><span data-stu-id="8efed-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="8efed-184">Arrastre y coloque el recurso prefabricado de **MixedRealityCameraParent** de la carpeta **Prefabs** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="8efed-185">Haga clic con el botón derecho en la **luz direccional** de la jerarquía y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="8efed-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="8efed-186">En la carpeta **hologramas** , arrastre y coloque los recursos siguientes en la raíz de la **jerarquía**:</span><span class="sxs-lookup"><span data-stu-id="8efed-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="8efed-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="8efed-187">**AstroMan**</span></span>
    * <span data-ttu-id="8efed-188">**Circular**</span><span class="sxs-lookup"><span data-stu-id="8efed-188">**Lights**</span></span>
    * <span data-ttu-id="8efed-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="8efed-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="8efed-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="8efed-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="8efed-191">Inicie el **modo de reproducción** ▶ para ver el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8efed-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="8efed-192">Vuelva a hacer clic en **modo de reproducción** ▶ para **detenerse**.</span><span class="sxs-lookup"><span data-stu-id="8efed-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="8efed-193">En la carpeta **hologramas** , busque el recurso **Fitbox** y arrástrelo hasta la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="8efed-194">Seleccione **Fitbox** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="8efed-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="8efed-195">Arrastre la colección **AstroMan** desde la **jerarquía** a la propiedad de **colección holograma** de Fitbox en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="8efed-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="8efed-196">Guardar el proyecto</span><span class="sxs-lookup"><span data-stu-id="8efed-196">Save the project</span></span>

1. <span data-ttu-id="8efed-197">Guarde la nueva escena: **archivo > guardar la escena como**.</span><span class="sxs-lookup"><span data-stu-id="8efed-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="8efed-198">Haga clic en **nueva carpeta** y asigne un nombre a la carpeta **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="8efed-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="8efed-199">Asigne al archivo el nombre "**ModelExplorer**" y guárdelo en la carpeta **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="8efed-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="8efed-200">Compilar el proyecto</span><span class="sxs-lookup"><span data-stu-id="8efed-200">Build the project</span></span>

1. <span data-ttu-id="8efed-201">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="8efed-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8efed-202">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="8efed-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="8efed-203">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="8efed-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="8efed-204">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="8efed-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="8efed-205">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8efed-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="8efed-206">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="8efed-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="8efed-207">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="8efed-207">Click **Build**.</span></span>
7. <span data-ttu-id="8efed-208">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="8efed-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="8efed-209">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8efed-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="8efed-210">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="8efed-210">Press **Select Folder**.</span></span>

<span data-ttu-id="8efed-211">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="8efed-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="8efed-212">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8efed-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="8efed-213">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8efed-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="8efed-214">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="8efed-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="8efed-215">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="8efed-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="8efed-216">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="8efed-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="8efed-217">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="8efed-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="8efed-218">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="8efed-218">Click **Select**.</span></span> <span data-ttu-id="8efed-219">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="8efed-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="8efed-220">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8efed-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="8efed-221">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="8efed-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="8efed-222">Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.</span><span class="sxs-lookup"><span data-stu-id="8efed-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="8efed-223">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="8efed-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="8efed-224">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="8efed-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="8efed-225">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="8efed-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="8efed-226">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8efed-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="8efed-227">Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="8efed-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="8efed-228">Capítulo 2: comentarios de cursores y de destino</span><span class="sxs-lookup"><span data-stu-id="8efed-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="8efed-229">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-229">Objectives</span></span>

* <span data-ttu-id="8efed-230">Comportamiento y diseño visual de los cursores.</span><span class="sxs-lookup"><span data-stu-id="8efed-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="8efed-231">Comentarios del cursor basados en la mirada.</span><span class="sxs-lookup"><span data-stu-id="8efed-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="8efed-232">Comentarios sobre hologramas basados en la mirada.</span><span class="sxs-lookup"><span data-stu-id="8efed-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="8efed-233">Vamos a basar nuestro trabajo en algunos principios de diseño de cursores, es decir:</span><span class="sxs-lookup"><span data-stu-id="8efed-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="8efed-234">El cursor siempre está presente.</span><span class="sxs-lookup"><span data-stu-id="8efed-234">The cursor is always present.</span></span>
* <span data-ttu-id="8efed-235">No deje que el cursor sea demasiado pequeño o grande.</span><span class="sxs-lookup"><span data-stu-id="8efed-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="8efed-236">Evite obstruir el contenido.</span><span class="sxs-lookup"><span data-stu-id="8efed-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="8efed-237">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8efed-237">Instructions</span></span>

1. <span data-ttu-id="8efed-238">En la carpeta **HoloToolkit\Input\Prefabs** , busque el recurso **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="8efed-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="8efed-239">Arrastre y coloque el **InputManager** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="8efed-240">En la carpeta **HoloToolkit\Input\Prefabs** , busque el recurso **cursor** .</span><span class="sxs-lookup"><span data-stu-id="8efed-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="8efed-241">Arrastre y coloque el **cursor** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="8efed-242">Seleccione el objeto **InputManager** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="8efed-243">Arrastre el objeto **cursor** desde la **jerarquía** al campo **cursor** de la **SimpleSinglePointerSelector**de InputManager, en la parte inferior del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="8efed-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configuración sencilla del selector de puntero único](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="8efed-245">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8efed-245">Build and Deploy</span></span>

1. <span data-ttu-id="8efed-246">Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="8efed-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="8efed-247">Abra la **carpeta**de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8efed-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="8efed-248">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8efed-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="8efed-249">Haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8efed-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="8efed-250">Observe cómo se dibuja el cursor y cómo cambia la apariencia si toca un holograma.</span><span class="sxs-lookup"><span data-stu-id="8efed-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="8efed-251">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8efed-251">Instructions</span></span>

1. <span data-ttu-id="8efed-252">En el panel **jerarquía** , expanda el objeto **AstroMan**->**GEO_G**->**Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="8efed-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="8efed-253">Haga doble clic en **Interactible.CS** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8efed-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="8efed-254">Quite las marcas de comentario de las líneas de las devoluciones de llamada **IFocusable. OnFocusEnter ()** y **IFocusable. OnFocusExit ()** en **Interactible.CS**.</span><span class="sxs-lookup"><span data-stu-id="8efed-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="8efed-255">Las llama el InputManager del kit de herramientas de realidad mixta cuando el foco (ya sea por miras o por controlador) entra y sale del Colisionador de GameObject específico.</span><span class="sxs-lookup"><span data-stu-id="8efed-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="8efed-256">Usamos `EnableKeyword` y `DisableKeyword` arriba.</span><span class="sxs-lookup"><span data-stu-id="8efed-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="8efed-257">Con el fin de usarlos en su propia aplicación con el sombreador estándar del kit de herramientas, debe seguir las [directrices de Unity para acceder a los materiales a través del script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="8efed-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="8efed-258">En este caso, ya hemos incluido las [tres variantes de material resaltado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necesarios en la carpeta de recursos (busque los tres materiales con resaltado en el nombre).</span><span class="sxs-lookup"><span data-stu-id="8efed-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="8efed-259">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8efed-259">Build and Deploy</span></span>

1. <span data-ttu-id="8efed-260">Como antes, compile el proyecto e impleméntelo en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8efed-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="8efed-261">Observe lo que sucede cuando la mirada está dirigida a un objeto y cuando no lo está.</span><span class="sxs-lookup"><span data-stu-id="8efed-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="8efed-262">Capítulo 3: técnicas de destino</span><span class="sxs-lookup"><span data-stu-id="8efed-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="8efed-263">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-263">Objectives</span></span>

* <span data-ttu-id="8efed-264">Facilitar el destino de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="8efed-265">Estabilice los movimientos de los cabezales naturales.</span><span class="sxs-lookup"><span data-stu-id="8efed-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="8efed-266">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8efed-266">Instructions</span></span>

1. <span data-ttu-id="8efed-267">En el panel **jerarquía** , seleccione el objeto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="8efed-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="8efed-268">En el panel **Inspector** , busque el script del **estabilizador de miras** .</span><span class="sxs-lookup"><span data-stu-id="8efed-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="8efed-269">Haga clic en él para abrirlo en Visual Studio, si desea echar un vistazo.</span><span class="sxs-lookup"><span data-stu-id="8efed-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="8efed-270">Este script recorre en iteración muestras de datos de Raycast y ayuda a estabilizar la mirada del usuario para el destino de precisión.</span><span class="sxs-lookup"><span data-stu-id="8efed-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="8efed-271">En el **Inspector**, puede editar el valor de los **ejemplos de estabilidad almacenados** .</span><span class="sxs-lookup"><span data-stu-id="8efed-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="8efed-272">Este valor representa el número de muestras que el estabilizador recorre en iteración para calcular el valor estabilizado.</span><span class="sxs-lookup"><span data-stu-id="8efed-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="8efed-273">Capítulo 4: indicador direccional</span><span class="sxs-lookup"><span data-stu-id="8efed-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="8efed-274">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-274">Objectives</span></span>

* <span data-ttu-id="8efed-275">Agregue un indicador direccional en el cursor para buscar hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="8efed-276">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8efed-276">Instructions</span></span>

<span data-ttu-id="8efed-277">Vamos a usar el archivo **DirectionIndicator.CS** , que:</span><span class="sxs-lookup"><span data-stu-id="8efed-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="8efed-278">Muestra el indicador direccional si el usuario no se Gazing en los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="8efed-279">Oculte el indicador direccional si el usuario es Gazing en los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="8efed-280">Actualice el indicador direccional para que apunte a los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="8efed-281">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="8efed-281">Let's get started.</span></span>

1. <span data-ttu-id="8efed-282">Haga clic en el objeto **AstroMan** en el panel **jerarquía** y **haga clic en la flecha** para expandirlo.</span><span class="sxs-lookup"><span data-stu-id="8efed-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="8efed-283">En el panel **jerarquía** , seleccione el objeto **DirectionalIndicator** en **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="8efed-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="8efed-284">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="8efed-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="8efed-285">En el menú, escriba en el indicador de **Dirección**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8efed-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="8efed-286">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8efed-286">Select the search result.</span></span>
5. <span data-ttu-id="8efed-287">En el panel **jerarquía** , arrastre y coloque el objeto **cursor** en la propiedad **cursor** del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="8efed-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="8efed-288">En el **panel Proyecto** , en la **carpeta hologramas** , arrastre y coloque el recurso **DirectionalIndicator** en la propiedad **indicador direccional** del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="8efed-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="8efed-289">Compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8efed-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="8efed-290">Vea cómo el objeto indicador direccional le ayuda a encontrar el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8efed-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="8efed-291">Capítulo 5: cartelera</span><span class="sxs-lookup"><span data-stu-id="8efed-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="8efed-292">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-292">Objectives</span></span>

* <span data-ttu-id="8efed-293">Use la cartelera para que los hologramas siempre se encuentren en su caso.</span><span class="sxs-lookup"><span data-stu-id="8efed-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="8efed-294">Vamos a usar el archivo **Billboard.CS** para mantener una orientación GameObject de forma que se enfrente al usuario en todo momento.</span><span class="sxs-lookup"><span data-stu-id="8efed-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="8efed-295">En el panel **jerarquía** , seleccione el objeto **AstroMan** .</span><span class="sxs-lookup"><span data-stu-id="8efed-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="8efed-296">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="8efed-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="8efed-297">En el menú, escriba en el cuadro de búsqueda de la **cartelera**.</span><span class="sxs-lookup"><span data-stu-id="8efed-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="8efed-298">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8efed-298">Select the search result.</span></span>
4. <span data-ttu-id="8efed-299">En el **Inspector** , establezca el **eje dinámico** en **Y**.</span><span class="sxs-lookup"><span data-stu-id="8efed-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="8efed-300">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="8efed-300">Try it!</span></span> <span data-ttu-id="8efed-301">Compile e implemente la aplicación como antes.</span><span class="sxs-lookup"><span data-stu-id="8efed-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="8efed-302">Vea cómo se enfrenta el objeto de la cartelera independientemente de cómo cambie el punto de vista.</span><span class="sxs-lookup"><span data-stu-id="8efed-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="8efed-303">Elimine el script de **AstroMan** por ahora.</span><span class="sxs-lookup"><span data-stu-id="8efed-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="8efed-304">Capítulo 6: Etiquetas:</span><span class="sxs-lookup"><span data-stu-id="8efed-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="8efed-305">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8efed-305">Objectives</span></span>

* <span data-ttu-id="8efed-306">Use la etiqueta para que nuestros hologramas nos vayan alrededor de la habitación.</span><span class="sxs-lookup"><span data-stu-id="8efed-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="8efed-307">A medida que trabajamos en este problema, se le guiará por las siguientes restricciones de diseño:</span><span class="sxs-lookup"><span data-stu-id="8efed-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="8efed-308">El contenido siempre debe ser un vistazo.</span><span class="sxs-lookup"><span data-stu-id="8efed-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="8efed-309">El contenido no debe estar en el camino.</span><span class="sxs-lookup"><span data-stu-id="8efed-309">Content should not be in the way.</span></span>
* <span data-ttu-id="8efed-310">No se siente el contenido del bloqueo de encabezado.</span><span class="sxs-lookup"><span data-stu-id="8efed-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="8efed-311">La solución que se usa aquí es usar un enfoque "etiqueta a lo largo".</span><span class="sxs-lookup"><span data-stu-id="8efed-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="8efed-312">Un objeto de etiqueta no deja completamente la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="8efed-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="8efed-313">Puede pensar en una etiqueta, como un objeto asociado al encabezado del usuario por las bandas de goma.</span><span class="sxs-lookup"><span data-stu-id="8efed-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="8efed-314">A medida que el usuario se mueve, el contenido permanecerá dentro de un sencillo vistazo mediante la deslizamiento hacia el borde de la vista sin salir completamente.</span><span class="sxs-lookup"><span data-stu-id="8efed-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="8efed-315">Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver.</span><span class="sxs-lookup"><span data-stu-id="8efed-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="8efed-316">Vamos a usar el archivo **SimpleTagalong.CS** , que:</span><span class="sxs-lookup"><span data-stu-id="8efed-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="8efed-317">Determine si el objeto de etiqueta se encuentra dentro de los límites de la cámara.</span><span class="sxs-lookup"><span data-stu-id="8efed-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="8efed-318">Si no se encuentra dentro del frustum de vista, coloque la etiqueta junto a parcialmente dentro del frustum de la vista.</span><span class="sxs-lookup"><span data-stu-id="8efed-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="8efed-319">De lo contrario, coloque la etiqueta junto a una distancia predeterminada del usuario.</span><span class="sxs-lookup"><span data-stu-id="8efed-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="8efed-320">Para ello, primero debemos cambiar el script **Interactible.CS** para llamar a **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="8efed-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="8efed-321">Edite **Interactible.CS** completando la codificación del ejercicio 6. a (Quite los comentarios de las líneas 84 a 87).</span><span class="sxs-lookup"><span data-stu-id="8efed-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="8efed-322">El script **InteractibleAction.CS** , emparejado con **Interactible.CS** , realiza acciones personalizadas cuando se pulsa en los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8efed-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="8efed-323">En este caso, usaremos un específicamente para etiquetar.</span><span class="sxs-lookup"><span data-stu-id="8efed-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="8efed-324">En la carpeta **scripts** , haga clic en el recurso **TagalongAction.CS** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8efed-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="8efed-325">Complete el ejercicio de codificación o cámbielo por este:</span><span class="sxs-lookup"><span data-stu-id="8efed-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="8efed-326">En la parte superior de la **jerarquía**, en la barra de búsqueda, escriba **ChestButton_Center** y seleccione el resultado.</span><span class="sxs-lookup"><span data-stu-id="8efed-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="8efed-327">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="8efed-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="8efed-328">En el menú, escriba en la **acción tagalong**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8efed-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="8efed-329">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="8efed-329">Select the search result.</span></span>
  * <span data-ttu-id="8efed-330">En la carpeta **hologramas** , busque el recurso **tagalong** .</span><span class="sxs-lookup"><span data-stu-id="8efed-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="8efed-331">Seleccione el objeto **ChestButton_Center** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8efed-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="8efed-332">Arrastre y coloque el objeto **TagAlong** del panel **proyecto** en el **Inspector** en el **objeto en** la propiedad TagAlong.</span><span class="sxs-lookup"><span data-stu-id="8efed-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="8efed-333">Arrastre el objeto de **acción tagalong** desde el **Inspector** al campo **Acción** interactiva del script **interactuable** .</span><span class="sxs-lookup"><span data-stu-id="8efed-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="8efed-334">Haga doble clic en el script **TagalongAction** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8efed-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Instalación interactiva](images/holograms210-interactible.png)

<span data-ttu-id="8efed-336">Necesitamos agregar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8efed-336">We need to add the following:</span></span>

* <span data-ttu-id="8efed-337">Agregue funcionalidad a la función PerformAction en el script TagalongAction (se hereda de InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="8efed-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="8efed-338">Agregue la cartelera al objeto mirados y establezca el eje dinámico en XY.</span><span class="sxs-lookup"><span data-stu-id="8efed-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="8efed-339">A continuación, agregue la etiqueta simple junto al objeto.</span><span class="sxs-lookup"><span data-stu-id="8efed-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="8efed-340">Esta es nuestra solución, desde **TagalongAction.CS**:</span><span class="sxs-lookup"><span data-stu-id="8efed-340">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="8efed-341">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="8efed-341">Try it!</span></span> <span data-ttu-id="8efed-342">Compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8efed-342">Build and deploy the app.</span></span>
* <span data-ttu-id="8efed-343">Vea cómo el contenido sigue el centro del punto de miración, pero no continuamente y sin bloquearlo.</span><span class="sxs-lookup"><span data-stu-id="8efed-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
