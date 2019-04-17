---
title: Obtenga aplicaciones para HoloLens
description: Describe la instalación de aplicaciones para HoloLens, tanto a través de la Microsoft Store y la instalación de prueba.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: transferir localmente, carga del lado, instalaciones de prueba, almacén, uwp, aplicación, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597557"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="84131-104">Obtenga aplicaciones para HoloLens</span><span class="sxs-lookup"><span data-stu-id="84131-104">Get apps for HoloLens</span></span>

<span data-ttu-id="84131-105">Como un dispositivo Windows 10, HoloLens, es compatible con muchas aplicaciones de UWP existentes desde la tienda de aplicaciones, así como nuevas aplicaciones creadas específicamente para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="84131-106">En la parte superior, incluso podría [desarrollar](development-overview.md) e instalar sus propias aplicaciones o aquellas de sus amigos!</span><span class="sxs-lookup"><span data-stu-id="84131-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="84131-107">Instalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="84131-107">Installing Apps</span></span>

<span data-ttu-id="84131-108">Hay tres formas de instalar nuevas aplicaciones en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="84131-109">Será el método principal instalar nuevas aplicaciones desde el Store de Windows.</span><span class="sxs-lookup"><span data-stu-id="84131-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="84131-110">Sin embargo, también puede instalar en sus propias aplicaciones mediante Device Portal o mediante su implementación desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84131-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="84131-111">Desde la Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="84131-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="84131-112">Realizar una [bloom](gestures.md#bloom) gesto para abrir el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="84131-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="84131-113">Seleccione la aplicación Store y, a continuación, puntee para colocar este icono en el mundo.</span><span class="sxs-lookup"><span data-stu-id="84131-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="84131-114">Cuando se abra la aplicación Store, use la barra de búsqueda para buscar cualquier aplicación que desee.</span><span class="sxs-lookup"><span data-stu-id="84131-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="84131-115">Seleccione **obtener** o **instalar** en la página de aplicación (una compra puede ser necesaria).</span><span class="sxs-lookup"><span data-stu-id="84131-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="84131-116">Instalar un paquete de aplicación con el Portal de dispositivo</span><span class="sxs-lookup"><span data-stu-id="84131-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="84131-117">Establecer una conexión desde [Device Portal](using-the-windows-device-portal.md) al destino HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="84131-118">Navegue hasta la **aplicaciones** página en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="84131-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="84131-119">En **paquete de aplicación** busque el archivo .appx relacionado con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="84131-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="84131-120">Asegúrese de hacer referencia a los archivos asociados de dependencia y el certificado.</span><span class="sxs-lookup"><span data-stu-id="84131-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="84131-121">Haga clic en **vaya**.</span><span class="sxs-lookup"><span data-stu-id="84131-121">Click **Go**.</span></span>

<span data-ttu-id="84131-122">![Instalar el formulario de aplicación de Windows Device Portal en Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="84131-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="84131-123">Uso de Windows Device Portal para instalar una aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="84131-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="84131-124">Implementar desde Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="84131-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="84131-125">Abra la solución de Visual Studio de la aplicación (archivo .sln).</span><span class="sxs-lookup"><span data-stu-id="84131-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="84131-126">Abra el proyecto **propiedades** .</span><span class="sxs-lookup"><span data-stu-id="84131-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="84131-127">Seleccione la configuración de compilación siguiente: Equipo maestro o x86/remoto.</span><span class="sxs-lookup"><span data-stu-id="84131-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="84131-128">Al seleccionar un equipo remoto:</span><span class="sxs-lookup"><span data-stu-id="84131-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="84131-129">Asegúrese de que la dirección señala a la dirección de IP WiFi de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="84131-130">Establecer la autenticación Universal (protocolo sin cifrar).</span><span class="sxs-lookup"><span data-stu-id="84131-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="84131-131">Compile la solución.</span><span class="sxs-lookup"><span data-stu-id="84131-131">Build your solution.</span></span>
6. <span data-ttu-id="84131-132">Haga clic en el **máquina remota** botón para implementar la aplicación desde el equipo de desarrollo en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="84131-133">Si ya tiene una compilación existente en el HoloLens, seleccione Sí para volver a instalar esta versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="84131-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="84131-134">![Implementación de la máquina remota para las aplicaciones de Microsoft HoloLens en Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="84131-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="84131-135">Instalará la aplicación y auto lanzamiento en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="84131-135">The application will install and auto launch on your HoloLens.</span></span>
