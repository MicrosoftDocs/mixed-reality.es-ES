---
title: Conectarse a Wi-Fi en HoloLens
description: Instrucciones sobre cómo conectarse a internet inalámbrica con HoloLens y cómo identificar la dirección IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, conexiones inalámbricas, internet, ip, dirección ip
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670111"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="799c7-104">Conectarse a Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="799c7-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="799c7-105">HoloLens contiene un 802. 11ac-capaz, 2 x 2 radio de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="799c7-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="799c7-106">La conexión de HoloLens a una red Wi-Fi es parecido a conectar un dispositivo Windows 10 escritorio o móvil a una red Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="799c7-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Configuración de Wi-Fi de HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="799c7-108">Conectarse a una red Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="799c7-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="799c7-109">[Bloom](gestures.md#bloom) a la **iniciar** menú.</span><span class="sxs-lookup"><span data-stu-id="799c7-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="799c7-110">Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="799c7-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="799c7-111">El **configuración** aplicación será coloca automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="799c7-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="799c7-112">Seleccione **red e Internet**.</span><span class="sxs-lookup"><span data-stu-id="799c7-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="799c7-113">Asegúrate de que la conexión Wi-Fi está activada.</span><span class="sxs-lookup"><span data-stu-id="799c7-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="799c7-114">Seleccione una red Wi-Fi de la lista.</span><span class="sxs-lookup"><span data-stu-id="799c7-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="799c7-115">Escriba la contraseña de la red Wi-Fi (si es necesario).</span><span class="sxs-lookup"><span data-stu-id="799c7-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="799c7-116">Deshabilitación de Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="799c7-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="799c7-117">Uso de la aplicación de configuración en HoloLens</span><span class="sxs-lookup"><span data-stu-id="799c7-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="799c7-118">[Bloom](gestures.md#bloom) a la **iniciar** menú.</span><span class="sxs-lookup"><span data-stu-id="799c7-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="799c7-119">Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="799c7-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="799c7-120">El **configuración** aplicación será coloca automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="799c7-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="799c7-121">Seleccione **red e Internet**.</span><span class="sxs-lookup"><span data-stu-id="799c7-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="799c7-122">Seleccione el control deslizante Wi-Fi para moverla a la posición "Off".</span><span class="sxs-lookup"><span data-stu-id="799c7-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="799c7-123">Esto se desactivará los componentes de RF de la radio de Wi-Fi y deshabilitar toda la funcionalidad de Wi-Fi en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="799c7-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="799c7-124">HoloLens no podrá cargar automáticamente su [espacios](environment-considerations-for-hololens.md#WiFi fingerprint considerations) cuando está deshabilitado el radio de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="799c7-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="799c7-125">Mueva el control deslizante a la posición "On" para activar el radio de Wi-Fi y restaurar la funcionalidad de Wi-Fi en Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="799c7-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="799c7-126">El estado seleccionado de radio de Wi-Fi ("On" de "Off") se conservan entre reinicios.</span><span class="sxs-lookup"><span data-stu-id="799c7-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="799c7-127">Cómo confirmar que está conectados a una red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="799c7-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="799c7-128">[Bloom](gestures.md#bloom) para que aparezca el **iniciar** menú.</span><span class="sxs-lookup"><span data-stu-id="799c7-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="799c7-129">En la parte superior izquierda del menú Inicio para el estado de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="799c7-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="799c7-130">Se mostrará el estado de Wi-Fi y el SSID de la red conectada.</span><span class="sxs-lookup"><span data-stu-id="799c7-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="799c7-131">Que identifica la dirección IP de su HoloLens en la red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="799c7-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="799c7-132">Uso de la aplicación de configuración</span><span class="sxs-lookup"><span data-stu-id="799c7-132">Using the Settings app</span></span>

1. <span data-ttu-id="799c7-133">[Bloom](gestures.md#bloom) a la **iniciar** menú.</span><span class="sxs-lookup"><span data-stu-id="799c7-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="799c7-134">Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="799c7-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="799c7-135">El **configuración** aplicación será coloca automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="799c7-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="799c7-136">Seleccione **red e Internet**.</span><span class="sxs-lookup"><span data-stu-id="799c7-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="799c7-137">Desplácese hacia abajo hasta debajo de la lista de redes Wi-Fi disponibles y seleccione **propiedades de Hardware**.</span><span class="sxs-lookup"><span data-stu-id="799c7-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Propiedades de hardware en las opciones de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="799c7-139">Se mostrará junto a la dirección IP **dirección IPv4**.</span><span class="sxs-lookup"><span data-stu-id="799c7-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="799c7-140">Uso de Cortana</span><span class="sxs-lookup"><span data-stu-id="799c7-140">Using Cortana</span></span>

<span data-ttu-id="799c7-141">Por ejemplo "*Hola Cortana, ¿cuál es mi dirección IP?*"</span><span class="sxs-lookup"><span data-stu-id="799c7-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="799c7-142">y Cortana mostrará y leer la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="799c7-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="799c7-143">Uso de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="799c7-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="799c7-144">Abra el [portal dispositivos](using-the-windows-device-portal.md#networking) en un explorador web en su PC.</span><span class="sxs-lookup"><span data-stu-id="799c7-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="799c7-145">Navegue hasta la **redes** sección.</span><span class="sxs-lookup"><span data-stu-id="799c7-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="799c7-146">Allí se mostrará la dirección IP y otra información de red.</span><span class="sxs-lookup"><span data-stu-id="799c7-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="799c7-147">Este método permite fácil copiar y pegar de la dirección IP en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="799c7-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
