---
title: Autocar manual
description: manos 3D que se desencadenan cuando el sistema no detecta las manos del usuario para ayudarles.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, autocar de mano, auriculares envolvente, MRTK, manos, ayudando a manos
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345674"
---
# <a name="hand-coach"></a><span data-ttu-id="f033a-104">Autocar manual</span><span class="sxs-lookup"><span data-stu-id="f033a-104">Hand coach</span></span>
![Ejemplo: autocar manual](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="f033a-106">El autocar de mano es una práctica con modelo 3D que se desencadena cuando el sistema no detecta las manos del usuario.</span><span class="sxs-lookup"><span data-stu-id="f033a-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="f033a-107">Esto se implementa como un componente de "enseñanza" que ayuda a guiar al usuario cuando no se ha impartido el gesto.</span><span class="sxs-lookup"><span data-stu-id="f033a-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="f033a-108">Si los usuarios no han realizado el gesto especificado durante un período, las manos se repetirán con un retraso.</span><span class="sxs-lookup"><span data-stu-id="f033a-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="f033a-109">El autocar manual se puede usar para representar presionar un botón o recoger un holograma.</span><span class="sxs-lookup"><span data-stu-id="f033a-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="f033a-110">Autocar proporcionado</span><span class="sxs-lookup"><span data-stu-id="f033a-110">Hand coach provided</span></span>

<span data-ttu-id="f033a-111">El modelo de interacción actual representa una gran variedad de controles de gestos, como el desplazamiento, la selección desplazada y la derivación cercana.</span><span class="sxs-lookup"><span data-stu-id="f033a-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="f033a-112">A continuación se muestra una lista completa de los gestos de mano existentes que se proporcionan en<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span><span class="sxs-lookup"><span data-stu-id="f033a-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f033a-113">![Ejemplo de Near Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="f033a-114">**Ejemplo de Near Selected muestra cómo seleccionar botones o cerrar objetos interactivos**</span><span class="sxs-lookup"><span data-stu-id="f033a-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-115">![Ejemplo de TAP de Air](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="f033a-116">**Ejemplo de TAP de Air: se usa para mostrar cómo seleccionar objetos que están lejos**</span><span class="sxs-lookup"><span data-stu-id="f033a-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-117">![Ejemplo de movimiento](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="f033a-118">**Ejemplo de movimiento de un objeto en el espacio: se usa para mostrar cómo mover un holograma en el espacio**</span><span class="sxs-lookup"><span data-stu-id="f033a-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-119">![Ejemplo de giro](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="f033a-120">**Ejemplo de Rotate: se usa para mostrar cómo se giran los hologramas u objetos**</span><span class="sxs-lookup"><span data-stu-id="f033a-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f033a-121">![Ejemplo de escala](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="f033a-122">**Ejemplo de escalado: se usa para mostrar cómo manipular los hologramas para ser más grandes o más pequeños**</span><span class="sxs-lookup"><span data-stu-id="f033a-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-123">![Ejemplo de Palm up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="f033a-124">**Ejemplo de Palm up: uso sugerido, para abrir menús**</span><span class="sxs-lookup"><span data-stu-id="f033a-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-125">![Ejemplo de HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="f033a-126">**La forma de voltear la mano: otra manera de abrir los menús de la mano**</span><span class="sxs-lookup"><span data-stu-id="f033a-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="f033a-127">![Ejemplo de desplazamiento](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="f033a-128">**Ejemplo de scroll: se usa para desplazarse por una lista o un documento largo**</span><span class="sxs-lookup"><span data-stu-id="f033a-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="f033a-129">Conceptos de diseño</span><span class="sxs-lookup"><span data-stu-id="f033a-129">Design concepts</span></span>

<span data-ttu-id="f033a-130">En el caso de Hololens2, diseñamos interacciones de mano basadas en instinctual y gestos de mano naturales.</span><span class="sxs-lookup"><span data-stu-id="f033a-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="f033a-131">Creemos que son intuitivos para la mayoría de los usuarios y, por lo tanto, no crean momentos de aprendizaje de gestos dedicados.</span><span class="sxs-lookup"><span data-stu-id="f033a-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="f033a-132">En su lugar, creamos el autocar de mano para ayudar a los usuarios que se bloquean o que no están familiarizados con la interacción con los hologramas. Obtenga información sobre estos gestos.</span><span class="sxs-lookup"><span data-stu-id="f033a-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="f033a-133">Sin un momento de aprendizaje, pensamos que mostrar a los usuarios cómo realizar una acción mediante la demostración sería la mejor opción.</span><span class="sxs-lookup"><span data-stu-id="f033a-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="f033a-134">En nuestros estudios, encontramos que los usuarios podían averiguar el gesto pero necesitaba un poco de orientación.</span><span class="sxs-lookup"><span data-stu-id="f033a-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="f033a-135">Si se detecta que un usuario no interactúa con un objeto durante un período, se desencadenaría un autocar de mano que demuestra la colocación correcta de la mano y el dedo.</span><span class="sxs-lookup"><span data-stu-id="f033a-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="f033a-136">Intuitivo</span><span class="sxs-lookup"><span data-stu-id="f033a-136">Intuitive</span></span>

<span data-ttu-id="f033a-137">Al animar las manos, debe ser obvio y shoudn't causar cualquier confusión.</span><span class="sxs-lookup"><span data-stu-id="f033a-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="f033a-138">La animación de las manos es una representación del gesto que está intentando llevar al usuario a entender su finalidad.</span><span class="sxs-lookup"><span data-stu-id="f033a-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="f033a-139">Por ejemplo, si desea que un usuario presione un botón, se desencadenaría una mano al presionar un botón.</span><span class="sxs-lookup"><span data-stu-id="f033a-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="f033a-140">![Ejemplo: autocar de mano cerca de TAP](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="f033a-141">*Manos del coche que muestra cómo pulsar cerca de una gema*</span><span class="sxs-lookup"><span data-stu-id="f033a-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="f033a-142">Escala de mano</span><span class="sxs-lookup"><span data-stu-id="f033a-142">Hand scale</span></span>

<span data-ttu-id="f033a-143">Se han probado varios tamaños de mano con los menús de la interfaz de usuario y se ha dado la sensación de que, si las manos eran verdaderas para el tamaño, se dio una menacing pero, si fueran demasiado pequeños, era difícil ver y entender el gesto.</span><span class="sxs-lookup"><span data-stu-id="f033a-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="f033a-144">**Voz sobre y manos**</span><span class="sxs-lookup"><span data-stu-id="f033a-144">**Voice over and hands**</span></span>

<span data-ttu-id="f033a-145">No se espera que los usuarios puedan escuchar un conjunto de instrucciones a través de la voz y ver instrucciones diferentes a través del autocar manual.</span><span class="sxs-lookup"><span data-stu-id="f033a-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="f033a-146">Ordene las instrucciones para ayudar a los usuarios a centrarse en la atención en su atención para reducir la sobrecarga organoléptica.</span><span class="sxs-lookup"><span data-stu-id="f033a-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="f033a-147">¿Puedo crear mis propios?</span><span class="sxs-lookup"><span data-stu-id="f033a-147">Can I create my own?</span></span>

<span data-ttu-id="f033a-148">Sí.</span><span class="sxs-lookup"><span data-stu-id="f033a-148">Yes!</span></span> <span data-ttu-id="f033a-149">Le recomendamos que cree su propio gesto único para su juego y contribuya de nuevo a la comunidad.</span><span class="sxs-lookup"><span data-stu-id="f033a-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="f033a-150">Hemos proporcionado un archivo Maya de una mano RIGGED que se puede usar para la aplicación que se puede descargar aquí: <a href="files/HandCoach_MRTK.zip">descargar HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="f033a-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="f033a-151">![Ejemplo de manos animadas en Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="f033a-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="f033a-152">*Ejemplo de Poking de mano animada un cuadro en Maya*</span><span class="sxs-lookup"><span data-stu-id="f033a-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="f033a-153">**Herramienta de creación recomendada**</span><span class="sxs-lookup"><span data-stu-id="f033a-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="f033a-154">Entre los artistas 3D, muchos optan por usar [Maya de Autodesk, que es capaz de usar HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar el modo en que se crean los recursos.</span><span class="sxs-lookup"><span data-stu-id="f033a-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="f033a-155">El archivo de manos proporcionado es un archivo binario Maya, por lo que se recomienda usar Maya para animar y exportar las manos.</span><span class="sxs-lookup"><span data-stu-id="f033a-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="f033a-156">Si prefiere usar otro programa 3D, aquí se muestra un <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Descargue HandCoachMRTK_FBX.zip</a> para crear su propia configuración del controlador.</span><span class="sxs-lookup"><span data-stu-id="f033a-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="f033a-157">Si se usa el archivo de la mano que se va a descargar, se recomienda reducir el tamaño de las manos en Unity a 0,6.</span><span class="sxs-lookup"><span data-stu-id="f033a-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="f033a-158">![Ejemplo: plataforma de autocar manual en Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="f033a-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="f033a-159">*Manos de RIGGED*</span><span class="sxs-lookup"><span data-stu-id="f033a-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="f033a-160">Especificaciones técnicas</span><span class="sxs-lookup"><span data-stu-id="f033a-160">Technical Specs</span></span>

*   <span data-ttu-id="f033a-161">El archivo de dos manos está disponible en formato de formato ASCII Maya</span><span class="sxs-lookup"><span data-stu-id="f033a-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="f033a-162">La mano derecha e izquierda está disponible en formato binario de Maya</span><span class="sxs-lookup"><span data-stu-id="f033a-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="f033a-163">Establezca el archivo Maya en 24 FPS</span><span class="sxs-lookup"><span data-stu-id="f033a-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="f033a-164">Dentro del archivo, hay una mano izquierda y derecha que se puede usar para los gestos de dos manos o de una sola mano.</span><span class="sxs-lookup"><span data-stu-id="f033a-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="f033a-165">La mano derecha solo será visible de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f033a-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="f033a-166">Se recomienda dejar un búfer de aproximadamente 10 fotogramas al principio y al final de los fundidos</span><span class="sxs-lookup"><span data-stu-id="f033a-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="f033a-167">Si se anima un objeto con un destino especificado, su procedimiento recomendado es animar a un cuadro predeterminado o a un valor null.</span><span class="sxs-lookup"><span data-stu-id="f033a-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="f033a-168">Si la mano está animando un objeto físico como un cuadro, el procedimiento recomendado es no animar la traducción en Maya pero esperar a animarla en Unity o en el código.</span><span class="sxs-lookup"><span data-stu-id="f033a-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="f033a-169">La animación visible debe ser de 1,5 segundos para que se transmita información significativa</span><span class="sxs-lookup"><span data-stu-id="f033a-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="f033a-170">Cuando se sienta satisfecho con la animación:</span><span class="sxs-lookup"><span data-stu-id="f033a-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="f033a-171">Seleccionar todas las uniones y los fotogramas clave de la hornea</span><span class="sxs-lookup"><span data-stu-id="f033a-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="f033a-172">Elimine los controladores, seleccione Unions and Mesh y Export como FBX</span><span class="sxs-lookup"><span data-stu-id="f033a-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="f033a-173">Si hay varias animaciones, puede usar el exportador de juegos integrado de Maya:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="f033a-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="f033a-174">Exportar desde Maya</span><span class="sxs-lookup"><span data-stu-id="f033a-174">Exporting from Maya</span></span>

<span data-ttu-id="f033a-175">Una vez que esté satisfecho con la animación</span><span class="sxs-lookup"><span data-stu-id="f033a-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="f033a-176">Seleccionar todas las uniones: seleccionar > jerarquía</span><span class="sxs-lookup"><span data-stu-id="f033a-176">Select all joints: Select > Hierarchy</span></span>

     ![Ejemplo: Ubicación del menú](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="f033a-178">Integrar la animación: cambiar a la animación > clave > animación de hornear</span><span class="sxs-lookup"><span data-stu-id="f033a-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Ejemplo: Ubicación del menú](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="f033a-180">Elimine la plataforma de pruebas de controlador: > MainR_Grp o MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="f033a-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Ejemplo: Ubicación del menú](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="f033a-182">Exportar como FBX: seleccione JNT + Mesh: file > exportar selección (cuadro de opción) > selección de exportación</span><span class="sxs-lookup"><span data-stu-id="f033a-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Ejemplo: Ubicación del menú](images/HandCoach/OptionBox.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/SelectionExport.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="f033a-186">Al exportar como FBX y incorporarse a Unity, escale las manos hacia abajo hasta 0,6.</span><span class="sxs-lookup"><span data-stu-id="f033a-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="f033a-187">Encontramos que este era el equilibrio perfecto para mostrar las manos.</span><span class="sxs-lookup"><span data-stu-id="f033a-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="f033a-188">![Ejemplo: configuración de Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="f033a-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="f033a-189">*Se encontró la configuración de Unity para HandCoach_R recurso prefabricado en MRTK*</span><span class="sxs-lookup"><span data-stu-id="f033a-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="f033a-190">Implementación de manos en el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="f033a-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="f033a-191">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="f033a-191">Best practices</span></span>
*    <span data-ttu-id="f033a-192">Se recomienda reducir verticalmente las manos en Unity en 0,6</span><span class="sxs-lookup"><span data-stu-id="f033a-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="f033a-193">Las manos se deben reproducir dos veces y, si no se completan, se repiten continuamente hasta que se completa el gesto.</span><span class="sxs-lookup"><span data-stu-id="f033a-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="f033a-194">Las manos deben repetirse dos veces para asegurarse de que el usuario tiene tiempo para registrarse y ver el gesto.</span><span class="sxs-lookup"><span data-stu-id="f033a-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="f033a-195">Las manos deben intensificar y desplazarse entre bucles.</span><span class="sxs-lookup"><span data-stu-id="f033a-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="f033a-196">Si las manos de los usuarios son visibles para las cámaras HL2, pero los usuarios no realizan la interacción necesaria, las manos aparecerán después de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="f033a-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="f033a-197">Si las manos del usuario no son visibles para las cámaras de HL2, las manos aparecerán después de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="f033a-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="f033a-198">Si se realiza un seguimiento de las manos del usuario mediante las cámaras HL2 en el medio de la animación, la animación se completará y desaparecerá.</span><span class="sxs-lookup"><span data-stu-id="f033a-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="f033a-199">Si incluye la voz sobre, se recomienda que se corresponda con el gesto de la mano.</span><span class="sxs-lookup"><span data-stu-id="f033a-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="f033a-200">Si ha aprendido las manos al menos una vez, repita solo el gesto si detecta que el usuario está atascado.</span><span class="sxs-lookup"><span data-stu-id="f033a-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="f033a-201">Si las posiciones de dedo/mano específicas son críticas, asegúrese de que los usuarios puedan ver claramente estos matices en la animación.</span><span class="sxs-lookup"><span data-stu-id="f033a-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="f033a-202">Pruebe angulación las manos para que las partes más importantes estén claramente visibles.</span><span class="sxs-lookup"><span data-stu-id="f033a-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="f033a-203">Si observa distorsión en las manos, debe ir a la configuración de calidad de Unity para aumentar la cantidad de huesos.</span><span class="sxs-lookup"><span data-stu-id="f033a-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="f033a-204">Vaya a la > Editar configuración del proyecto de Unity > calidad > otros pesos > Blend.</span><span class="sxs-lookup"><span data-stu-id="f033a-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="f033a-205">Asegúrese de que se seleccionan "4 huesos" para ver uniones suaves.</span><span class="sxs-lookup"><span data-stu-id="f033a-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Ejemplo: Ubicación del menú](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="f033a-207">Qué evitar</span><span class="sxs-lookup"><span data-stu-id="f033a-207">What to avoid</span></span>
* <span data-ttu-id="f033a-208">Escalar las manos demasiado grandes</span><span class="sxs-lookup"><span data-stu-id="f033a-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="f033a-209">colocar las manos demasiado cerca del usuario</span><span class="sxs-lookup"><span data-stu-id="f033a-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="f033a-210">Las manos solo deben impartirse una vez.</span><span class="sxs-lookup"><span data-stu-id="f033a-210">Hands should only be taught once.</span></span> <span data-ttu-id="f033a-211">La enseñanza en exceso puede causar confusión y desenredado</span><span class="sxs-lookup"><span data-stu-id="f033a-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="f033a-212">En Unity, descargue la versión más reciente de MRTK aquí:https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="f033a-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="f033a-213">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="f033a-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="f033a-214">Scripts: Consulte las instrucciones de MRTK para el <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">autocar de MRTK</a></span><span class="sxs-lookup"><span data-stu-id="f033a-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="f033a-215">Configuración por proyecto</span><span class="sxs-lookup"><span data-stu-id="f033a-215">Per- project setting</span></span>
        *   <span data-ttu-id="f033a-216">Escena establecida en UWP: puede encontrar instrucciones en el [proyecto de configuración de Unity](Configure-Unity-Project.md) para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f033a-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="f033a-217">Vea también</span><span class="sxs-lookup"><span data-stu-id="f033a-217">See also</span></span>
* [<span data-ttu-id="f033a-218">Interacción: aspectos fundamentales del</span><span class="sxs-lookup"><span data-stu-id="f033a-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f033a-219">Proceso de creación de recursos</span><span class="sxs-lookup"><span data-stu-id="f033a-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="f033a-220">Gestos</span><span class="sxs-lookup"><span data-stu-id="f033a-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f033a-221">Instalar las herramientas</span><span class="sxs-lookup"><span data-stu-id="f033a-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="f033a-222">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="f033a-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="f033a-223">Introducción al desarrollo de Unity</span><span class="sxs-lookup"><span data-stu-id="f033a-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="f033a-224">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="f033a-224">MRTK 101</span></span>](mrtk-101.md)
