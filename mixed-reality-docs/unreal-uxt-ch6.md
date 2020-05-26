---
title: 6. Empaquetado e implementación en el dispositivo o emulador
description: Parte 6 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519976"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="c58d2-104">6. Empaquetado e implementación en el dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="c58d2-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="c58d2-105">En esta sección se te orientará a lo largo de los pasos necesarios para preparar la aplicación para que se ejecute en un emulador o dispositivo de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c58d2-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="c58d2-106">Si tienes un dispositivo, puedes transmitir en secuencias desde el equipo al dispositivo o empaquetar la aplicación para ejecutarla directamente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c58d2-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="c58d2-107">Si no tienes ningún dispositivo, tendrás que empaquetar la aplicación para que se ejecute en el emulador.</span><span class="sxs-lookup"><span data-stu-id="c58d2-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="c58d2-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c58d2-108">Objectives</span></span>

* <span data-ttu-id="c58d2-109">[Solo dispositivo] Transmitir en secuencias la aplicación a HoloLens 2 mediante la comunicación remota con la aplicación holográfica</span><span class="sxs-lookup"><span data-stu-id="c58d2-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="c58d2-110">Empaquetar e implementar la aplicación en un dispositivo o emulador de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c58d2-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="c58d2-111">[Solo dispositivo] Transmitir en secuencias</span><span class="sxs-lookup"><span data-stu-id="c58d2-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="c58d2-112">Instala **Holographic Remoting Player** desde Microsoft Store en HoloLens 2 y ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c58d2-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="c58d2-113">Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="c58d2-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="c58d2-114">En la sección Holographic Remoting, activa la casilla para habilitar la comunicación remota y reinicia el editor.</span><span class="sxs-lookup"><span data-stu-id="c58d2-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="c58d2-115">Escribe la dirección IP del dispositivo y haz clic en Connect (Conectar).</span><span class="sxs-lookup"><span data-stu-id="c58d2-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="c58d2-116">Una vez conectado, en el editor de UE4, haz clic en la flecha desplegable situada a la derecha del botón Play (Jugar) y selecciona VR Preview (Vista previa de VR).</span><span class="sxs-lookup"><span data-stu-id="c58d2-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="c58d2-117">Empaquetar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="c58d2-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="c58d2-118">Si esta es la primera vez que empaquetas una aplicación de Unreal para HoloLens, deberás descargar los archivos auxiliares desde el iniciador de Epic.</span><span class="sxs-lookup"><span data-stu-id="c58d2-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="c58d2-119">Para ello, ve a la pestaña **Biblioteca** en el iniciador de Epic Games.</span><span class="sxs-lookup"><span data-stu-id="c58d2-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="c58d2-120">Selecciona la flecha desplegable situada junto a **Iniciar** y selecciona **Opciones**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="c58d2-121">En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="c58d2-122">![Configuración del proyecto: Descripción](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="c58d2-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="c58d2-123">Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="c58d2-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="c58d2-124">En **Project > Description > About > Project Name** (Proyecto > Descripción > Acerca de > Nombre del proyecto), asigna un nombre al proyecto.</span><span class="sxs-lookup"><span data-stu-id="c58d2-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="c58d2-125">En **Project > Description > Publisher > Company Distinguished Name** (Proyecto > Descripción > Editor > Empresa > Nombre distintivo), escribe “CN={NOMBRE DE EMPRESA}”.</span><span class="sxs-lookup"><span data-stu-id="c58d2-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="c58d2-126">Si dejas alguno de estos campos en blanco, se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="c58d2-126">Leaving either of these fields blank will result in an error.</span></span> 

![Configuración del proyecto: descripción](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="c58d2-128">En **Platforms > HoloLens** (Plataformas > HoloLens), elige Emulation (Emulación) o Device (Dispositivo), en función del destino al que quieras orientarte.</span><span class="sxs-lookup"><span data-stu-id="c58d2-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="c58d2-129">En la sección **Packaging** (Empaquetado), haz clic junto a **Signing Certificate** (Certificado de firma), haz clic en el botón **Generate new** (Generar nuevo) para generar un nuevo certificado de firma.</span><span class="sxs-lookup"><span data-stu-id="c58d2-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="c58d2-130">Vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="c58d2-130">Return to the Main window.</span></span>

![Configuración del proyecto - Plataformas - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="c58d2-132">Ve a **File > Package Project** (Archivo > Proyecto de paquete) y selecciona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="c58d2-133">Crea una nueva carpeta en la que guardar el paquete y haz clic en **Select Folder** (Seleccionar carpeta).</span><span class="sxs-lookup"><span data-stu-id="c58d2-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="c58d2-134">Una vez empaquetada la aplicación, abre el **Portal de dispositivos de Windows**, ve a **Vistas > Aplicaciones** y busca la sección **Implementar aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="c58d2-135">Haz clic en **Examinar...** y desplázate hasta el archivo **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="c58d2-136">Haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="c58d2-136">Click **Open**.</span></span> 

    * <span data-ttu-id="c58d2-137">Si es la primera vez que instalas la aplicación en el dispositivo, activa la casilla situada junto a **Allow me to select framework packages** (Permitirme seleccionar paquetes de marcos).</span><span class="sxs-lookup"><span data-stu-id="c58d2-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="c58d2-138">En el siguiente cuadro de diálogo, incluye el archivo appx VCLibs adecuado (arm64 para el dispositivo, x64 para el emulador).</span><span class="sxs-lookup"><span data-stu-id="c58d2-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="c58d2-139">Haz clic en **Instalar**</span><span class="sxs-lookup"><span data-stu-id="c58d2-139">Click **Install**</span></span>

<span data-ttu-id="c58d2-140">Enhorabuena por haber finalizado este tutorial.</span><span class="sxs-lookup"><span data-stu-id="c58d2-140">Congratulations on finishing this tutorial!</span></span>  