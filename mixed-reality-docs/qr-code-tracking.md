---
title: Seguimiento del código QR
description: Obtenga información sobre cómo detectar códigos QR en HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, entretenimiento basado en ubicación, VR Arcade, Arcade, inmersivo, QR, código QR, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047166"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="ca152-104">Seguimiento del código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-104">QR code tracking</span></span>

<span data-ttu-id="ca152-105">HoloLens 2 puede detectar códigos QR en el entorno alrededor del casco y establecer un sistema de coordenadas en la ubicación real del código.</span><span class="sxs-lookup"><span data-stu-id="ca152-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca152-106">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="ca152-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca152-107">Característica</span><span class="sxs-lookup"><span data-stu-id="ca152-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="ca152-108"><a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></span><span class="sxs-lookup"><span data-stu-id="ca152-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="ca152-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ca152-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="ca152-110"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="ca152-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ca152-111">Detección del código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="ca152-112">️</span><span class="sxs-lookup"><span data-stu-id="ca152-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca152-113">✔️</span><span class="sxs-lookup"><span data-stu-id="ca152-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ca152-114">Vea la nota</span><span class="sxs-lookup"><span data-stu-id="ca152-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="ca152-115">En la actualidad, el paquete de NuGet siguiente no es compatible con los auriculares con una realidad mixta de Windows en equipos de escritorio.</span><span class="sxs-lookup"><span data-stu-id="ca152-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="ca152-116">Manténgase atento a las actualizaciones adicionales de soporte técnico de escritorio.</span><span class="sxs-lookup"><span data-stu-id="ca152-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="ca152-117">Obtención del paquete QR</span><span class="sxs-lookup"><span data-stu-id="ca152-117">Getting the QR package</span></span>
<span data-ttu-id="ca152-118">Puede descargar un paquete de NuGet para la detección del código QR [aquí](https://github.com/dorreneb/mixed-reality/releases).</span><span class="sxs-lookup"><span data-stu-id="ca152-118">You can download a NuGet package for QR code detection [here](https://github.com/dorreneb/mixed-reality/releases).</span></span>

<span data-ttu-id="ca152-119">Las versiones futuras de este paquete estarán disponibles a través del repositorio público de paquetes NuGet.</span><span class="sxs-lookup"><span data-stu-id="ca152-119">Future versions of this package will be available through the public NuGet package repository.</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="ca152-120">Detección de códigos QR</span><span class="sxs-lookup"><span data-stu-id="ca152-120">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="ca152-121">Agregar la funcionalidad de cámara web</span><span class="sxs-lookup"><span data-stu-id="ca152-121">Adding the webcam capability</span></span>
<span data-ttu-id="ca152-122">Tendrá que agregar la funcionalidad `webcam` al manifiesto para detectar códigos QR.</span><span class="sxs-lookup"><span data-stu-id="ca152-122">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="ca152-123">Esta capacidad es necesaria, ya que los datos de los códigos detectados en el entorno del usuario pueden contener información confidencial.</span><span class="sxs-lookup"><span data-stu-id="ca152-123">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="ca152-124">El permiso se puede solicitar mediante `QRCodeWatcher.RequestAccessAsync()`una llamada a:</span><span class="sxs-lookup"><span data-stu-id="ca152-124">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="ca152-125">_C#:_</span><span class="sxs-lookup"><span data-stu-id="ca152-125">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ca152-126">_C++:_</span><span class="sxs-lookup"><span data-stu-id="ca152-126">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ca152-127">Se debe solicitar permiso antes de construir un objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="ca152-127">Permission should be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="ca152-128">Aunque la detección del código QR `webcam` requiere la capacidad, la detección se produce mediante las cámaras de seguimiento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ca152-128">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="ca152-129">Esto proporciona un hipergráfico de detección más amplio y una mayor duración de la batería en comparación con la detección con la cámara foto/vídeo (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ca152-129">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="ca152-130">Detección de códigos QR en Unity</span><span class="sxs-lookup"><span data-stu-id="ca152-130">Detecting QR codes in Unity</span></span>

<span data-ttu-id="ca152-131">Puede usar la API de detección de código QR en Unity sin tomar una dependencia en MRTK.</span><span class="sxs-lookup"><span data-stu-id="ca152-131">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="ca152-132">Para ello, debe:</span><span class="sxs-lookup"><span data-stu-id="ca152-132">To do so, you must:</span></span>

1. <span data-ttu-id="ca152-133">Cree una nueva carpeta en la carpeta assets del proyecto de Unity con el nombre *plugins*.</span><span class="sxs-lookup"><span data-stu-id="ca152-133">Create a new folder in the assets folder of your unity project with the name *Plugins*.</span></span>
2. <span data-ttu-id="ca152-134">Copie todos los archivos necesarios de esta carpeta en la carpeta local "plugins" que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="ca152-134">Copy all the required files from this folder into the local "Plugins" folder you just created.</span></span>

<span data-ttu-id="ca152-135">Hay una aplicación de Unity de ejemplo que muestra un cuadrado holográfica sobre códigos QR, junto con los datos asociados, como el GUID, el tamaño físico, la marca de tiempo y los datos descodificados.</span><span class="sxs-lookup"><span data-stu-id="ca152-135">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="ca152-136">Esta aplicación se puede encontrar en https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span><span class="sxs-lookup"><span data-stu-id="ca152-136">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="ca152-137">Detección de códigos QR enC++</span><span class="sxs-lookup"><span data-stu-id="ca152-137">Detecting QR codes in C++</span></span>

>[!NOTE]
><span data-ttu-id="ca152-138">Los C++ fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="ca152-138">The C++ code snippets in this article currently demonstrate the use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="ca152-139">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque es necesario traducir el código.</span><span class="sxs-lookup"><span data-stu-id="ca152-139">The concepts are equivalent for a C++/WinRT project, though you need to translate the code.</span></span>

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="ca152-140">Obtención del sistema de coordenadas para un código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-140">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="ca152-141">Cada código QR detectado expone un [sistema de coordenadas espaciales](coordinate-systems.md) alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida en la parte superior izquierda, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="ca152-141">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="ca152-142">Cuando se usa directamente el SDK QR, el eje Z apunta al papel (no se muestra) cuando se convierte en coordenadas de Unity, el eje Z apunta fuera del papel y se entrega a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="ca152-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="ca152-143">Se muestran las alineaciones de SpatialCoordinateSystem del código QR.</span><span class="sxs-lookup"><span data-stu-id="ca152-143">A QR code's SpatialCoordinateSystem aligns shown.</span></span> <span data-ttu-id="ca152-144">Este sistema de coordenadas se puede obtener de la plataforma llamando a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> y pasando el SpatialGraphNodeId del código.</span><span class="sxs-lookup"><span data-stu-id="ca152-144">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="ca152-146">En el caso de un objeto QRCode C++, el siguiente código/CX muestra cómo crear un rectángulo y colocarlo mediante el sistema de coordenadas del código QR:</span><span class="sxs-lookup"><span data-stu-id="ca152-146">For a QRCode object, the following C++/CX code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="ca152-147">Puede usar el tamaño físico para crear el rectángulo QR:</span><span class="sxs-lookup"><span data-stu-id="ca152-147">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="ca152-148">El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:</span><span class="sxs-lookup"><span data-stu-id="ca152-148">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

<span data-ttu-id="ca152-149">Por completo, su *QRCodeWatcher:: QRCodeAddedHandler* puede tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="ca152-149">Altogether, your *QRCodeWatcher::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="ca152-150">Prácticas recomendadas para la detección del código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-150">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="ca152-151">Zonas tranquilas alrededor de códigos QR</span><span class="sxs-lookup"><span data-stu-id="ca152-151">Quiet zones around QR Codes</span></span>

<span data-ttu-id="ca152-152">Para que se puedan leer correctamente, los códigos QR requieren un margen alrededor de todos los lados del código.</span><span class="sxs-lookup"><span data-stu-id="ca152-152">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="ca152-153">Este margen no debe contener contenido impreso y debe ser de cuatro módulos (un solo cuadrado negro en el código).</span><span class="sxs-lookup"><span data-stu-id="ca152-153">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="ca152-154">La [especificación QR](https://www.qrcode.com/en/howto/code.html) contiene más información acerca de las zonas tranquilas.</span><span class="sxs-lookup"><span data-stu-id="ca152-154">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="ca152-155">Iluminación y fondo</span><span class="sxs-lookup"><span data-stu-id="ca152-155">Lighting and backdrop</span></span>
<span data-ttu-id="ca152-156">La calidad de detección del código QR es susceptible a la iluminación y el telón de fondo variables.</span><span class="sxs-lookup"><span data-stu-id="ca152-156">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="ca152-157">En una escena con iluminación especialmente brillante, imprima un código negro sobre un fondo gris.</span><span class="sxs-lookup"><span data-stu-id="ca152-157">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="ca152-158">De lo contrario, imprima un código QR negro sobre un fondo blanco.</span><span class="sxs-lookup"><span data-stu-id="ca152-158">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="ca152-159">Si el telón de fondo para el código es especialmente oscuro, pruebe un color negro en el código gris si la tasa de detección es baja.</span><span class="sxs-lookup"><span data-stu-id="ca152-159">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="ca152-160">Si el telón de fondo es relativamente claro, un código normal debería funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="ca152-160">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="ca152-161">Tamaño de los códigos QR</span><span class="sxs-lookup"><span data-stu-id="ca152-161">Size of QR codes</span></span>
<span data-ttu-id="ca152-162">Los dispositivos de Windows Mixed Reality no funcionan con códigos QR con lados inferiores a 5 cm cada uno.</span><span class="sxs-lookup"><span data-stu-id="ca152-162">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="ca152-163">En el caso de los códigos QR entre 5 y 10 cm de longitud, debe estar bastante cerca de detectar el código.</span><span class="sxs-lookup"><span data-stu-id="ca152-163">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="ca152-164">También se tardará más tiempo en detectar códigos en este tamaño.</span><span class="sxs-lookup"><span data-stu-id="ca152-164">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="ca152-165">El tiempo exacto para detectar códigos depende no solo del tamaño de los códigos QR, sino de la distancia del código.</span><span class="sxs-lookup"><span data-stu-id="ca152-165">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="ca152-166">Si se desplaza más cerca del código, se le ayudará a desplazar los problemas con el tamaño.</span><span class="sxs-lookup"><span data-stu-id="ca152-166">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="ca152-167">Distancia y posición angular del código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-167">Distance and angular position from the QR code</span></span>
<span data-ttu-id="ca152-168">Las cámaras de seguimiento solo pueden detectar un cierto nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="ca152-168">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="ca152-169">Para códigos muy pequeños: < 10cm a lo largo de los lados: debe estar bastante cerca.</span><span class="sxs-lookup"><span data-stu-id="ca152-169">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="ca152-170">En el caso de un código QR de la versión 1 que varía entre 10 y 25 cm de ancho, la distancia mínima de detección oscila entre 0,15 y 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="ca152-170">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="ca152-171">La distancia de detección para el tamaño aumenta linealmente.</span><span class="sxs-lookup"><span data-stu-id="ca152-171">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="ca152-172">La detección de QR funciona con un intervalo de ángulos + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="ca152-172">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="ca152-173">Esto es para asegurarse de que tenemos una solución adecuada para detectar el código.</span><span class="sxs-lookup"><span data-stu-id="ca152-173">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="ca152-174">Códigos QR con logotipos</span><span class="sxs-lookup"><span data-stu-id="ca152-174">QR codes with logos</span></span>
<span data-ttu-id="ca152-175">Los códigos QR con logotipos no se han probado y actualmente no se admiten.</span><span class="sxs-lookup"><span data-stu-id="ca152-175">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="ca152-176">Administración de datos de código QR</span><span class="sxs-lookup"><span data-stu-id="ca152-176">Managing QR code data</span></span>
<span data-ttu-id="ca152-177">Los dispositivos de Windows Mixed Reality detectan códigos QR en el nivel de sistema del controlador.</span><span class="sxs-lookup"><span data-stu-id="ca152-177">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="ca152-178">Cuando se reinicia el dispositivo, los códigos QR detectados desaparecen y se vuelven a detectar como nuevos objetos la próxima vez.</span><span class="sxs-lookup"><span data-stu-id="ca152-178">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="ca152-179">Se recomienda configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específica.</span><span class="sxs-lookup"><span data-stu-id="ca152-179">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="ca152-180">Actualmente, la API no permite borrar el historial del código QR.</span><span class="sxs-lookup"><span data-stu-id="ca152-180">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="ca152-181">Colocación del código QR en un espacio</span><span class="sxs-lookup"><span data-stu-id="ca152-181">QR code placement in a space</span></span>
<span data-ttu-id="ca152-182">Para obtener recomendaciones sobre dónde y cómo colocar códigos QR, consulte [consideraciones de entorno para HoloLens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="ca152-182">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="ca152-183">Referencia de la API QR</span><span class="sxs-lookup"><span data-stu-id="ca152-183">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ca152-184">Vea también</span><span class="sxs-lookup"><span data-stu-id="ca152-184">See also</span></span>
* [<span data-ttu-id="ca152-185">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="ca152-185">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="ca152-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="ca152-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>