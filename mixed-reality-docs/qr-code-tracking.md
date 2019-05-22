---
title: Seguimiento del código QR
description: Obtenga información sobre cómo activar el seguimiento de los auriculares de Windows Mixed Reality envolventes (VR) del código QR e implemente la característica en sus aplicaciones de realidad virtual.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, lbe, entretenimiento basadas en la ubicación, vr arcade, código qr de arcade envolventes, qr,
ms.openlocfilehash: e6588552c0cfa8bffa19ac2be5c247c5f73dc19c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974899"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="87b96-104">Seguimiento del código QR</span><span class="sxs-lookup"><span data-stu-id="87b96-104">QR code tracking</span></span>

<span data-ttu-id="87b96-105">Seguimiento del código QR está implementado en el controlador Windows Mixed Reality inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="87b96-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="87b96-106">Al habilitar el seguimiento de código QR en el controlador de auriculares, los auriculares buscará códigos QR y se notifican a las aplicaciones interesadas.</span><span class="sxs-lookup"><span data-stu-id="87b96-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="87b96-107">Esta característica solo está disponible a partir de la [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="87b96-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="87b96-108">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="87b96-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="87b96-109">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="87b96-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="87b96-110">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="87b96-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="87b96-111">Característica</span><span class="sxs-lookup"><span data-stu-id="87b96-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="87b96-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="87b96-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="87b96-113"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="87b96-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="87b96-114">Seguimiento del código QR</span><span class="sxs-lookup"><span data-stu-id="87b96-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="87b96-115">✔️</span><span class="sxs-lookup"><span data-stu-id="87b96-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="87b96-116">Seguimiento de los auriculares de código de activación y desactivación de QR</span><span class="sxs-lookup"><span data-stu-id="87b96-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="87b96-117">Nota: En esta sección solo es válida para [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="87b96-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="87b96-118">Desde el 1 de 19h compilaciones y versiones posteriores no tendrá que hacerlo.</span><span class="sxs-lookup"><span data-stu-id="87b96-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="87b96-119">Si está desarrollando una aplicación de realidad mixta que aprovechará el seguimiento del código QR o es un cliente de una de estas aplicaciones, deberá activar manualmente el código QR en el controlador de los auriculares de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="87b96-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="87b96-120">Para **activar el seguimiento del código QR** para su envolventes auriculares (VR):</span><span class="sxs-lookup"><span data-stu-id="87b96-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="87b96-121">Cierre la aplicación de Portal de realidad mixta en su PC.</span><span class="sxs-lookup"><span data-stu-id="87b96-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="87b96-122">Desconecte los auriculares de su PC.</span><span class="sxs-lookup"><span data-stu-id="87b96-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="87b96-123">En el símbolo del sistema, ejecute el siguiente script:</span><span class="sxs-lookup"><span data-stu-id="87b96-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="87b96-124">Vuelva a conectar los auriculares a su equipo.</span><span class="sxs-lookup"><span data-stu-id="87b96-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="87b96-125">Para **desactivar el seguimiento del código QR** para su envolventes auriculares (VR):</span><span class="sxs-lookup"><span data-stu-id="87b96-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="87b96-126">Cierre la aplicación de Portal de realidad mixta en su PC.</span><span class="sxs-lookup"><span data-stu-id="87b96-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="87b96-127">Desconecte los auriculares de su PC.</span><span class="sxs-lookup"><span data-stu-id="87b96-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="87b96-128">En el símbolo del sistema, ejecute el siguiente script:</span><span class="sxs-lookup"><span data-stu-id="87b96-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="87b96-129">Vuelva a conectar los auriculares a su equipo.</span><span class="sxs-lookup"><span data-stu-id="87b96-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="87b96-130">Esto hará que los códigos QR detectados "no-localizable."</span><span class="sxs-lookup"><span data-stu-id="87b96-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="87b96-131">Códigos de impresión</span><span class="sxs-lookup"><span data-stu-id="87b96-131">Printing codes</span></span>

<span data-ttu-id="87b96-132">Principalmente, el [especificaciones para los códigos QR](https://www.qrcode.com/en/howto/code.html) dice "el área de símbolos de código QR requiere un margen o una"zona quiet"a su alrededor para usarse.</span><span class="sxs-lookup"><span data-stu-id="87b96-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="87b96-133">El margen es un área claro en torno a un símbolo de donde se imprime nada.</span><span class="sxs-lookup"><span data-stu-id="87b96-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="87b96-134">Código QR requiere un amplio margen de cuatro módulos en todos los lados de un símbolo".</span><span class="sxs-lookup"><span data-stu-id="87b96-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="87b96-135">Esto debe tener una anchura, en cada lado, de cuatro veces el tamaño de un módulo: un cuadrado negro único en el código.</span><span class="sxs-lookup"><span data-stu-id="87b96-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="87b96-136">La página especificación contiene consejos sobre cómo imprimir los códigos QR y averiguar el área requerida para hacer un determinado tamaño código QR.</span><span class="sxs-lookup"><span data-stu-id="87b96-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="87b96-137">Actualmente calidad de detección de código QR es susceptible a distintos de iluminación y telón de fondo.</span><span class="sxs-lookup"><span data-stu-id="87b96-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="87b96-138">Para combatir esta situación, tenga en cuenta la iluminación e imprimir el código adecuado.</span><span class="sxs-lookup"><span data-stu-id="87b96-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="87b96-139">En una escena con iluminación especialmente brillante, imprimir un código de color negro sobre un fondo gris.</span><span class="sxs-lookup"><span data-stu-id="87b96-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="87b96-140">En una escena poca luz, negra sobre blanco funciona.</span><span class="sxs-lookup"><span data-stu-id="87b96-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="87b96-141">Del mismo modo, si el telón de fondo para el código es especialmente oscuro, pruebe un color negro en gris código si la tasa de detección es baja.</span><span class="sxs-lookup"><span data-stu-id="87b96-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="87b96-142">En caso contrario, si el texto de fondo es más claro, un código normal debería funcionar bien.</span><span class="sxs-lookup"><span data-stu-id="87b96-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="87b96-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="87b96-143">QRTracking API</span></span>

<span data-ttu-id="87b96-144">El complemento QRTracking expone las API para seguimiento del código QR.</span><span class="sxs-lookup"><span data-stu-id="87b96-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="87b96-145">Para usar el complemento, deberá usar los siguientes tipos de la *QRCodesTrackerPlugin* espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="87b96-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="87b96-146">Implementación de código QR de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="87b96-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="87b96-147">Ejemplo de segundo plano de Unity en MRTK (Kit de herramientas de realidad mixta)</span><span class="sxs-lookup"><span data-stu-id="87b96-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="87b96-148">Puede encontrar un ejemplo de cómo usar la API de seguimiento QR en el Kit de herramientas de realidad mixta [sitio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span><span class="sxs-lookup"><span data-stu-id="87b96-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="87b96-149">MRTK ha implementado los scripts necesarios para simpilify el seguimiento del uso de QR.</span><span class="sxs-lookup"><span data-stu-id="87b96-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="87b96-150">Todos los recursos necesarios para desarrollar QR realizar seguimiento de aplicaciones están en la carpeta "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="87b96-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="87b96-151">Hay dos escenas: el primero es un ejemplo simplemente para mostrar los detalles de los códigos QR cuando se detectan y el segundo ejemplo muestra cómo usar el sistema de coordenadas que se adjunta al código QR para mostrar hologramas.</span><span class="sxs-lookup"><span data-stu-id="87b96-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="87b96-152">Hay un prefabricado "QRScanner" que agrega todos los scripts necesarios para el segundo plano para utilizar QRCodes.</span><span class="sxs-lookup"><span data-stu-id="87b96-152">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="87b96-153">La secuencia de comandos QRCodeManager es una clase singleton que implementa la API CódigoQR.</span><span class="sxs-lookup"><span data-stu-id="87b96-153">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="87b96-154">Esto debe agregarse a la escena.</span><span class="sxs-lookup"><span data-stu-id="87b96-154">This needs to be added to your scene.</span></span> <span data-ttu-id="87b96-155">La secuencia de comandos "AttachToQRCode" se utiliza para adjuntar hologramas para los sistemas de coordenadas del código QR, esta secuencia de comandos se puede agregar a cualquiera de sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="87b96-155">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="87b96-156">El "SpatialGraphCoordinateSystem" muestra cómo usar el sistema de coordenadas CódigoQR.</span><span class="sxs-lookup"><span data-stu-id="87b96-156">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="87b96-157">Estos scripts se pueden usar como-está en el proyecto de segundo plano, o puede escribir su propio directamente con el complemento como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="87b96-157">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="87b96-158">Implementar el seguimiento en Unity sin MRTK del código QR</span><span class="sxs-lookup"><span data-stu-id="87b96-158">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="87b96-159">También puede usar la API de seguimiento QR en Unity sin depender de MRTK.</span><span class="sxs-lookup"><span data-stu-id="87b96-159">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="87b96-160">Para poder usar la API, deberá preparar el proyecto con la siguiente instrucción:</span><span class="sxs-lookup"><span data-stu-id="87b96-160">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="87b96-161">Crear una nueva carpeta en la carpeta activos del proyecto de unity con el nombre: "Complementos".</span><span class="sxs-lookup"><span data-stu-id="87b96-161">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="87b96-162">Copie todos los archivos necesarios de [esta carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) en la carpeta local de "Complementos" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="87b96-162">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="87b96-163">Puede usar el QR seguimiento secuencias de comandos en el [carpeta de scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o escribir el suyo propio.</span><span class="sxs-lookup"><span data-stu-id="87b96-163">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="87b96-164">Nota: Estos complementos son solo para [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md) compilaciones.</span><span class="sxs-lookup"><span data-stu-id="87b96-164">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="87b96-165">Los complementos se actualizará con la próxima versión de windows.</span><span class="sxs-lookup"><span data-stu-id="87b96-165">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="87b96-166">Los complementos actuales eran experimentales y no funcionará para una versión futura de windows.</span><span class="sxs-lookup"><span data-stu-id="87b96-166">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="87b96-167">Se publicará nuevos complementos que puede usarse desde la próxima versión de windows y no será con versiones anteriores compatibles y no funcionará con RS5).</span><span class="sxs-lookup"><span data-stu-id="87b96-167">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="87b96-168">Implementación de código QR en DirectX de seguimiento</span><span class="sxs-lookup"><span data-stu-id="87b96-168">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="87b96-169">Para usar el QRTrackingPlugin en Visual Studio, deberá agregar una referencia de la QRTrackingPlugin a la .winmd.</span><span class="sxs-lookup"><span data-stu-id="87b96-169">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="87b96-170">Puede encontrar el [archivos necesarios para las plataformas admitidas aquí](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="87b96-170">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="87b96-171">Obtención de un sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="87b96-171">Getting a coordinate system</span></span>

<span data-ttu-id="87b96-172">Definimos un sistema de coordenadas derecho alineado con el código QR en la esquina superior izquierda del cuadrado detección rápida en la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="87b96-172">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="87b96-173">A continuación se muestra el sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="87b96-173">The coordinate system is shown below.</span></span> <span data-ttu-id="87b96-174">Señala al eje z en el documento (no mostrado), pero en Unity es el eje z ha quedado sin el papel y zurdo.</span><span class="sxs-lookup"><span data-stu-id="87b96-174">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="87b96-175">Se define un SpatialCoordinateSystem que se alinea tal como se muestra.</span><span class="sxs-lookup"><span data-stu-id="87b96-175">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="87b96-176">Se puede obtener este sistema de coordenadas de la plataforma mediante la API de *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="87b96-176">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="87b96-178">Desde CódigoQR ^ código objeto, el código siguiente muestra cómo crear un rectángulo y colóquelo en el sistema de coordenadas QR:</span><span class="sxs-lookup"><span data-stu-id="87b96-178">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="87b96-179">Puede usar el tamaño físico para crear un rectángulo QR:</span><span class="sxs-lookup"><span data-stu-id="87b96-179">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="87b96-180">El sistema de coordenadas puede utilizarse para dibujar el código QR o adjuntar hologramas a la ubicación:</span><span class="sxs-lookup"><span data-stu-id="87b96-180">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="87b96-181">En conjunto, su *QRCodesTrackerPlugin::QRCodeAddedHandler* es posible que este aspecto:</span><span class="sxs-lookup"><span data-stu-id="87b96-181">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="87b96-182">Solución de problemas y preguntas más frecuentes</span><span class="sxs-lookup"><span data-stu-id="87b96-182">Troubleshooting and FAQ</span></span>

<span data-ttu-id="87b96-183">**Solución de problemas generales**</span><span class="sxs-lookup"><span data-stu-id="87b96-183">**General troubleshooting**</span></span>

* <span data-ttu-id="87b96-184">¿Es un equipo que ejecute Windows 10 de octubre de 2018 actualizar?</span><span class="sxs-lookup"><span data-stu-id="87b96-184">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="87b96-185">¿Ha establecido la clave del registro?</span><span class="sxs-lookup"><span data-stu-id="87b96-185">Have you set the reg key?</span></span> <span data-ttu-id="87b96-186">¿Reinicia el dispositivo más adelante?</span><span class="sxs-lookup"><span data-stu-id="87b96-186">Restarted the device afterwards?</span></span>
* <span data-ttu-id="87b96-187">¿Es una versión compatible de la versión del código QR?</span><span class="sxs-lookup"><span data-stu-id="87b96-187">Is the QR code version a supported version?</span></span> <span data-ttu-id="87b96-188">Admite la API actual hasta el 20 de versión de código QR.</span><span class="sxs-lookup"><span data-stu-id="87b96-188">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="87b96-189">Se recomienda usar la versión 5 para el uso general.</span><span class="sxs-lookup"><span data-stu-id="87b96-189">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="87b96-190">¿Son cerrar lo suficiente como para el código QR?</span><span class="sxs-lookup"><span data-stu-id="87b96-190">Are you close enough to the QR code?</span></span> <span data-ttu-id="87b96-191">Cuanto más se acerque la cámara es el código QR, cuanto mayor sea la versión de código la API de QR puede admitir.</span><span class="sxs-lookup"><span data-stu-id="87b96-191">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="87b96-192">**¿Qué es necesario para el código QR para detectarlo?**</span><span class="sxs-lookup"><span data-stu-id="87b96-192">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="87b96-193">Esto dependerá del tamaño del código QR, y también qué versión es.</span><span class="sxs-lookup"><span data-stu-id="87b96-193">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="87b96-194">Para un código QR de la versión 1 varía entre los lados 5 cm y lados 25 cm, la distancia mínima de detección se comprendido entre 0,15 metros y metros de 0,5.</span><span class="sxs-lookup"><span data-stu-id="87b96-194">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="87b96-195">Más alejada inmediatamente estos se pueden detectar desde va de aproximadamente 0,3 metros para el destino del código QR más pequeño a 1,4 metros para el más grande.</span><span class="sxs-lookup"><span data-stu-id="87b96-195">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="87b96-196">Para mayor los códigos QR, puede hacer una estimación; la distancia de detección para el tamaño aumenta linealmente.</span><span class="sxs-lookup"><span data-stu-id="87b96-196">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="87b96-197">Nuestro rastreador no funciona con los códigos QR con lados menor que 5 cm.</span><span class="sxs-lookup"><span data-stu-id="87b96-197">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="87b96-198">**¿Hacer que los códigos QR con logotipos trabajo?**</span><span class="sxs-lookup"><span data-stu-id="87b96-198">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="87b96-199">Códigos QR con logotipos no se han probado y son compatibles actualmente.</span><span class="sxs-lookup"><span data-stu-id="87b96-199">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="87b96-200">**¿Cómo borrar los códigos QR desde mi aplicación por lo que no se conserva?**</span><span class="sxs-lookup"><span data-stu-id="87b96-200">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="87b96-201">Códigos QR solo se conservan en la sesión de inicio.</span><span class="sxs-lookup"><span data-stu-id="87b96-201">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="87b96-202">Una vez que se reinicie (o reinicie el controlador), pasado y se detectan como nuevos objetos próxima vez.</span><span class="sxs-lookup"><span data-stu-id="87b96-202">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="87b96-203">Historial de código QR se guarda en el nivel de sistema en la sesión de controlador, pero puede configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específico, si desea.</span><span class="sxs-lookup"><span data-stu-id="87b96-203">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="87b96-204">Actualmente, la API admite QR Borrar historial de código, como varias aplicaciones pueden estar interesadas en los datos.</span><span class="sxs-lookup"><span data-stu-id="87b96-204">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="87b96-205">**Los complementos para RS5 y las versiones futuras no están compatible** RS5 versión del complemento solo funciona para RS5 y no funcionará en versiones futuras.</span><span class="sxs-lookup"><span data-stu-id="87b96-205">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="87b96-206">El complemento de expermental se reemplazará con el complemento real y debe ser el único que podemos usar en futuras versiones de windows.</span><span class="sxs-lookup"><span data-stu-id="87b96-206">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
