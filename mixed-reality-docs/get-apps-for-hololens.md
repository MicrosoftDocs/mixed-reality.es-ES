---
title: Obtener aplicaciones para HoloLens
description: Describe la instalación de aplicaciones para HoloLens, tanto mediante el Microsoft Store como la carga de prueba.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: instalación de prueba, carga lateral, carga lateral, almacén, UWP, aplicación, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522563"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="d3299-104">Obtener aplicaciones para HoloLens</span><span class="sxs-lookup"><span data-stu-id="d3299-104">Get apps for HoloLens</span></span>

<span data-ttu-id="d3299-105">Como dispositivo Windows 10, HoloLens es compatible con muchas aplicaciones UWP existentes desde la tienda de aplicaciones, así como con nuevas aplicaciones compiladas específicamente para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d3299-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="d3299-106">Además, es posible que incluso desee [desarrollar](development-overview.md) e instalar sus propias aplicaciones o sus amigos.</span><span class="sxs-lookup"><span data-stu-id="d3299-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="d3299-107">Instalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="d3299-107">Installing Apps</span></span>

<span data-ttu-id="d3299-108">Hay tres maneras de instalar aplicaciones nuevas en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d3299-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="d3299-109">El método principal será instalar nuevas aplicaciones desde la tienda Windows.</span><span class="sxs-lookup"><span data-stu-id="d3299-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="d3299-110">Sin embargo, también puede instalar sus propias aplicaciones con el portal de dispositivos o mediante su implementación desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3299-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="d3299-111">Desde el Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="d3299-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="d3299-112">Realice un gesto de [floración](gestures.md#bloom) para abrir el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="d3299-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d3299-113">Seleccione la aplicación de la tienda y, después, pulse para colocar este icono en su mundo.</span><span class="sxs-lookup"><span data-stu-id="d3299-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="d3299-114">Una vez que se abra la aplicación de la tienda, use la barra de búsqueda para buscar cualquier aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="d3299-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="d3299-115">Seleccione **obtener** o **instalar** en la página de la aplicación (es posible que se requiera una compra).</span><span class="sxs-lookup"><span data-stu-id="d3299-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="d3299-116">Instalación de un paquete de aplicación con el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="d3299-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="d3299-117">Establezca una conexión desde el [portal de dispositivos](using-the-windows-device-portal.md) a la HoloLens de destino.</span><span class="sxs-lookup"><span data-stu-id="d3299-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="d3299-118">Vaya a la página **aplicaciones** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="d3299-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="d3299-119">En **paquete** de la aplicación, busque el archivo. appx asociado a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d3299-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="d3299-120">Asegúrese de hacer referencia a los archivos de certificado y de dependencia asociados.</span><span class="sxs-lookup"><span data-stu-id="d3299-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="d3299-121">Haga clic en **ir**.</span><span class="sxs-lookup"><span data-stu-id="d3299-121">Click **Go**.</span></span>

<span data-ttu-id="d3299-122">![Instalación del formulario de aplicación en Windows Device portal en Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="d3299-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="d3299-123">Uso del portal de dispositivos de Windows para instalar una aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="d3299-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="d3299-124">Implementación desde Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="d3299-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="d3299-125">Abra la solución de Visual Studio de la aplicación (archivo. sln).</span><span class="sxs-lookup"><span data-stu-id="d3299-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="d3299-126">Abra las **propiedades** del proyecto.</span><span class="sxs-lookup"><span data-stu-id="d3299-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="d3299-127">Seleccione la siguiente configuración de compilación: Máquina maestra/x86/equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="d3299-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="d3299-128">Al seleccionar equipo remoto:</span><span class="sxs-lookup"><span data-stu-id="d3299-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="d3299-129">Asegúrese de que la dirección señala a la dirección IP de Wi-Fi de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d3299-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="d3299-130">Establezca la autenticación en universal (protocolo sin cifrar).</span><span class="sxs-lookup"><span data-stu-id="d3299-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="d3299-131">Compile la solución.</span><span class="sxs-lookup"><span data-stu-id="d3299-131">Build your solution.</span></span>
6. <span data-ttu-id="d3299-132">Haga clic en el botón **equipo remoto** para implementar la aplicación desde el equipo de desarrollo en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d3299-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="d3299-133">Si ya tiene una compilación existente en HoloLens, seleccione Sí para volver a instalar esta versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="d3299-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="d3299-134">![Implementación de equipos remotos para aplicaciones en Microsoft HoloLens en Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="d3299-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="d3299-135">La aplicación se instalará y se iniciará automáticamente en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d3299-135">The application will install and auto launch on your HoloLens.</span></span>
