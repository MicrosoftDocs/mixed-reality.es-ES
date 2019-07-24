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
# <a name="qr-code-tracking"></a>Seguimiento del código QR

El seguimiento del código QR se implementa en el controlador de Windows Mixed Reality para auriculares envolventes (VR). Al habilitar el seguimiento de código QR en el controlador de auriculares, el casco busca códigos QR y se les envía a las aplicaciones interesadas. Esta característica solo está disponible a partir de la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md).

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Seguimiento del código QR</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Habilitación y deshabilitación del seguimiento del código QR para el casco
Nota: Esta sección solo es válida para la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md). En las compilaciones de 19h1, no tendrá que hacer esto.
Tanto si está desarrollando una aplicación de realidad mixta que aprovecha el seguimiento del código QR como si es un cliente de una de estas aplicaciones, deberá activar manualmente el seguimiento del código QR en el controlador del auricular.

Para activar el **seguimiento del código QR** para los auriculares envolventes (VR):

1. Cierre la aplicación del portal de realidad mixta en su PC.
2. Desenchufe los auriculares del equipo.
3. Ejecute el siguiente script en el símbolo del sistema:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Vuelva a conectar los auriculares a su PC.

Para desactivar el **seguimiento del código QR** para los auriculares envolventes (VR):

1. Cierre la aplicación del portal de realidad mixta en su PC.
2. Desenchufe los auriculares del equipo.
3. Ejecute el siguiente script en el símbolo del sistema:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Vuelva a conectar los auriculares a su PC. Esto hará que los códigos QR detectados no sean localizables.

## <a name="printing-codes"></a>Imprimir códigos

En primer lugar, la [especificación de los códigos QR](https://www.qrcode.com/en/howto/code.html) indica "el área de símbolos del código QR requiere un margen o una" zona silenciosa "alrededor que se va a usar. El margen es un área clara alrededor de un símbolo en el que no se imprime nada. El código QR requiere un margen ancho de cuatro módulos en todos los lados de un símbolo. " Esto necesita tener un ancho, en cada lado, de cuatro veces el tamaño de un módulo, un solo cuadrado negro en el código. La página de especificaciones contiene consejos sobre cómo imprimir códigos QR y determinar el área necesaria para crear cierto código QR de tamaño.

Actualmente, la calidad de detección del código QR es susceptible a la iluminación y el telón de fondo variables. Para combatir esto, tenga en cuenta su iluminación e imprima el código adecuado. En una escena con iluminación especialmente brillante, imprima un código negro sobre un fondo gris. En una escena de baja luz, negro en blanco funciona. Del mismo modo, si el telón de fondo del código es especialmente oscuro, pruebe con un color negro en el código gris si la tasa de detección es baja. De lo contrario, si el telón de fondo es más claro, un código normal debería funcionar correctamente.

## <a name="qrtracking-api"></a>API de QRTracking

El complemento QRTracking expone las API para el seguimiento del código QR. Para usar el complemento, debe usar los siguientes tipos del espacio de nombres *QRCodesTrackerPlugin* .

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementación del seguimiento del código QR en Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Escenas de ejemplo de Unity en MRTK (kit de herramientas de realidad mixta)

Puede encontrar un ejemplo de cómo usar la API de seguimiento de QR en el [sitio de github](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)del kit de herramientas de realidad mixta.

MRTK ha implementado los scripts necesarios para simpilify el uso del seguimiento de QR. Todos los recursos necesarios para desarrollar aplicaciones de seguimiento QR se encuentran en la carpeta "QRTracker". Hay dos escenas: el primero es un ejemplo para simplemente mostrar los detalles de los códigos QR a medida que se detectan, y en el segundo se muestra cómo usar el sistema de coordenadas asociado al código QR para mostrar los hologramas.
Hay un recurso prefabricado "QRScanner" que agrega todos los scripts necesarios a las escenas para usar QRCodes. El script QRCodeManager es una clase singleton que implementa la API QRCode. Debe agregarse a la escena. El script "AttachToQRCode" se usa para adjuntar hologramas a los sistemas de coordenadas del código QR; este script puede agregarse a cualquiera de los hologramas. El "SpatialGraphCoordinateSystem" muestra cómo usar el sistema de coordenadas QRCode. Estos scripts se pueden usar tal cual en las escenas del proyecto o puede escribir sus propios directamente mediante el complemento, tal y como se ha descrito anteriormente.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementación del seguimiento del código QR en Unity sin MRTK

También puede usar la API de seguimiento de QR en Unity sin tener una dependencia en MRTK. Para poder usar la API, debe preparar el proyecto con la siguiente instrucción:

1. Cree una nueva carpeta en la carpeta assets del proyecto de Unity con el nombre: "Complementos".
2. Copie todos los archivos necesarios de [esta carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) en la carpeta local "plugins" que acaba de crear.
3. Puede usar los scripts de seguimiento de QR en la [carpeta MRTK scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o escribir los suyos propios.
Nota: Estos complementos son solo para las compilaciones de la [actualización 2018 de octubre de Windows 10 (también conocida como RS5)](release-notes-october-2018.md) . Los complementos se actualizarán con la siguiente versión de Windows. Los complementos actuales eran experimentales y no funcionarán para versiones futuras de Windows. Se publicarán nuevos complementos que se pueden usar desde la próxima versión de Windows y no serán compatibles con versiones anteriores y no funcionarán con RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementación del seguimiento del código QR en DirectX

Para usar QRTrackingPlugin en Visual Studio, debe agregar una referencia de QRTrackingPlugin al archivo. winmd. Aquí puede encontrar los [archivos necesarios para las plataformas compatibles](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

## <a name="getting-a-coordinate-system"></a>Obtener un sistema de coordenadas

Definimos un sistema de coordenadas de la derecha alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida en la parte superior izquierda. A continuación se muestra el sistema de coordenadas. El eje Z apunta al papel (no se muestra), pero en Unity el eje z está fuera del papel y se entrega a la izquierda.

Se define un SpatialCoordinateSystem que está alineado como se muestra. Este sistema de coordenadas se puede obtener de la plataforma mediante la API *Windows::P erception:: Spatial::P Review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

En el objeto de código QRCode ^, el código siguiente muestra cómo crear un rectángulo y colocarlo en el sistema de coordenadas QR:

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

Puede usar el tamaño físico para crear el rectángulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Por completo, su *QRCodesTrackerPlugin:: QRCodeAddedHandler* puede tener un aspecto similar al siguiente:

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

## <a name="troubleshooting-and-faq"></a>Solución de problemas y preguntas más frecuentes

**Solución de problemas generales**

* ¿El equipo está ejecutando la actualización 2018 de octubre de Windows 10?
* ¿Ha establecido la clave de registro? ¿Se ha reiniciado el dispositivo después?
* ¿La versión del código QR es una versión compatible? La API actual es compatible con la versión 20 del código QR. Se recomienda usar la versión 5 para el uso general. 
* ¿Está lo suficientemente cerca del código QR? Cuanto más se acerque la cámara al código QR, mayor será la versión del código QR que puede admitir la API.  

**¿Cómo se debe cerrar el código QR para detectarlo?**

Esto dependerá del tamaño del código QR y de la versión que sea. En el caso de un código QR de la versión 1 que varía entre 5 cm y 25 cm, la distancia mínima de detección oscila entre 0,15 y 0,5 metros. Lo más alejado puede detectarse de aproximadamente 0,3 metros para los destinos de código QR más pequeño hasta 1,4 metros para mayor. En el caso de los códigos QR mayores que eso, puede estimar; la distancia de detección para el tamaño aumenta linealmente. Nuestro seguimiento no funciona con códigos QR con lados inferiores a 5 cm.

**¿Funcionan los códigos QR con los logotipos?**

Los códigos QR con logotipos no se han probado y actualmente no se admiten.

**Cómo borrar códigos QR de la aplicación para que no se conserven?**

* Los códigos QR solo se conservan en la sesión de arranque. Una vez que reinicie (o reinicie el controlador), estos desaparecerán y se detectarán como nuevos objetos la próxima vez.
* El historial del código QR se guarda en el nivel del sistema en la sesión del controlador, pero puede configurar la aplicación para que omita los códigos QR anteriores a una marca de tiempo específica si lo desea. Actualmente, la API admite Borrar el historial del código QR, ya que es posible que varias aplicaciones estén interesadas en los datos.

**Los complementos de RS5 y versiones futuras no son compatibles** La versión RS5 del complemento solo funciona para RS5 y no funcionará en versiones futuras. El complemento expermental se reemplazará por el complemento real y debe ser el que se pueda usar en versiones futuras de Windows.
