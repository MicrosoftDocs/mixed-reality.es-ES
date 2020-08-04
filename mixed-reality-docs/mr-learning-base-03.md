---
title: 'Tutoriales de introducción: 3. Configuración de los perfiles de MRTK'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376647"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="ee1d5-105">3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="ee1d5-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="ee1d5-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="ee1d5-106">Overview</span></span>

<span data-ttu-id="ee1d5-107">En este tutorial, aprenderá a personalizar y configurar los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="ee1d5-108">En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="ee1d5-109">Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="ee1d5-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ee1d5-110">Objectives</span></span>

* <span data-ttu-id="ee1d5-111">Obtener información sobre cómo personalizar y configurar los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="ee1d5-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="ee1d5-112">Ocultar la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="ee1d5-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="ee1d5-113">Cambio de la opción de visualización del reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="ee1d5-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="ee1d5-114">Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="ee1d5-115">Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="ee1d5-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="ee1d5-116">Habilitar el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="ee1d5-117">Clonar el perfil del sistema de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="ee1d5-118">Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="ee1d5-119">Cambiar la visibilidad de la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="ee1d5-120">De forma predeterminada, los perfiles de MRTK no son editables.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="ee1d5-121">Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="ee1d5-122">Hay varias capas anidadas de perfiles.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="ee1d5-123">Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="ee1d5-124">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="ee1d5-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="ee1d5-125">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="ee1d5-126">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="ee1d5-127">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, cambie el valor del perfil de configuración **MixedRealityToolkit** a **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="ee1d5-129">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="ee1d5-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="ee1d5-131">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_HoloLens2ConfigurationProfiley_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="ee1d5-133">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="ee1d5-135">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="ee1d5-136">Recuerde guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="ee1d5-137">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="ee1d5-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="ee1d5-138">En la ventana Jerarquía, seleccione el objeto **MixedRealityToolkit**; después, en la ventana Inspector, seleccione la pestaña **Spatial Awareness** (Reconocimiento espacial) y, a continuación, active la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="ee1d5-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="ee1d5-140">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="ee1d5-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="ee1d5-141">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="ee1d5-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="ee1d5-143">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="ee1d5-145">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="ee1d5-147">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="ee1d5-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="ee1d5-148">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="ee1d5-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="ee1d5-150">En la ventana para clonar perfil, escriba un **Nombre de perfil** adecuado; por ejemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_. A continuación, haga clic en el botón **Clonar** para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="ee1d5-152">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="ee1d5-154">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="ee1d5-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="ee1d5-155">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambie **Opción de visualización** a **Oclusión** para que la malla de asignación espacial sea invisible y funcional a la vez:</span><span class="sxs-lookup"><span data-stu-id="ee1d5-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="ee1d5-157">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="ee1d5-158">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="ee1d5-159">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="ee1d5-160">Como puede ver, para personalizar la configuración de MRTK, debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="ee1d5-161">Dado que los perfiles predeterminados no son editables, siempre los tendrá como referencias si quiere revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="ee1d5-162">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puede consultar la [guía de configuración de perfiles de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="ee1d5-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="ee1d5-163">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ee1d5-163">Congratulations</span></span>

<span data-ttu-id="ee1d5-164">En este tutorial, aprendió a clonar, personalizar y configurar los perfiles de MRTK y sus opciones.</span><span class="sxs-lookup"><span data-stu-id="ee1d5-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="ee1d5-165">Tutorial siguiente: 4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="ee1d5-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
