---
title: 'Tutoriales sobre Azure Spatial Anchors: 1. Introducción'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376557"
---
# <a name="1-introduction"></a><span data-ttu-id="971d9-105">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="971d9-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="971d9-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="971d9-106">Overview</span></span>

<span data-ttu-id="971d9-107">Le damos la bienvenida a los tutoriales sobre Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="971d9-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="971d9-108">En esta serie de tutoriales, aprenderá los aspectos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) y cómo anclar una experiencia de realidad mixta completa en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="971d9-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="971d9-109">También aprenderá a implementar el proyecto en iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="971d9-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="971d9-110">Tutoriales de esta serie:</span><span class="sxs-lookup"><span data-stu-id="971d9-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="971d9-111">Introducción</span><span class="sxs-lookup"><span data-stu-id="971d9-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="971d9-112">Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="971d9-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="971d9-113">Almacenamiento, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="971d9-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="971d9-114">Visualización de comentarios de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="971d9-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="971d9-115">Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="971d9-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="971d9-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="971d9-116">Objectives</span></span>

* <span data-ttu-id="971d9-117">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="971d9-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="971d9-118">Aprender a lograr la alineación espacial entre sesiones de una aplicación</span><span class="sxs-lookup"><span data-stu-id="971d9-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="971d9-119">Aprender a lograr la alineación espacial entre varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="971d9-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="971d9-120">Aprender a preparar, compilar e implementar el proyecto en iOS y Android</span><span class="sxs-lookup"><span data-stu-id="971d9-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="971d9-121">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="971d9-121">Prerequisites</span></span>

* <span data-ttu-id="971d9-122">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="971d9-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="971d9-123">Windows 10, SDK 10.0.18362.0 o una versión posterior</span><span class="sxs-lookup"><span data-stu-id="971d9-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="971d9-124">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="971d9-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="971d9-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="971d9-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="971d9-126">Haber completado la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="971d9-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="971d9-127">Haber finalizado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK.</span><span class="sxs-lookup"><span data-stu-id="971d9-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="971d9-128">Haber completado la serie de [tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) o contar con experiencia anterior en la creación de una cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="971d9-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="971d9-129">Si va a realizar la implementación en Android y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="971d9-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="971d9-130">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="971d9-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="971d9-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de Android agregado</span><span class="sxs-lookup"><span data-stu-id="971d9-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="971d9-132">Si va a realizar la implementación en iOS y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="971d9-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="971d9-133">Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="971d9-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="971d9-134">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS</span><span class="sxs-lookup"><span data-stu-id="971d9-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="971d9-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de iOS agregado</span><span class="sxs-lookup"><span data-stu-id="971d9-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="971d9-136">La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="971d9-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="971d9-137">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="971d9-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="971d9-138">Esta sustituye los requisitos de versión de Unity descritos en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="971d9-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="971d9-139">Tutorial siguiente: 2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="971d9-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
