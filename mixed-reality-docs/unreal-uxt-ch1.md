---
title: 1. Introducción
description: Parte 1 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840134"
---
# <a name="1-getting-started"></a><span data-ttu-id="f8d54-104">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="f8d54-104">1. Getting started</span></span>

<span data-ttu-id="f8d54-105">Este es un tutorial detallado que te mostrará cómo compilar una aplicación de ajedrez interactiva para HoloLens 2 con Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="f8d54-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="f8d54-106">También aprenderás a usar el complemento UX Tools de Mixed Reality Toolkit para Unreal para acelerar el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f8d54-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f8d54-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f8d54-107">Prerequisites</span></span>

* <span data-ttu-id="f8d54-108">Windows 10 1809 o posterior</span><span class="sxs-lookup"><span data-stu-id="f8d54-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="f8d54-109">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="f8d54-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f8d54-110">Unreal Engine 4.25 o posterior</span><span class="sxs-lookup"><span data-stu-id="f8d54-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="f8d54-111">Un dispositivo Microsoft HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode) o un emulador</span><span class="sxs-lookup"><span data-stu-id="f8d54-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="f8d54-112">Visual Studio 2019 (con las cargas de trabajo y los componentes siguientes)</span><span class="sxs-lookup"><span data-stu-id="f8d54-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="f8d54-113">Instalación de Visual Studio 2019, las cargas de trabajo y los componentes</span><span class="sxs-lookup"><span data-stu-id="f8d54-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="f8d54-114">Actualiza a la versión más reciente de Visual Studio 2019 o instálala</span><span class="sxs-lookup"><span data-stu-id="f8d54-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="f8d54-115">Descargar Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="f8d54-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="f8d54-116">Instala las cargas de trabajo siguientes:</span><span class="sxs-lookup"><span data-stu-id="f8d54-116">Install the following workloads:</span></span>
* <span data-ttu-id="f8d54-117">Desarrollo de escritorio con C++</span><span class="sxs-lookup"><span data-stu-id="f8d54-117">Desktop development with C++</span></span>
* <span data-ttu-id="f8d54-118">Desarrollo de escritorio de .NET</span><span class="sxs-lookup"><span data-stu-id="f8d54-118">.NET desktop development</span></span>
* <span data-ttu-id="f8d54-119">Desarrollo con la Plataforma universal de Windows</span><span class="sxs-lookup"><span data-stu-id="f8d54-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="f8d54-120">Instala los siguientes componentes individuales:</span><span class="sxs-lookup"><span data-stu-id="f8d54-120">Install the following individual components:</span></span>
* <span data-ttu-id="f8d54-121">Compiladores, herramientas de compilación y entornos en tiempo de ejecución > herramientas de desarrollo para ARM64 en C++ de MSVC v142 - VS 2019 (versión más reciente)</span><span class="sxs-lookup"><span data-stu-id="f8d54-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="f8d54-122">Sección siguiente: 2. Inicialización del proyecto y primera aplicación</span><span class="sxs-lookup"><span data-stu-id="f8d54-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)