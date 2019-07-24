---
title: Conexión a Wi-Fi en HoloLens
description: Instrucciones sobre cómo conectarse a Internet inalámbrica con HoloLens y cómo identificar la dirección IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, inalámbrica, Internet, IP, dirección IP
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670111"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="29f32-104">Conexión a Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f32-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="29f32-105">HoloLens contiene una radio Wi-Fi compatible con AC 802.11 y 2x2.</span><span class="sxs-lookup"><span data-stu-id="29f32-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="29f32-106">Conectar HoloLens a una red Wi-Fi es similar a conectar un dispositivo móvil o de escritorio de Windows 10 a una red Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="29f32-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Configuración de Wi-Fi de HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="29f32-108">Conexión a una red Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f32-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="29f32-109">[Floración](gestures.md#bloom) al menú **Inicio** .</span><span class="sxs-lookup"><span data-stu-id="29f32-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="29f32-110">Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="29f32-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="29f32-111">La aplicación de **configuración** se colocará automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="29f32-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="29f32-112">Seleccione **red & Internet**.</span><span class="sxs-lookup"><span data-stu-id="29f32-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="29f32-113">Asegúrate de que la conexión Wi-Fi está activada.</span><span class="sxs-lookup"><span data-stu-id="29f32-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="29f32-114">Seleccione una red Wi-Fi en la lista.</span><span class="sxs-lookup"><span data-stu-id="29f32-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="29f32-115">Escriba la contraseña de red Wi-Fi (si es necesario).</span><span class="sxs-lookup"><span data-stu-id="29f32-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="29f32-116">Deshabilitación de Wi-Fi en HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f32-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="29f32-117">Uso de la aplicación de configuración en HoloLens</span><span class="sxs-lookup"><span data-stu-id="29f32-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="29f32-118">[Floración](gestures.md#bloom) al menú **Inicio** .</span><span class="sxs-lookup"><span data-stu-id="29f32-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="29f32-119">Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="29f32-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="29f32-120">La aplicación de **configuración** se colocará automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="29f32-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="29f32-121">Seleccione **red & Internet**.</span><span class="sxs-lookup"><span data-stu-id="29f32-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="29f32-122">Seleccione el conmutador de control deslizante de Wi-Fi para moverlo a la posición "desactivado".</span><span class="sxs-lookup"><span data-stu-id="29f32-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="29f32-123">Se desactivarán los componentes de RF del radio Wi-Fi y se deshabilitará toda la funcionalidad de Wi-Fi en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="29f32-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="29f32-124">HoloLens no podrá cargar automáticamente los [espacios](environment-considerations-for-hololens.md#WiFi fingerprint considerations) cuando la radio Wi-Fi esté deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="29f32-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="29f32-125">Mueva el control deslizante a la posición "activado" para activar la radio Wi-Fi y restaurar la funcionalidad de Wi-Fi en Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="29f32-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="29f32-126">El estado de radio Wi-Fi seleccionado ("activado" de "desactivado") se conservará en los reinicios.</span><span class="sxs-lookup"><span data-stu-id="29f32-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="29f32-127">Cómo confirmar que está conectado a una red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="29f32-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="29f32-128">[Floración](gestures.md#bloom) para abrir el menú **Inicio** .</span><span class="sxs-lookup"><span data-stu-id="29f32-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="29f32-129">Fíjese en la parte superior izquierda del menú Inicio para ver el estado de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="29f32-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="29f32-130">Se mostrará el estado de Wi-Fi y el SSID de la red conectada.</span><span class="sxs-lookup"><span data-stu-id="29f32-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="29f32-131">Identificación de la dirección IP de HoloLens en la red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="29f32-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="29f32-132">Uso de la aplicación de configuración</span><span class="sxs-lookup"><span data-stu-id="29f32-132">Using the Settings app</span></span>

1. <span data-ttu-id="29f32-133">[Floración](gestures.md#bloom) al menú **Inicio** .</span><span class="sxs-lookup"><span data-stu-id="29f32-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="29f32-134">Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="29f32-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="29f32-135">La aplicación de **configuración** se colocará automáticamente delante de usted.</span><span class="sxs-lookup"><span data-stu-id="29f32-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="29f32-136">Seleccione **red & Internet**.</span><span class="sxs-lookup"><span data-stu-id="29f32-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="29f32-137">Desplácese hacia abajo hasta la lista de redes Wi-Fi disponibles y seleccione **propiedades de hardware**.</span><span class="sxs-lookup"><span data-stu-id="29f32-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Propiedades de hardware en configuración de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="29f32-139">La dirección IP se mostrará junto a **dirección IPv4**.</span><span class="sxs-lookup"><span data-stu-id="29f32-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="29f32-140">Uso de Cortana</span><span class="sxs-lookup"><span data-stu-id="29f32-140">Using Cortana</span></span>

<span data-ttu-id="29f32-141">Supongamos*que "Hola Cortana, ¿cuál es mi dirección IP?* "</span><span class="sxs-lookup"><span data-stu-id="29f32-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="29f32-142">y Cortana mostrará y leerá su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="29f32-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="29f32-143">Uso del portal de dispositivos de Windows</span><span class="sxs-lookup"><span data-stu-id="29f32-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="29f32-144">Abra el [portal de dispositivos](using-the-windows-device-portal.md#networking) en un explorador Web en su PC.</span><span class="sxs-lookup"><span data-stu-id="29f32-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="29f32-145">Vaya a la sección **redes** .</span><span class="sxs-lookup"><span data-stu-id="29f32-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="29f32-146">La dirección IP y otra información de red se mostrarán allí.</span><span class="sxs-lookup"><span data-stu-id="29f32-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="29f32-147">Este método permite copiar y pegar fácilmente la dirección IP en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="29f32-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
