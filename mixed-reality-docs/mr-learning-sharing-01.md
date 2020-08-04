---
title: 'Tutoriales sobre las funcionalidades multiusuario: 1. Introducción'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376355"
---
# <a name="1-introduction"></a><span data-ttu-id="f4cd1-105">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="f4cd1-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="f4cd1-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="f4cd1-106">Overview</span></span>

<span data-ttu-id="f4cd1-107">¡Le damos la bienvenida a los tutoriales sobre las funcionalidades multiusuario!</span><span class="sxs-lookup"><span data-stu-id="f4cd1-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="f4cd1-108">A lo largo de esta serie de tutoriales aprenderá los aspectos básicos de la creación de una experiencia multiusuario mediante <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="f4cd1-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="f4cd1-109">PUN es una de las diversas opciones de redes disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="f4cd1-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="f4cd1-110">Tutoriales de esta serie:</span><span class="sxs-lookup"><span data-stu-id="f4cd1-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="f4cd1-111">Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="f4cd1-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="f4cd1-112">Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="f4cd1-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="f4cd1-113">Uso compartido de movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="f4cd1-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="f4cd1-114">Integración de Azure Spatial Anchors en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="f4cd1-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="f4cd1-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f4cd1-115">Objectives</span></span>

* <span data-ttu-id="f4cd1-116">Aprender a crear una aplicación de PUN y conectarla al proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="f4cd1-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="f4cd1-117">Aprender a conectar varios usuarios en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="f4cd1-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="f4cd1-118">Aprender a compartir los movimientos de objetos con otros usuarios</span><span class="sxs-lookup"><span data-stu-id="f4cd1-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="f4cd1-119">Aprender a lograr la alineación espacial entre varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="f4cd1-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4cd1-120">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f4cd1-120">Prerequisites</span></span>

* <span data-ttu-id="f4cd1-121">Un equipo Windows 10 configurado con las [herramientas adecuadas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="f4cd1-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f4cd1-122">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="f4cd1-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f4cd1-123">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="f4cd1-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f4cd1-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="f4cd1-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="f4cd1-125">Haber completado la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="f4cd1-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="f4cd1-126">Haber completado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK</span><span class="sxs-lookup"><span data-stu-id="f4cd1-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="f4cd1-127">Haber completado la serie de [tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) o contar con experiencia previa en la creación de una cuenta de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f4cd1-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="f4cd1-128">Si va a realizar la implementación en Android y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="f4cd1-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="f4cd1-129">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="f4cd1-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="f4cd1-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de Android agregado</span><span class="sxs-lookup"><span data-stu-id="f4cd1-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="f4cd1-131">Si va a realizar la implementación en iOS y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="f4cd1-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="f4cd1-132">Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="f4cd1-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="f4cd1-133">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS</span><span class="sxs-lookup"><span data-stu-id="f4cd1-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="f4cd1-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de iOS agregado</span><span class="sxs-lookup"><span data-stu-id="f4cd1-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="f4cd1-135">La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="f4cd1-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="f4cd1-136">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="f4cd1-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="f4cd1-137">Esta sustituye los requisitos de versión de Unity descritos en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f4cd1-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="f4cd1-138">Tutorial siguiente: 2. Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="f4cd1-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
