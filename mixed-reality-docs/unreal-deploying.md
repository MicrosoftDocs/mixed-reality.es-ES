---
title: Implementación en el dispositivo en Unreal
description: Guía para la implementación en el dispositivo de un equipo inreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, equipo, documentación
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408183"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="b2777-104">Implementación en el dispositivo en Unreal</span><span class="sxs-lookup"><span data-stu-id="b2777-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="b2777-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="b2777-105">Overview</span></span>
<span data-ttu-id="b2777-106">Hay dos maneras de implementar una aplicación no real en HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="b2777-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span> 
* <span data-ttu-id="b2777-107">Directamente desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="b2777-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="b2777-108">Como un paquete cargado a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b2777-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="b2777-109">Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](using-the-windows-device-portal.md) para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="b2777-109">Both options require you to set up your HoloLens to use the [device portal](using-the-windows-device-portal.md) for development.</span></span> 

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="b2777-110">Implementación en el dispositivo desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="b2777-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="b2777-111">Haga clic en la flecha desplegable situada junto al botón **iniciar** .</span><span class="sxs-lookup"><span data-stu-id="b2777-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="b2777-112">Inicialmente, la opción de dispositivo HoloLens estará atenuada.</span><span class="sxs-lookup"><span data-stu-id="b2777-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="b2777-114">Abra el **Device Manager**.</span><span class="sxs-lookup"><span data-stu-id="b2777-114">Open the **Device Manager**.</span></span> <span data-ttu-id="b2777-115">Tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2777-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="b2777-116">Expanda la sección **Agregar un dispositivo** que no está en la lista.</span><span class="sxs-lookup"><span data-stu-id="b2777-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="b2777-117">Seleccione **HoloLens** como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b2777-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="b2777-118">Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2777-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="b2777-119">Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB).</span><span class="sxs-lookup"><span data-stu-id="b2777-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="b2777-120">Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2777-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="b2777-121">Presione **Agregar** y cierre el administrador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2777-121">Hit **Add** and close the device manager.</span></span> 
    * <span data-ttu-id="b2777-122">En el caso de un error (por ejemplo, una dirección incorrecta, un nombre de usuario o una contraseña), se imprimirá un mensaje en el registro de salida.</span><span class="sxs-lookup"><span data-stu-id="b2777-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="b2777-124">Haga clic en la flecha desplegable situada junto al botón **Launch (iniciar** ) de nuevo; esta vez debería ver el dispositivo HoloLens que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="b2777-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="b2777-125">Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b2777-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span> 

>[!NOTE]
><span data-ttu-id="b2777-126">La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="b2777-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="b2777-127">No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo).</span><span class="sxs-lookup"><span data-stu-id="b2777-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="b2777-128">De lo contrario, se producirá un error de compilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="b2777-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="b2777-129">Implementación en el dispositivo a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b2777-129">Deploying to device via device portal</span></span>

<span data-ttu-id="b2777-130">Puede encontrar instrucciones detalladas sobre cómo [empaquetar e implementar una aplicación](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) en la última sección del introducción con una serie de tutoriales inreal.</span><span class="sxs-lookup"><span data-stu-id="b2777-130">You can find detailed instructions on [packaging and deploying an app](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>
