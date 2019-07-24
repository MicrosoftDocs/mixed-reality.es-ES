---
title: Seguimiento del código QR
description: Obtenga información sobre cómo activar el seguimiento del código QR para los auriculares con Windows Mixed Reality inmersivo (VR) e implementar la característica en las aplicaciones de VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, LBE, entretenimiento basado en ubicación, VR Arcade, Arcade, inmersivo, QR y código QR
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829983"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="a4c7c-104">Seguimiento del código QR</span><span class="sxs-lookup"><span data-stu-id="a4c7c-104">QR code tracking</span></span>

<span data-ttu-id="a4c7c-105">El seguimiento del código QR se implementa en el controlador de Windows Mixed Reality para auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="a4c7c-106">Al habilitar el seguimiento de código QR en el controlador de auriculares, el casco busca códigos QR y se les envía a las aplicaciones interesadas.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="a4c7c-107">Esta característica solo está disponible a partir de la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="a4c7c-108">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a4c7c-109">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="a4c7c-110">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a4c7c-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a4c7c-111"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="a4c7c-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a4c7c-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a4c7c-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a4c7c-113"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="a4c7c-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a4c7c-114">Seguimiento del código QR</span><span class="sxs-lookup"><span data-stu-id="a4c7c-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="a4c7c-115">❌</span><span class="sxs-lookup"><span data-stu-id="a4c7c-115">❌</span></span></td>
        <td><span data-ttu-id="a4c7c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a4c7c-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="a4c7c-117">Habilitación y deshabilitación del seguimiento del código QR para el casco</span><span class="sxs-lookup"><span data-stu-id="a4c7c-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="a4c7c-118">Nota: Esta sección solo es válida para la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="a4c7c-119">En las compilaciones de 19h1, no tendrá que hacer esto.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="a4c7c-120">Tanto si está desarrollando una aplicación de realidad mixta que aprovecha el seguimiento del código QR como si es un cliente de una de estas aplicaciones, deberá activar manualmente el seguimiento del código QR en el controlador del auricular.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="a4c7c-121">Para activar el **seguimiento del código QR** para los auriculares envolventes (VR):</span><span class="sxs-lookup"><span data-stu-id="a4c7c-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="a4c7c-122">Cierre la aplicación del portal de realidad mixta en su PC.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="a4c7c-123">Desenchufe los auriculares del equipo.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="a4c7c-124">Ejecute el siguiente script en el símbolo del sistema:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="a4c7c-125">Vuelva a conectar los auriculares a su PC.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="a4c7c-126">Para desactivar el **seguimiento del código QR** para los auriculares envolventes (VR):</span><span class="sxs-lookup"><span data-stu-id="a4c7c-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="a4c7c-127">Cierre la aplicación del portal de realidad mixta en su PC.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="a4c7c-128">Desenchufe los auriculares del equipo.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="a4c7c-129">Ejecute el siguiente script en el símbolo del sistema:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="a4c7c-130">Vuelva a conectar los auriculares a su PC.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="a4c7c-131">Esto hará que los códigos QR detectados no sean localizables.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="a4c7c-132">Imprimir códigos</span><span class="sxs-lookup"><span data-stu-id="a4c7c-132">Printing codes</span></span>

<span data-ttu-id="a4c7c-133">En primer lugar, la [especificación de los códigos QR](https://www.qrcode.com/en/howto/code.html) indica "el área de símbolos del código QR requiere un margen o una" zona silenciosa "alrededor que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="a4c7c-134">El margen es un área clara alrededor de un símbolo en el que no se imprime nada.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="a4c7c-135">El código QR requiere un margen ancho de cuatro módulos en todos los lados de un símbolo. "</span><span class="sxs-lookup"><span data-stu-id="a4c7c-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="a4c7c-136">Esto necesita tener un ancho, en cada lado, de cuatro veces el tamaño de un módulo, un solo cuadrado negro en el código.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="a4c7c-137">La página de especificaciones contiene consejos sobre cómo imprimir códigos QR y determinar el área necesaria para crear cierto código QR de tamaño.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="a4c7c-138">Actualmente, la calidad de detección del código QR es susceptible a la iluminación y el telón de fondo variables.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="a4c7c-139">Para combatir esto, tenga en cuenta su iluminación e imprima el código adecuado.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="a4c7c-140">En una escena con iluminación especialmente brillante, imprima un código negro sobre un fondo gris.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="a4c7c-141">En una escena de baja luz, negro en blanco funciona.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="a4c7c-142">Del mismo modo, si el telón de fondo del código es especialmente oscuro, pruebe con un color negro en el código gris si la tasa de detección es baja.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="a4c7c-143">De lo contrario, si el telón de fondo es más claro, un código normal debería funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="a4c7c-144">API de QRTracking</span><span class="sxs-lookup"><span data-stu-id="a4c7c-144">QRTracking API</span></span>

<span data-ttu-id="a4c7c-145">El complemento QRTracking expone las API para el seguimiento del código QR.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="a4c7c-146">Para usar el complemento, debe usar los siguientes tipos del espacio de nombres *QRCodesTrackerPlugin* .</span><span class="sxs-lookup"><span data-stu-id="a4c7c-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="a4c7c-147">Implementación del seguimiento del código QR en Unity</span><span class="sxs-lookup"><span data-stu-id="a4c7c-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="a4c7c-148">Escenas de ejemplo de Unity en MRTK (kit de herramientas de realidad mixta)</span><span class="sxs-lookup"><span data-stu-id="a4c7c-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="a4c7c-149">Puede encontrar un ejemplo de cómo usar la API de seguimiento de QR en el [sitio de github](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)del kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="a4c7c-150">MRTK ha implementado los scripts necesarios para simpilify el uso del seguimiento de QR.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="a4c7c-151">Todos los recursos necesarios para desarrollar aplicaciones de seguimiento QR se encuentran en la carpeta "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="a4c7c-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="a4c7c-152">Hay dos escenas: el primero es un ejemplo para simplemente mostrar los detalles de los códigos QR a medida que se detectan, y en el segundo se muestra cómo usar el sistema de coordenadas asociado al código QR para mostrar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="a4c7c-153">Hay un recurso prefabricado "QRScanner" que agrega todos los scripts necesarios a las escenas para usar QRCodes.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="a4c7c-154">El script QRCodeManager es una clase singleton que implementa la API QRCode.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="a4c7c-155">Debe agregarse a la escena.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-155">This needs to be added to your scene.</span></span> <span data-ttu-id="a4c7c-156">El script "AttachToQRCode" se usa para adjuntar hologramas a los sistemas de coordenadas del código QR; este script puede agregarse a cualquiera de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="a4c7c-157">El "SpatialGraphCoordinateSystem" muestra cómo usar el sistema de coordenadas QRCode.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="a4c7c-158">Estos scripts se pueden usar tal cual en las escenas del proyecto o puede escribir sus propios directamente mediante el complemento, tal y como se ha descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="a4c7c-159">Implementación del seguimiento del código QR en Unity sin MRTK</span><span class="sxs-lookup"><span data-stu-id="a4c7c-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="a4c7c-160">También puede usar la API de seguimiento de QR en Unity sin tener una dependencia en MRTK.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="a4c7c-161">Para poder usar la API, debe preparar el proyecto con la siguiente instrucción:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="a4c7c-162">Cree una nueva carpeta en la carpeta assets del proyecto de Unity con el nombre: "Complementos".</span><span class="sxs-lookup"><span data-stu-id="a4c7c-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="a4c7c-163">Copie todos los archivos necesarios de [esta carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) en la carpeta local "plugins" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="a4c7c-164">Puede usar los scripts de seguimiento de QR en la [carpeta MRTK scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o escribir los suyos propios.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="a4c7c-165">Nota: Estos complementos son solo para las compilaciones de la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md) .</span><span class="sxs-lookup"><span data-stu-id="a4c7c-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="a4c7c-166">Los complementos se actualizarán con la siguiente versión de Windows.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="a4c7c-167">Los complementos actuales eran experimentales y no funcionarán para versiones futuras de Windows.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="a4c7c-168">Se publicarán nuevos complementos que se pueden usar desde la próxima versión de Windows y no serán compatibles con versiones anteriores y no funcionarán con RS5).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="a4c7c-169">Implementación del seguimiento del código QR en DirectX</span><span class="sxs-lookup"><span data-stu-id="a4c7c-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="a4c7c-170">Para usar QRTrackingPlugin en Visual Studio, debe agregar una referencia de QRTrackingPlugin al archivo. winmd.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="a4c7c-171">Aquí puede encontrar los [archivos necesarios para las plataformas compatibles](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="a4c7c-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="a4c7c-172">Obtener un sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="a4c7c-172">Getting a coordinate system</span></span>

<span data-ttu-id="a4c7c-173">Definimos un sistema de coordenadas de la derecha alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida en la parte superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="a4c7c-174">A continuación se muestra el sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-174">The coordinate system is shown below.</span></span> <span data-ttu-id="a4c7c-175">El eje Z apunta al papel (no se muestra), pero en Unity el eje z está fuera del papel y se entrega a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="a4c7c-176">Se define un SpatialCoordinateSystem que está alineado como se muestra.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="a4c7c-177">Este sistema de coordenadas se puede obtener de la plataforma mediante la API *Windows::P erception:: Spatial::P Review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="a4c7c-179">En el objeto de código QRCode ^, el código siguiente muestra cómo crear un rectángulo y colocarlo en el sistema de coordenadas QR:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="a4c7c-180">Puede usar el tamaño físico para crear el rectángulo QR:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="a4c7c-181">El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="a4c7c-182">Por completo, su *QRCodesTrackerPlugin:: QRCodeAddedHandler* puede tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="a4c7c-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="a4c7c-183">Solución de problemas y preguntas más frecuentes</span><span class="sxs-lookup"><span data-stu-id="a4c7c-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="a4c7c-184">**Solución de problemas generales**</span><span class="sxs-lookup"><span data-stu-id="a4c7c-184">**General troubleshooting**</span></span>

* <span data-ttu-id="a4c7c-185">¿El equipo está ejecutando la actualización 2018 de octubre de Windows 10?</span><span class="sxs-lookup"><span data-stu-id="a4c7c-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="a4c7c-186">¿Ha establecido la clave de registro?</span><span class="sxs-lookup"><span data-stu-id="a4c7c-186">Have you set the reg key?</span></span> <span data-ttu-id="a4c7c-187">¿Se ha reiniciado el dispositivo después?</span><span class="sxs-lookup"><span data-stu-id="a4c7c-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="a4c7c-188">¿La versión del código QR es una versión compatible?</span><span class="sxs-lookup"><span data-stu-id="a4c7c-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="a4c7c-189">La API actual es compatible con la versión 20 del código QR.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="a4c7c-190">Se recomienda usar la versión 5 para el uso general.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="a4c7c-191">¿Está lo suficientemente cerca del código QR?</span><span class="sxs-lookup"><span data-stu-id="a4c7c-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="a4c7c-192">Cuanto más se acerque la cámara al código QR, mayor será la versión del código QR que puede admitir la API.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="a4c7c-193">**¿Cómo se debe cerrar el código QR para detectarlo?**</span><span class="sxs-lookup"><span data-stu-id="a4c7c-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="a4c7c-194">Esto dependerá del tamaño del código QR y de la versión que sea.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="a4c7c-195">En el caso de un código QR de la versión 1 que varía entre 5 cm y 25 cm, la distancia mínima de detección oscila entre 0,15 y 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="a4c7c-196">Lo más alejado puede detectarse de aproximadamente 0,3 metros para los destinos de código QR más pequeño hasta 1,4 metros para mayor.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="a4c7c-197">En el caso de los códigos QR mayores que eso, puede estimar; la distancia de detección para el tamaño aumenta linealmente.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="a4c7c-198">Nuestro seguimiento no funciona con códigos QR con lados inferiores a 5 cm.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="a4c7c-199">**¿Funcionan los códigos QR con los logotipos?**</span><span class="sxs-lookup"><span data-stu-id="a4c7c-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="a4c7c-200">Los códigos QR con logotipos no se han probado y actualmente no se admiten.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="a4c7c-201">**Cómo borrar códigos QR de la aplicación para que no se conserven?**</span><span class="sxs-lookup"><span data-stu-id="a4c7c-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="a4c7c-202">Los códigos QR solo se conservan en la sesión de arranque.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="a4c7c-203">Una vez que reinicie (o reinicie el controlador), estos desaparecerán y se detectarán como nuevos objetos la próxima vez.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="a4c7c-204">El historial del código QR se guarda en el nivel del sistema en la sesión del controlador, pero puede configurar la aplicación para que omita los códigos QR anteriores a una marca de tiempo específica si lo desea.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="a4c7c-205">Actualmente, la API admite Borrar el historial del código QR, ya que es posible que varias aplicaciones estén interesadas en los datos.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="a4c7c-206">**Los complementos de RS5 y versiones futuras no son compatibles** La versión RS5 del complemento solo funciona para RS5 y no funcionará en versiones futuras.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="a4c7c-207">El complemento expermental se reemplazará por el complemento real y debe ser el que se pueda usar en versiones futuras de Windows.</span><span class="sxs-lookup"><span data-stu-id="a4c7c-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
