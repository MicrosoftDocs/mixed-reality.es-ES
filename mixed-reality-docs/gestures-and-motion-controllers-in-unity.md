---
title: Los gestos y controladores de movimiento en Unity
description: Hay dos formas de realizar acciones en su mirada en Unity, gestos de mano y los controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: los gestos, los controladores de movimiento, unity, mirada, de entrada
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597657"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="56172-104">Los gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="56172-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="56172-105">Hay dos formas de realizar acciones en su [que mirar en Unity](gaze-in-unity.md), [gestos de mano](gestures.md) y [motion controladores](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="56172-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="56172-106">Tener acceso a los datos de ambos orígenes de entrada espacial a través de las mismas API de Unity.</span><span class="sxs-lookup"><span data-stu-id="56172-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="56172-107">Unity proporciona dos métodos principales para tener acceso a los datos espaciales de entrada para Windows Mixed Reality, común *Input.GetButton/Input.GetAxis* API que funcionan a través de varios SDK XR de Unity, y un *InteractionManager / GestureRecognizer* API específica de Windows Mixed Reality que expone el conjunto completo de datos espaciales de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="56172-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="56172-108">Tabla de asignación de botón o eje de Unity</span><span class="sxs-lookup"><span data-stu-id="56172-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="56172-109">Los identificadores de botón y de los ejes en la tabla siguiente se admiten en Administrador de entradas de Unity para los controladores de Windows Mixed Reality movimiento a través de la *Input.GetButton/GetAxis* API, mientras que la columna de "MR Windows específicos" hace referencia a propiedades disponible fuera de la *InteractionSourceState* tipo.</span><span class="sxs-lookup"><span data-stu-id="56172-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="56172-110">Cada una de estas API se describen en detalle en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="56172-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="56172-111">Las asignaciones de identificador de botón o eje para Windows Mixed Reality coinciden con el botón Oculus/eje identificadores.</span><span class="sxs-lookup"><span data-stu-id="56172-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="56172-112">Las asignaciones de identificador de botón o eje para Windows Mixed Reality se diferencian de las asignaciones de OpenVR de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="56172-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="56172-113">La asignación usa identificadores de panel táctil que son distintos de tecla de navegación, para admitir controladores con sticks analógicos y touchpads.</span><span class="sxs-lookup"><span data-stu-id="56172-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="56172-114">La asignación evita sobrecargar los identificadores para los botones de menú, dejarlos disponibles para los botones ABXY físicos de botón A y X.</span><span class="sxs-lookup"><span data-stu-id="56172-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="56172-115">Entrada</span><span class="sxs-lookup"><span data-stu-id="56172-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="56172-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API de Unity comunes</a></span><span class="sxs-lookup"><span data-stu-id="56172-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="56172-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="56172-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="56172-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API de entrada específica de Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="56172-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="56172-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="56172-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="56172-120">Parte izquierda</span><span class="sxs-lookup"><span data-stu-id="56172-120">Left hand</span></span> </th><th> <span data-ttu-id="56172-121">Mano derecha</span><span class="sxs-lookup"><span data-stu-id="56172-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="56172-122">Selección del desencadenador presionado</span><span class="sxs-lookup"><span data-stu-id="56172-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="56172-123">9 = 1.0 de eje</span><span class="sxs-lookup"><span data-stu-id="56172-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="56172-124">Eje 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="56172-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="56172-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="56172-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-126">Seleccionar valor analógico de desencadenador</span><span class="sxs-lookup"><span data-stu-id="56172-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="56172-127">Eje 9</span><span class="sxs-lookup"><span data-stu-id="56172-127">Axis 9</span></span> </td><td> <span data-ttu-id="56172-128">Eje 10</span><span class="sxs-lookup"><span data-stu-id="56172-128">Axis 10</span></span> </td><td> <span data-ttu-id="56172-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="56172-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-130">Selección del desencadenador parcialmente presionado</span><span class="sxs-lookup"><span data-stu-id="56172-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="56172-131">Botón 14 <i>(compatibilidad de controlador para juegos)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="56172-132">Botón 15 <i>(compatibilidad de controlador para juegos)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="56172-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="56172-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-134">Botón de menú presionado</span><span class="sxs-lookup"><span data-stu-id="56172-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="56172-135">Botón 6 \*</span><span class="sxs-lookup"><span data-stu-id="56172-135">Button 6\*</span></span> </td><td> <span data-ttu-id="56172-136">Botón 7 \*</span><span class="sxs-lookup"><span data-stu-id="56172-136">Button 7\*</span></span> </td><td> <span data-ttu-id="56172-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="56172-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-138">Botón de control presionado</span><span class="sxs-lookup"><span data-stu-id="56172-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="56172-139">Eje 11 = 1.0 (sin valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="56172-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="56172-140">Botón 4 <i>(compatibilidad de controlador para juegos)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="56172-141">Eje 12 = 1.0 (sin valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="56172-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="56172-142">Botón 5 <i>(compatibilidad de controlador para juegos)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="56172-143">entendido todo</span><span class="sxs-lookup"><span data-stu-id="56172-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-144">Tecla de navegación X <i>(izquierdo: -1,0, correcto: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="56172-145">Eje 1</span><span class="sxs-lookup"><span data-stu-id="56172-145">Axis 1</span></span> </td><td> <span data-ttu-id="56172-146">Eje 4</span><span class="sxs-lookup"><span data-stu-id="56172-146">Axis 4</span></span> </td><td> <span data-ttu-id="56172-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="56172-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-148">Tecla de navegación Y <i>(parte superior: de -1,0, inferior: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="56172-149">Eje 2</span><span class="sxs-lookup"><span data-stu-id="56172-149">Axis 2</span></span> </td><td> <span data-ttu-id="56172-150">Eje 5</span><span class="sxs-lookup"><span data-stu-id="56172-150">Axis 5</span></span> </td><td> <span data-ttu-id="56172-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="56172-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-152">Presiona la tecla de navegación</span><span class="sxs-lookup"><span data-stu-id="56172-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="56172-153">Botón 8</span><span class="sxs-lookup"><span data-stu-id="56172-153">Button 8</span></span> </td><td> <span data-ttu-id="56172-154">Botón 9</span><span class="sxs-lookup"><span data-stu-id="56172-154">Button 9</span></span> </td><td> <span data-ttu-id="56172-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="56172-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-156">Panel táctil X <i>(izquierdo: -1,0, correcto: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="56172-157">Axis 17\*</span><span class="sxs-lookup"><span data-stu-id="56172-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="56172-158">Axis 19\*</span><span class="sxs-lookup"><span data-stu-id="56172-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="56172-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="56172-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-160">Panel táctil Y <i>(parte superior: de -1,0, inferior: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="56172-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="56172-161">Axis 18\*</span><span class="sxs-lookup"><span data-stu-id="56172-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="56172-162">Eje 20 \*</span><span class="sxs-lookup"><span data-stu-id="56172-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="56172-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="56172-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-164">Panel táctil tocada</span><span class="sxs-lookup"><span data-stu-id="56172-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="56172-165">Botón 18 \*</span><span class="sxs-lookup"><span data-stu-id="56172-165">Button 18\*</span></span> </td><td> <span data-ttu-id="56172-166">Botón 19 \*</span><span class="sxs-lookup"><span data-stu-id="56172-166">Button 19\*</span></span> </td><td> <span data-ttu-id="56172-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="56172-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-168">Panel táctil presionada</span><span class="sxs-lookup"><span data-stu-id="56172-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="56172-169">Botón 16 \*</span><span class="sxs-lookup"><span data-stu-id="56172-169">Button 16\*</span></span> </td><td> <span data-ttu-id="56172-170">Botón 17 \*</span><span class="sxs-lookup"><span data-stu-id="56172-170">Button 17\*</span></span> </td><td> <span data-ttu-id="56172-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="56172-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-172">6GDL postura de control o la postura de puntero</span><span class="sxs-lookup"><span data-stu-id="56172-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="56172-173"><i>Control</i> suponer solo: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="56172-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="56172-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="56172-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="56172-175">Pasar <i>control</i> o <i>puntero</i> como argumento: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="56172-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="56172-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="56172-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="56172-177">Estado de seguimiento</span><span class="sxs-lookup"><span data-stu-id="56172-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="56172-178"><i>Posición precisión y el origen de riesgo de pérdida solo está disponible a través de API específica MR</i> </span><span class="sxs-lookup"><span data-stu-id="56172-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="56172-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="56172-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="56172-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="56172-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="56172-181">Estos identificadores de botón o eje difieren de los identificadores que usa Unity para OpenVR debido a conflictos en las asignaciones de la configuración de los controles, Oculus táctil y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="56172-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="56172-182">Postura de control frente a la postura señalador</span><span class="sxs-lookup"><span data-stu-id="56172-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="56172-183">Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.</span><span class="sxs-lookup"><span data-stu-id="56172-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="56172-184">Para representar mejor estos controladores, hay dos tipos de plantea puede investigar para cada origen de interacción, el **control postura** y el **puntero postura**.</span><span class="sxs-lookup"><span data-stu-id="56172-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="56172-185">Tanto el control postura y puntero postura las coordenadas se expresan por todas las API de Unity en coordenadas globales de mundo de Unity.</span><span class="sxs-lookup"><span data-stu-id="56172-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="56172-186">Postura de control</span><span class="sxs-lookup"><span data-stu-id="56172-186">Grip pose</span></span>

<span data-ttu-id="56172-187">El **control postura** representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="56172-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="56172-188">En inmersivos, la postura de control se utiliza mejor para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo.</span><span class="sxs-lookup"><span data-stu-id="56172-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="56172-189">La postura de control también se utiliza al visualizar un controlador de movimiento, como el **modelo representable** proporcionados por Windows para un movimiento controlador utiliza la postura de control como su origen y el centro de rotación.</span><span class="sxs-lookup"><span data-stu-id="56172-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="56172-190">La postura de control se define específicamente como sigue:</span><span class="sxs-lookup"><span data-stu-id="56172-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="56172-191">El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control.</span><span class="sxs-lookup"><span data-stu-id="56172-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="56172-192">En el controlador de movimiento Windows Mixed Reality, esta posición generalmente se alinea con el botón de entender.</span><span class="sxs-lookup"><span data-stu-id="56172-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="56172-193">El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)</span><span class="sxs-lookup"><span data-stu-id="56172-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="56172-194">El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.</span><span class="sxs-lookup"><span data-stu-id="56172-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="56172-195">El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.</span><span class="sxs-lookup"><span data-stu-id="56172-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="56172-196">Puede tener acceso a la postura de control a través de la API de entrada de cualquier Unity entre proveedores (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API de Windows MR específicos (*sourceState.sourcePose.TryGetPosition/Rotation*, solicitando suponen datos para el **control** nodo).</span><span class="sxs-lookup"><span data-stu-id="56172-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="56172-197">Postura de puntero</span><span class="sxs-lookup"><span data-stu-id="56172-197">Pointer pose</span></span>

<span data-ttu-id="56172-198">El **puntero postura** representa la punta del controlador que señala hacia delante.</span><span class="sxs-lookup"><span data-stu-id="56172-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="56172-199">La postura de puntero proporcionado por el sistema se utiliza mejor para raycast cuando esté **el propio modelo de controlador de representación**.</span><span class="sxs-lookup"><span data-stu-id="56172-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="56172-200">Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe señalar con un radio que es más natural para ese objeto virtual, como un radio que recorre el Cañón del modelo filo definido por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="56172-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="56172-201">Dado que los usuarios pueden ver el objeto virtual y no en el controlador físico, que apunta con el objeto virtual probablemente será más natural para aquellos que usen la aplicación.</span><span class="sxs-lookup"><span data-stu-id="56172-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="56172-202">Actualmente, está disponible en Unity solo a través de la API de Windows MR específica, la postura de puntero *sourceState.sourcePose.TryGetPosition/Rotation*, pasando *InteractionSourceNode.Pointer* como la argumento.</span><span class="sxs-lookup"><span data-stu-id="56172-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="56172-203">Estado del controlador de seguimiento</span><span class="sxs-lookup"><span data-stu-id="56172-203">Controller tracking state</span></span>

<span data-ttu-id="56172-204">Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere ninguna configuración de los sensores de seguimiento externas.</span><span class="sxs-lookup"><span data-stu-id="56172-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="56172-205">En su lugar, se realiza un seguimiento de los controladores de sensores en los auriculares en sí mismo.</span><span class="sxs-lookup"><span data-stu-id="56172-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="56172-206">Si el usuario mueve los controladores de campo de la vista de los auriculares, en la mayoría de los casos Windows seguirá deducir las posiciones de controlador y le proporciona a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="56172-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="56172-207">Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado.</span><span class="sxs-lookup"><span data-stu-id="56172-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="56172-208">En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna.</span><span class="sxs-lookup"><span data-stu-id="56172-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="56172-209">Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar normalmente aunque aproximado con una precisión de sin que el usuario lo advierta.</span><span class="sxs-lookup"><span data-stu-id="56172-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="56172-210">La mejor forma de hacerse una idea de esto es probarlo usted mismo.</span><span class="sxs-lookup"><span data-stu-id="56172-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="56172-211">Vea este vídeo con ejemplos de contenido envolvente que funciona con los controladores de movimiento a través de varios Estados de seguimiento:</span><span class="sxs-lookup"><span data-stu-id="56172-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="56172-212">Seguimiento del estado de forma explícita el razonamiento</span><span class="sxs-lookup"><span data-stu-id="56172-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="56172-213">Es posible que vaya más allá e inspeccionar las propiedades en el estado del controlador, como las aplicaciones que desea tratar las posiciones de manera diferente en función de seguimiento del estado de *SourceLossRisk* y *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="56172-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="56172-214">Estado de seguimiento</span><span class="sxs-lookup"><span data-stu-id="56172-214">Tracking state</span></span> </th><th> <span data-ttu-id="56172-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="56172-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="56172-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="56172-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="56172-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="56172-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="56172-218"><b>Alta precisión</b> </span><span class="sxs-lookup"><span data-stu-id="56172-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="56172-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="56172-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="56172-220">Alto</span><span class="sxs-lookup"><span data-stu-id="56172-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="56172-221">true</span><span class="sxs-lookup"><span data-stu-id="56172-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-222"><b>Alta precisión (corre el riesgo de perder)</b> </span><span class="sxs-lookup"><span data-stu-id="56172-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="56172-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="56172-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="56172-224">Alto</span><span class="sxs-lookup"><span data-stu-id="56172-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="56172-225">true</span><span class="sxs-lookup"><span data-stu-id="56172-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-226"><b>Precisión aproximado</b> </span><span class="sxs-lookup"><span data-stu-id="56172-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="56172-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="56172-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="56172-228">Aproximado</span><span class="sxs-lookup"><span data-stu-id="56172-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="56172-229">true</span><span class="sxs-lookup"><span data-stu-id="56172-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="56172-230"><b>Ninguna posición</b> </span><span class="sxs-lookup"><span data-stu-id="56172-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="56172-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="56172-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="56172-232">Aproximado</span><span class="sxs-lookup"><span data-stu-id="56172-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="56172-233">falso</span><span class="sxs-lookup"><span data-stu-id="56172-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="56172-234">Estos Estados de seguimiento del controlador de movimiento se definen como sigue:</span><span class="sxs-lookup"><span data-stu-id="56172-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="56172-235">**Alta precisión:** Mientras el controlador de movimiento está dentro de campo de la vista de los auriculares, generalmente entregará las posiciones de alta precisión, en función de seguimiento visual.</span><span class="sxs-lookup"><span data-stu-id="56172-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="56172-236">Tenga en cuenta que un controlador de movimiento que momentáneamente deja el campo de visión o se oculta temporalmente de los sensores de auriculares (por ejemplo, por otro lado del usuario) continuará devolviendo plantea de alta precisión durante un breve período, en función de seguimiento inercial del controlador Sí.</span><span class="sxs-lookup"><span data-stu-id="56172-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="56172-237">**Alta precisión (corre el riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde de campo de la vista de los auriculares, los auriculares pronto podrá realizar un seguimiento visual de la posición del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="56172-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="56172-238">La aplicación conoce cuando el controlador ha alcanzado este límite FOV viendo el **SourceLossRisk** llegar a 1.0.</span><span class="sxs-lookup"><span data-stu-id="56172-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="56172-239">En ese momento, la aplicación puede optar por pausar los gestos de controlador que requieren un flujo constante de plantea muy alta calidad.</span><span class="sxs-lookup"><span data-stu-id="56172-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="56172-240">**Precisión aproximado:** Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado.</span><span class="sxs-lookup"><span data-stu-id="56172-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="56172-241">En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna.</span><span class="sxs-lookup"><span data-stu-id="56172-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="56172-242">Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar como while normal con una precisión aproximada de sin que el usuario lo advierta.</span><span class="sxs-lookup"><span data-stu-id="56172-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="56172-243">Pueden elegir sentido esta lista de aplicaciones con requisitos de entrada más **alta** precisión a **aproximado** precisión inspeccionando el **PositionAccuracy** propiedad, para ejemplo para otorgar al usuario un hitbox más generosa en destinos fuera de la pantalla durante este tiempo.</span><span class="sxs-lookup"><span data-stu-id="56172-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="56172-244">**Ninguna posición:** Mientras que el controlador puede operar en una precisión aproximada durante mucho tiempo, en ocasiones, el sistema sepa que incluso una posición bloqueada de cuerpo no es significativa en este momento.</span><span class="sxs-lookup"><span data-stu-id="56172-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="56172-245">Por ejemplo, un controlador que ha estado encendido solo es posible que nunca se han observado visualmente, o un usuario puede dejar un controlador que, a continuación, se recoge por otra persona.</span><span class="sxs-lookup"><span data-stu-id="56172-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="56172-246">En esos momentos, el sistema no proporcionará cualquier posición a la aplicación, y *TryGetPosition* devolverá false.</span><span class="sxs-lookup"><span data-stu-id="56172-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="56172-247">API de Unity comunes (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="56172-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="56172-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="56172-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="56172-249">**Tipos**: *Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="56172-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="56172-250">Unity usa actualmente su general *Input.GetButton/Input.GetAxis* API para exponer la entrada [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidos las manos y los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="56172-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="56172-251">Si su aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento a través de varios SDK XR, incluidos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="56172-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="56172-252">Al obtener el estado presionado de un botón lógico</span><span class="sxs-lookup"><span data-stu-id="56172-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="56172-253">Para usar la entrada de Unity general API, normalmente empezará por inserción de botones y los ejes a los nombres lógicos en el [Unity entrada Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), enlace un botón o eje identificadores a cada nombre.</span><span class="sxs-lookup"><span data-stu-id="56172-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="56172-254">A continuación, puede escribir código que hace referencia a dicho nombre lógico de botón o eje.</span><span class="sxs-lookup"><span data-stu-id="56172-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="56172-255">Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción de envío, vaya a **Editar > configuración del proyecto > entrada** dentro de Unity y expanda las propiedades de la sección de envío en los ejes.</span><span class="sxs-lookup"><span data-stu-id="56172-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="56172-256">Cambiar el **botón positivo** o **Alt positivo botón** propiedad que se va a leer **botón joystick 14**, similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="56172-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="56172-257">![InputManager de Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="56172-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="56172-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="56172-258">*Unity InputManager*</span></span>

<span data-ttu-id="56172-259">A continuación, puede comprobar el script para la acción de envío mediante *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="56172-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="56172-260">Puede agregar botones más lógicos cambiando el **tamaño** propiedad bajo **ejes**.</span><span class="sxs-lookup"><span data-stu-id="56172-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="56172-261">Obtener estado presionado de un botón físico directamente</span><span class="sxs-lookup"><span data-stu-id="56172-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="56172-262">También puede acceder botones por su nombre completo nombre, con *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="56172-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="56172-263">Obtener una mano o postura del controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="56172-264">Puede tener acceso a la posición y rotación del controlador, mediante *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="56172-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="56172-265">Tenga en cuenta que esto representa la postura de control del controlador (donde el usuario mantiene el controlador), lo que resulta útil para representar una Espada o presión en la mano del usuario o un modelo de la propia controladora.</span><span class="sxs-lookup"><span data-stu-id="56172-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="56172-266">Tenga en cuenta que puede diferir la relación entre la postura de este control y la postura de puntero (donde está señalando a la punta del controlador) en todos los controladores.</span><span class="sxs-lookup"><span data-stu-id="56172-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="56172-267">En este momento, tener acceso a la postura del puntero del controlador sólo es posible a través de la entrada MR específica API que se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="56172-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="56172-268">API específicas de Windows (XR. WSA. Entrada)</span><span class="sxs-lookup"><span data-stu-id="56172-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="56172-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="56172-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="56172-270">**Tipos**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="56172-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="56172-271">Para obtener información más detallada acerca de la entrada de la mano de Windows Mixed Reality (para HoloLens) y los controladores de movimiento, puede elegir usar las API de entrada espacial específicas de Windows bajo la *UnityEngine.XR.WSA.Input* espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="56172-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="56172-272">Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite indicar a las manos y los controladores de distancia.</span><span class="sxs-lookup"><span data-stu-id="56172-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="56172-273">Sondear el estado de las manos y los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="56172-274">Se puede sondear para el estado de este fotograma para cada origen (controlador de mano o movimiento) de interacción con el *GetCurrentReading* método.</span><span class="sxs-lookup"><span data-stu-id="56172-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="56172-275">Cada *InteractionSourceState* obtendrá back representa un origen de interacción en el momento actual.</span><span class="sxs-lookup"><span data-stu-id="56172-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="56172-276">El *InteractionSourceState* expone información como:</span><span class="sxs-lookup"><span data-stu-id="56172-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="56172-277">Que [tipos de pulsaciones](motion-controllers.md) se producen (Select/menú/comprensión o panel táctil o tecla de navegación)</span><span class="sxs-lookup"><span data-stu-id="56172-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="56172-278">Otros datos específicos de los controladores de movimiento, tales el panel táctil o de tecla de navegación coordenadas XY y estado modificada</span><span class="sxs-lookup"><span data-stu-id="56172-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="56172-279">El InteractionSourceKind saber si el origen es una mano o un controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="56172-280">Sondear plantea representación predicho de avance</span><span class="sxs-lookup"><span data-stu-id="56172-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="56172-281">Al sondear en busca de datos de origen de la interacción de las manos y los controladores, la puede causar que obtendrá es plantea predicho de avance por el momento en el tiempo cuando photons de este fotograma llegarán a la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="56172-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="56172-282">Estos plantea predicho de avance resultan especialmente útiles para **representación** el controlador o un retenidos objeto cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="56172-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="56172-283">Si están destinadas a la acción de presionar una determinada o versión con el controlador, que será más precisos, si usa el evento histórico API descritas a continuación.</span><span class="sxs-lookup"><span data-stu-id="56172-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="56172-284">También puede obtener la postura principal predicho de avance para este marco actual.</span><span class="sxs-lookup"><span data-stu-id="56172-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="56172-285">Igual que con la postura de origen, esto es útil para **representación** un cursor, aunque destinado a un determinado presione o versión serán más preciso, si usa el evento histórico API descritas a continuación.</span><span class="sxs-lookup"><span data-stu-id="56172-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="56172-286">Control de eventos del origen de interacción</span><span class="sxs-lookup"><span data-stu-id="56172-286">Handling interaction source events</span></span>

<span data-ttu-id="56172-287">Para controlar los eventos de entrada cuando se produzcan con sus datos precisos postura históricos, puede controlar eventos del origen de interacción en lugar de sondeo.</span><span class="sxs-lookup"><span data-stu-id="56172-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="56172-288">Para controlar los eventos de origen de interacción:</span><span class="sxs-lookup"><span data-stu-id="56172-288">To handle interaction source events:</span></span>
* <span data-ttu-id="56172-289">Registrarse para una *InteractionManager* evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="56172-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="56172-290">Para cada tipo de evento de interacción que le interesen, deberá suscribirse a él.</span><span class="sxs-lookup"><span data-stu-id="56172-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="56172-291">Controle el evento.</span><span class="sxs-lookup"><span data-stu-id="56172-291">Handle the event.</span></span> <span data-ttu-id="56172-292">Una vez que se ha suscrito a un evento de interacción, obtendrá la devolución de llamada cuando corresponda.</span><span class="sxs-lookup"><span data-stu-id="56172-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="56172-293">En el *SourcePressed* ejemplo, se trata de una vez se ha detectado el origen y antes de que se publicó o se pierde.</span><span class="sxs-lookup"><span data-stu-id="56172-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="56172-294">Cómo detener un evento de control</span><span class="sxs-lookup"><span data-stu-id="56172-294">How to stop handling an event</span></span>

<span data-ttu-id="56172-295">Debe dejar de controlar un evento cuando ya no está interesado en el evento o se destruya el objeto que se ha suscrito al evento.</span><span class="sxs-lookup"><span data-stu-id="56172-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="56172-296">Para dejar de controlar el evento, anular la suscripción del evento.</span><span class="sxs-lookup"><span data-stu-id="56172-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="56172-297">Lista de eventos del origen de interacción</span><span class="sxs-lookup"><span data-stu-id="56172-297">List of interaction source events</span></span>

<span data-ttu-id="56172-298">Los eventos de origen de la interacción disponible son:</span><span class="sxs-lookup"><span data-stu-id="56172-298">The available interaction source events are:</span></span>
* <span data-ttu-id="56172-299">*InteractionSourceDetected* (origen se convierte en activado)</span><span class="sxs-lookup"><span data-stu-id="56172-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="56172-300">*InteractionSourceLost* (pasa a estar inactiva)</span><span class="sxs-lookup"><span data-stu-id="56172-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="56172-301">*InteractionSourcePressed* (tap, presionar el botón o "Select" dijeron)</span><span class="sxs-lookup"><span data-stu-id="56172-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="56172-302">*InteractionSourceReleased* (final de una derivación, el botón o al final de "Select" dijeron)</span><span class="sxs-lookup"><span data-stu-id="56172-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="56172-303">*InteractionSourceUpdated* (mueva o cambie algún estado de lo contrario)</span><span class="sxs-lookup"><span data-stu-id="56172-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="56172-304">Eventos para histórico plantea destinatarios que coinciden con la máxima precisión con una presione o versión</span><span class="sxs-lookup"><span data-stu-id="56172-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="56172-305">Las API de sondeos que se ha descrito anteriormente, asigne a la aplicación puede causar predicho de avance.</span><span class="sxs-lookup"><span data-stu-id="56172-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="56172-306">Mientras esos plantea predicho es más adecuada para representar un objeto de dispositivo de mano virtual o el controlador, puede causar futuras no es óptimas para destinatarios por dos razones fundamentales:</span><span class="sxs-lookup"><span data-stu-id="56172-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="56172-307">Cuando el usuario presiona un botón en un controlador, puede haber unos 20 ms de latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la prensa.</span><span class="sxs-lookup"><span data-stu-id="56172-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="56172-308">A continuación, si está utilizando una postura predicho de avance, existe son aplicables para el tiempo cuando photons del fotograma actual llegará a la vista del usuario de destino otro 10-20ms de predicción hacia delante.</span><span class="sxs-lookup"><span data-stu-id="56172-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="56172-309">Esto significa que sondeo le ofrece una postura de origen o head suponer que es el 30-40 MS hacia delante desde donde principal y las manos del usuario realmente atrás cuando estaban ha ocurrido la prensa o versión.</span><span class="sxs-lookup"><span data-stu-id="56172-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="56172-310">Para la entrada de la mano de HoloLens, aunque no hay ningún retraso transmisiones inalámbricas, hay un retraso de procesamiento similares para detectar la prensa.</span><span class="sxs-lookup"><span data-stu-id="56172-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="56172-311">Identificar con precisión según la intención del usuario original pulsación de una mano o el controlador, debe usar la postura de origen históricos o postura principal desde que *InteractionSourcePressed* o *InteractionSourceReleased* evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="56172-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="56172-312">Puede tener como destino un presione o liberar con datos históricos postura de head del usuario o su controlador de:</span><span class="sxs-lookup"><span data-stu-id="56172-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="56172-313">Se ha producido la postura principal en el momento cuando se presiona un gesto o un controlador, que puede utilizarse para **destinadas a** para determinar cuál fue el usuario [gazing](gaze.md) en:</span><span class="sxs-lookup"><span data-stu-id="56172-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="56172-314">Se ha producido la postura de origen en el momento cuando se presiona un controlador de movimiento, que puede utilizarse para **destinatarios** para determinar lo que el usuario señalando el controlador en.</span><span class="sxs-lookup"><span data-stu-id="56172-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="56172-315">Este será el estado del controlador que experimentó la prensa.</span><span class="sxs-lookup"><span data-stu-id="56172-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="56172-316">Si está representando el propio controlador, puede solicitar la postura de puntero, en lugar de la postura de control, debe grabar el rayo destinatarios de lo que el usuario tendrá en cuenta la punta natural del que representa el controlador:</span><span class="sxs-lookup"><span data-stu-id="56172-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="56172-317">Ejemplo de controladores de eventos</span><span class="sxs-lookup"><span data-stu-id="56172-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="56172-318">Gesto de compuesto de alto nivel API (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="56172-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="56172-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="56172-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="56172-320">**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="56172-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="56172-321">La aplicación también puede reconocer gestos compuestos de mayor nivel para los gestos de suspensión, la manipulación y la navegación espacial de orígenes de entrada, Tap.</span><span class="sxs-lookup"><span data-stu-id="56172-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="56172-322">Puede reconocer estos gestos compuestos entre ambos [manos](gestures.md) y [controladores de movimiento](motion-controllers.md) utilizando el GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="56172-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="56172-323">Cada evento de gestos en el GestureRecognizer proporciona el SourceKind para la entrada, así como el rayo principal destinatarios en el momento del evento.</span><span class="sxs-lookup"><span data-stu-id="56172-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="56172-324">Algunos eventos proporcionan información específica de contexto adicional.</span><span class="sxs-lookup"><span data-stu-id="56172-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="56172-325">Hay solo unos pasos necesarios para capturar los gestos de un reconocedor de gestos:</span><span class="sxs-lookup"><span data-stu-id="56172-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="56172-326">Crear un nuevo reconocedor de gestos</span><span class="sxs-lookup"><span data-stu-id="56172-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="56172-327">Especifique qué gestos para inspeccionar</span><span class="sxs-lookup"><span data-stu-id="56172-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="56172-328">Suscripción a eventos de los gestos</span><span class="sxs-lookup"><span data-stu-id="56172-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="56172-329">Iniciar la captura de gestos</span><span class="sxs-lookup"><span data-stu-id="56172-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="56172-330">Crear un nuevo reconocedor de gestos</span><span class="sxs-lookup"><span data-stu-id="56172-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="56172-331">Para usar el *GestureRecognizer*, debe haber creado un *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="56172-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="56172-332">Especifique qué gestos para inspeccionar</span><span class="sxs-lookup"><span data-stu-id="56172-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="56172-333">Especifique qué gestos que esté interesado a través de *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="56172-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="56172-334">Suscripción a eventos de los gestos</span><span class="sxs-lookup"><span data-stu-id="56172-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="56172-335">Suscribirse a eventos para los gestos que esté interesado.</span><span class="sxs-lookup"><span data-stu-id="56172-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="56172-336">Los gestos de navegación y manipulación son mutuamente excluyentes en una instancia de un *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="56172-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="56172-337">Iniciar la captura de gestos</span><span class="sxs-lookup"><span data-stu-id="56172-337">Start capturing gestures</span></span>

<span data-ttu-id="56172-338">De forma predeterminada, un *GestureRecognizer* no supervisa entrada hasta *StartCapturingGestures()* se llama.</span><span class="sxs-lookup"><span data-stu-id="56172-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="56172-339">Es posible que se puede generar un evento de gesto después *StopCapturingGestures()* se llama si la entrada se realizó antes del fotograma donde *StopCapturingGestures()* se procesó.</span><span class="sxs-lookup"><span data-stu-id="56172-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="56172-340">El *GestureRecognizer* recordarán si fue activado o desactivado durante el fotograma anterior en el que el gesto producido realmente y por lo que es confiable para iniciar y Detener supervisión de gesto según mirada de este marco destino.</span><span class="sxs-lookup"><span data-stu-id="56172-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="56172-341">Detener la captura de gestos</span><span class="sxs-lookup"><span data-stu-id="56172-341">Stop capturing gestures</span></span>

<span data-ttu-id="56172-342">Para detener el reconocimiento de gestos:</span><span class="sxs-lookup"><span data-stu-id="56172-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="56172-343">Quitar un reconocedor de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="56172-344">Recuerde que debe cancelar la suscripción a eventos suscritos antes de destruir un *GestureRecognizer* objeto.</span><span class="sxs-lookup"><span data-stu-id="56172-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="56172-345">Representación del modelo de controlador de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="56172-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="56172-346">![Teleportation y el modelo de controlador de movimiento](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="56172-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="56172-347">*Teleportation y el modelo de controlador de movimiento*</span><span class="sxs-lookup"><span data-stu-id="56172-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="56172-348">Para representar los controladores de movimiento en la aplicación que coinciden con los controladores de físicos a los usuarios mantienen y explicar como se presionan los botones distintos, puede usar el **MotionController prefabricado** en el [Kit de herramientas de realidad mixta ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="56172-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="56172-349">Este recurso prefabricado carga dinámicamente el modelo glTF correcto en tiempo de ejecución desde el controlador del controlador de movimiento instalados del sistema.</span><span class="sxs-lookup"><span data-stu-id="56172-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="56172-350">Es importante cargar estos modelos de forma dinámica en lugar de importarlos de forma manual en el editor, para que la aplicación mostrará modelos 3D físicamente precisos para los controladores actuales y futuros de los usuarios pueden tener.</span><span class="sxs-lookup"><span data-stu-id="56172-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="56172-351">Siga el [Introducción](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instrucciones para descargar el Kit de herramientas de realidad mixta y agregarlo a su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="56172-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="56172-352">Si reemplaza la cámara con la *MixedRealityCameraParent* prefabricado como parte de los pasos de introducción, estará listo para continuar.</span><span class="sxs-lookup"><span data-stu-id="56172-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="56172-353">Ese recurso prefabricado incluye representación de controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="56172-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="56172-354">De lo contrario, agregue *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* en su escena en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="56172-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="56172-355">Desea agregar que prefabricado como elemento secundario de cualquier objeto primario se usa para mover la cámara en torno a cuando la teleports usuario dentro de la escena, para que los controladores vienen junto con el usuario.</span><span class="sxs-lookup"><span data-stu-id="56172-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="56172-356">Si la aplicación no implica teleporting, simplemente agregue el prefabricado verá en la raíz de la escena.</span><span class="sxs-lookup"><span data-stu-id="56172-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="56172-357">Producir objetos</span><span class="sxs-lookup"><span data-stu-id="56172-357">Throwing objects</span></span>

<span data-ttu-id="56172-358">A continuación, generar objetos en realidad virtual es un problema más difícil al principio pareciera.</span><span class="sxs-lookup"><span data-stu-id="56172-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="56172-359">Al igual que con interacciones más físicamente en función, cuando se lanza en juego actúa de forma inesperada, es evidente de inmediato e inmersión se interrumpe.</span><span class="sxs-lookup"><span data-stu-id="56172-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="56172-360">Hemos pasado algún tiempo a pensar en profundidad acerca de cómo representan un comportamiento produce físicamente correcto y han inventado algunas instrucciones, habilitadas a través de las actualizaciones de nuestra plataforma, que nos gustaría compartir con usted.</span><span class="sxs-lookup"><span data-stu-id="56172-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="56172-361">Puede encontrar un ejemplo de cómo se recomienda implementar producir [aquí](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="56172-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="56172-362">Este ejemplo sigue estas cuatro directrices:</span><span class="sxs-lookup"><span data-stu-id="56172-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="56172-363">**Usar el controlador *velocity* en lugar de posición**.</span><span class="sxs-lookup"><span data-stu-id="56172-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="56172-364">En la actualización de noviembre de Windows, se introdujo un cambio de comportamiento cuando se encuentra en la ['' aproximado '' estado de seguimiento posicionales](motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="56172-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="56172-365">En este estado, información de progreso sobre el controlador seguirá notificará siempre que creemos que es de alta precisión, que a menudo es más larga de posición permanece alta precisión.</span><span class="sxs-lookup"><span data-stu-id="56172-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="56172-366">**Incorporar la *velocidad angular* del controlador de**.</span><span class="sxs-lookup"><span data-stu-id="56172-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="56172-367">Esta lógica se incluye en el `throwing.cs` de archivos en el `GetThrownObjectVelAngVel` métodos estáticos, dentro del paquete vinculado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="56172-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="56172-368">Como se conserva la velocidad angular, el objeto iniciado debe mantener la misma velocidad angular que tenía en el momento del lanzamiento: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="56172-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="56172-369">Como es probable no en el origen de la postura de control, es probable que tenga una velocidad diferente, a continuación, el controlador de en el marco de referencia del usuario del centro de masa del objeto iniciado.</span><span class="sxs-lookup"><span data-stu-id="56172-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="56172-370">La parte de la velocidad del objeto que aporta de esta manera es el progreso tangencial instantáneo del centro de masa del objeto se produce en torno al origen de controlador.</span><span class="sxs-lookup"><span data-stu-id="56172-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="56172-371">Esta velocidad tangencial: es el producto cruzado de la velocidad angular del controlador con el vector que representa la distancia entre el origen del controlador y del centro de masa del objeto iniciado.</span><span class="sxs-lookup"><span data-stu-id="56172-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="56172-372">La velocidad total del objeto se produce, por tanto, es la suma de la velocidad del controlador y este progreso tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="56172-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="56172-373">**Preste mucha atención a la *tiempo* en el que se aplique la velocidad**.</span><span class="sxs-lookup"><span data-stu-id="56172-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="56172-374">Cuando se presiona un botón, se pueden tardar hasta 20 ms para ese evento se propagan a través de Bluetooth en el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="56172-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="56172-375">Esto significa que si el sondeo para un cambio de estado del controlador de presionado para no presionado o viceversa, será realmente la información de la postura de controlador que obtiene con él por delante de este cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="56172-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="56172-376">Además, la postura de controlador presentada por nuestra API de sondeo al día se prevé para reflejar una postura es probable que en el momento que se mostrará el marco que podría ser más de 20 ms, a continuación, en el futuro.</span><span class="sxs-lookup"><span data-stu-id="56172-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="56172-377">Esto es bueno para *representación* mantiene los objetos, pero nuestro problema de tiempo para los compuestos *destinatarios* el objeto calculamos la trayectoria para el momento en que el usuario libera su throw.</span><span class="sxs-lookup"><span data-stu-id="56172-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="56172-378">Afortunadamente, con la actualización de noviembre, cuando un evento de Unity como *InteractionSourcePressed* o *InteractionSourceReleased* se envía el estado incluye los datos históricos postura desde nuevo cuando el botón era realmente presionado o publicadas.</span><span class="sxs-lookup"><span data-stu-id="56172-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="56172-379">Para obtener la representación más precisa de controlador y el controlador destinatarios durante produce, debe usar correctamente sondeo y eventos, según corresponda:</span><span class="sxs-lookup"><span data-stu-id="56172-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="56172-380">Para **representación controlador** cada fotograma, la aplicación debe colocar el controlador *GameObject* en el controlador predicho de avance suponer tiempo de photon del marco actual.</span><span class="sxs-lookup"><span data-stu-id="56172-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="56172-381">Obtener estos datos desde Unity, como las API de sondeos *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="56172-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="56172-382">Para **controlador destinatarios** tras un presione o versión, la aplicación debe raycast y calcular las trayectorias en función de la postura de controlador históricos para ese evento presione o versión.</span><span class="sxs-lookup"><span data-stu-id="56172-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="56172-383">Extraer estos datos de eventos de Unity API, como  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="56172-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="56172-384">**Utilice la postura de control**.</span><span class="sxs-lookup"><span data-stu-id="56172-384">**Use the grip pose**.</span></span> <span data-ttu-id="56172-385">Velocidad angular y la velocidad se notifican en relación con la postura de control, no un puntero postura.</span><span class="sxs-lookup"><span data-stu-id="56172-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="56172-386">Iniciando seguirá aumentando con futuras actualizaciones de Windows y se puede esperar encontrar más información al respecto aquí.</span><span class="sxs-lookup"><span data-stu-id="56172-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="56172-387">Acelere el desarrollo con el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="56172-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="56172-388">Hay dos escenas de ejemplo sobre InputManager y MotionController en Unity.</span><span class="sxs-lookup"><span data-stu-id="56172-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="56172-389">A través de estos escenas, pueden aprender cómo usar InputManager del MRTK y tener acceso a datos controlan los eventos de los botones del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="56172-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="56172-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="56172-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="56172-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="56172-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="56172-392">Archivo Léame de los detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="56172-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="56172-393">![Segundo plano de ejemplo de entrada en MRTK](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="56172-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="56172-394">*Segundo plano de ejemplo de entrada en MRTK*</span><span class="sxs-lookup"><span data-stu-id="56172-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="56172-395">Programa de instalación automática de escenas</span><span class="sxs-lookup"><span data-stu-id="56172-395">Automatic scene setup</span></span>

<span data-ttu-id="56172-396">Al importar [MRTK publicar paquetes de Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonar el proyecto desde el [repositorio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), va a buscar un nuevo menú 'Kit de herramientas de realidad mixta' en Unity.</span><span class="sxs-lookup"><span data-stu-id="56172-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="56172-397">En el menú "Configurar", verá el menú 'Aplicar configuración de escena de Mixed Reality'.</span><span class="sxs-lookup"><span data-stu-id="56172-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="56172-398">Al hacer clic en él, quita la cámara de forma predeterminada y agrega los componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), y [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="56172-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="56172-399">![Menú MRTK para la instalación de la escena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="56172-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="56172-400">*Menú MRTK para la instalación de la escena*</span><span class="sxs-lookup"><span data-stu-id="56172-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="56172-401">![Programa de instalación automática de escenas en MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="56172-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="56172-402">*Programa de instalación automática de escenas en MRTK*</span><span class="sxs-lookup"><span data-stu-id="56172-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="56172-403">MixedRealityCamera prefabricado</span><span class="sxs-lookup"><span data-stu-id="56172-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="56172-404">Puede agregar también manualmente desde el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="56172-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="56172-405">Puede encontrar estos componentes como prefabricados.</span><span class="sxs-lookup"><span data-stu-id="56172-405">You can find these components as prefabs.</span></span> <span data-ttu-id="56172-406">Al buscar **MixedRealityCamera**, podrá ver dos prefabricados cámara diferente.</span><span class="sxs-lookup"><span data-stu-id="56172-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="56172-407">La diferencia es que **MixedRealityCamera** es la cámara solo prefabricado, mientras que **MixedRealityCameraParent** incluye componentes adicionales para el inmersivos como Teleportation, movimiento Controlador y límites.</span><span class="sxs-lookup"><span data-stu-id="56172-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="56172-408">![Cámara prefabricados en MRTK](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="56172-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="56172-409">*Cámara prefabricados en MRTK*</span><span class="sxs-lookup"><span data-stu-id="56172-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="56172-410">**MixedRealtyCamera** admite HoloLens y auriculares envolventes.</span><span class="sxs-lookup"><span data-stu-id="56172-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="56172-411">Detecta el tipo de dispositivo y optimiza las propiedades como borrar las marcas y Skybox.</span><span class="sxs-lookup"><span data-stu-id="56172-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="56172-412">A continuación, encontrará algunas de las propiedades útiles que puede personalizar como Cursor personalizado, los modelos de controlador de movimiento y el suelo.</span><span class="sxs-lookup"><span data-stu-id="56172-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="56172-413">![Propiedades para el controlador de movimiento de Cursor y Floor](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="56172-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="56172-414">*Propiedades para el controlador de movimiento de Cursor y Floor*</span><span class="sxs-lookup"><span data-stu-id="56172-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="56172-415">Seguir tutoriales</span><span class="sxs-lookup"><span data-stu-id="56172-415">Follow along with tutorials</span></span>

<span data-ttu-id="56172-416">Tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en la Academia de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="56172-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="56172-417">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="56172-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="56172-418">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="56172-419">[![Entrada MR 213 - controlador de movimiento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="56172-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="56172-420">*Entrada MR 213 - controlador de movimiento*</span><span class="sxs-lookup"><span data-stu-id="56172-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="56172-421">Vea también</span><span class="sxs-lookup"><span data-stu-id="56172-421">See also</span></span>

* [<span data-ttu-id="56172-422">Gestos</span><span class="sxs-lookup"><span data-stu-id="56172-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="56172-423">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="56172-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="56172-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="56172-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="56172-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="56172-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="56172-426">InteractionInputSource.cs en MixedRealityToolkit Unity</span><span class="sxs-lookup"><span data-stu-id="56172-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
