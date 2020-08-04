---
title: 'Tutoriales de introducción: 8. Uso del seguimiento ocular'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376607"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="a1e23-105">8. Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="a1e23-105">8. Using eye-tracking</span></span>

## <a name="overview"></a><span data-ttu-id="a1e23-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="a1e23-106">Overview</span></span>

<span data-ttu-id="a1e23-107">En este tutorial, aprenderá a habilitar el seguimiento ocular para HoloLens 2 y agregará el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="a1e23-107">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="a1e23-108">Si también va a implementar este proyecto en HoloLens (primera generación), tenga en cuenta que el seguimiento ocular solo es compatible con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a1e23-108">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="a1e23-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a1e23-109">Objectives</span></span>

* <span data-ttu-id="a1e23-110">Aprender a habilitar el seguimiento ocular para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a1e23-110">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="a1e23-111">Aprender a usar el seguimiento ocular para desencadenar la acción</span><span class="sxs-lookup"><span data-stu-id="a1e23-111">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="a1e23-112">Asegurarse de que está habilitada la funcionalidad de entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="a1e23-112">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="a1e23-113">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="a1e23-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a1e23-115">La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="a1e23-115">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="a1e23-116">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="a1e23-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="a1e23-117">Habilitar la mirada con los ojos en el proveedor de mirada</span><span class="sxs-lookup"><span data-stu-id="a1e23-117">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="a1e23-118">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, seleccione la pestaña MixedRealityToolkit > **Input** (Entrada) y realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="a1e23-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="a1e23-119">Clone el perfil **DefaultHoloLens2InputSystemProfile** y asígnele un nombre adecuado; por ejemplo, _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="a1e23-119">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="a1e23-120">Expanda la sección **Punteros**.</span><span class="sxs-lookup"><span data-stu-id="a1e23-120">Expand the **Pointers** section</span></span>
* <span data-ttu-id="a1e23-121">Clone el perfil **DefaultMixedRealityPointerProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="a1e23-121">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="a1e23-122">Busque la sección **Gaze Settings** (Configuración de mirada) y active la casilla **Is Eye Tracking Enabled** (Está habilitado el seguimiento ocular).</span><span class="sxs-lookup"><span data-stu-id="a1e23-122">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a1e23-124">Para recibir un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="a1e23-124">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="a1e23-125">Habilitar el seguimiento ocular simulado para el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="a1e23-125">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="a1e23-126">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana Inspector, navegue hasta la pestaña **Entrada** y, a continuación:</span><span class="sxs-lookup"><span data-stu-id="a1e23-126">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="a1e23-127">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada)  > **Input Simulation Service** (Servicio de simulación de entrada).</span><span class="sxs-lookup"><span data-stu-id="a1e23-127">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="a1e23-128">Clone el perfil **DefaultMixedRealityInputSimulationProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="a1e23-128">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="a1e23-129">Busque la sección **Eye Simulation** (Simulación ocular) y active la casilla **Simulate Eye Position** (Simular posición ocular).</span><span class="sxs-lookup"><span data-stu-id="a1e23-129">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="a1e23-131">Agregar seguimiento ocular a los objetos</span><span class="sxs-lookup"><span data-stu-id="a1e23-131">Adding eye-tracking to objects</span></span>

<span data-ttu-id="a1e23-132">En la ventana Jerarquía, expanda el objeto RoverExplorer > **Botones** y, a continuación, para cada uno de los tres objetos de botón secundarios, expanda y seleccione el objeto SeeItSayItLabel > **TextMeshPro**:</span><span class="sxs-lookup"><span data-stu-id="a1e23-132">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="a1e23-134">Con los tres objetos TextMeshPro todavía seleccionados, en la ventana Inspector, use el botón **Agregar componente** para agregar los siguientes componentes a todos los objetos seleccionados:</span><span class="sxs-lookup"><span data-stu-id="a1e23-134">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="a1e23-135">Componente **Colisionador de cuadro**</span><span class="sxs-lookup"><span data-stu-id="a1e23-135">**Box Collider** component</span></span>
* <span data-ttu-id="a1e23-136">Componente **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="a1e23-136">**EyeTrackingTarget** component</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="a1e23-138">En la ventana Jerarquía, seleccione el objeto **Hints** (Sugerencias) > SeeItSayItLabel > **TextMeshPro** y, a continuación, configure el componente **EyeTrackingTarget** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a1e23-138">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="a1e23-139">En la sección de eventos **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="a1e23-139">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="a1e23-140">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="a1e23-140">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="a1e23-141">Asigne el propio objeto, es decir, el mismo objeto **TextMeshPro**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a1e23-141">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="a1e23-142">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a1e23-142">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="a1e23-143">Establezca el argumento en **0,06** para aumentar el tamaño de fuente actual de 0,04 por el 50 %.</span><span class="sxs-lookup"><span data-stu-id="a1e23-143">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="a1e23-144">En la sección de eventos **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="a1e23-144">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="a1e23-145">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="a1e23-145">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="a1e23-146">Asigne el propio objeto, es decir, el mismo objeto **TextMeshPro**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="a1e23-146">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="a1e23-147">En la lista desplegable **Ninguna función**, seleccione **TextMeshPro** > **float fontSize** (fontSize tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="a1e23-147">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="a1e23-148">Establezca el argumento en **0,04** para restablecer el tamaño de fuente en 0,04.</span><span class="sxs-lookup"><span data-stu-id="a1e23-148">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="a1e23-150">**Repita** este paso para los objetos **Explode** (Explosión) > SeeItSayItLabel > **TextMeshPro** y **Reset** (Restablecer) > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="a1e23-150">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="a1e23-151">Ahora, si entra en el Modo de Juego y, a continuación, mantiene presionado el botón secundario del mouse mientras lo mueve hasta que la mirada entre en contacto con una de las etiquetas, verá cómo la fuente aumenta su tamaño en un 50 % y se restablece su tamaño original al apartar la mirada:</span><span class="sxs-lookup"><span data-stu-id="a1e23-151">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="a1e23-153">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a1e23-153">Congratulations</span></span>

<span data-ttu-id="a1e23-154">En este tutorial, aprendió a habilitar el seguimiento ocular para HoloLens 2 y cómo agregar el seguimiento ocular a los objetos para desencadenar acciones cuando el usuario los mire.</span><span class="sxs-lookup"><span data-stu-id="a1e23-154">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

[<span data-ttu-id="a1e23-155">Tutorial siguiente: 9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="a1e23-155">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)