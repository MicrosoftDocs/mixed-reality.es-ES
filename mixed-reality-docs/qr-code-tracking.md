---
title: Seguimiento del código QR
description: Obtenga información sobre cómo activar el seguimiento de los auriculares de Windows Mixed Reality envolventes (VR) del código QR e implemente la característica en sus aplicaciones de realidad virtual.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, lbe, entretenimiento basadas en la ubicación, vr arcade, código qr de arcade envolventes, qr,
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605787"
---
# <a name="qr-code-tracking"></a>Seguimiento del código QR

Seguimiento del código QR está implementado en el controlador Windows Mixed Reality inmersivos (VR). Al habilitar el seguimiento de código QR en el controlador de auriculares, los auriculares buscará códigos QR y se notifican a las aplicaciones interesadas. Esta característica solo está disponible a partir de la [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md).

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Seguimiento del código QR</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Seguimiento de los auriculares de código de activación y desactivación de QR
Nota: En esta sección solo es válida para [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md). Desde el 1 de 19h compilaciones y versiones posteriores no tendrá que hacerlo.
Si está desarrollando una aplicación de realidad mixta que aprovechará el seguimiento del código QR o es un cliente de una de estas aplicaciones, deberá activar manualmente el código QR en el controlador de los auriculares de seguimiento.

Para **activar el seguimiento del código QR** para su envolventes auriculares (VR):

1. Cierre la aplicación de Portal de realidad mixta en su PC.
2. Desconecte los auriculares de su PC.
3. En el símbolo del sistema, ejecute el siguiente script:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Vuelva a conectar los auriculares a su equipo.

Para **desactivar el seguimiento del código QR** para su envolventes auriculares (VR):

1. Cierre la aplicación de Portal de realidad mixta en su PC.
2. Desconecte los auriculares de su PC.
3. En el símbolo del sistema, ejecute el siguiente script:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Vuelva a conectar los auriculares a su equipo. Esto hará que los códigos QR detectados "no-localizable."

## <a name="printing-codes"></a>Códigos de impresión

Principalmente, el [especificaciones para los códigos QR](https://www.qrcode.com/en/howto/code.html) dice "el área de símbolos de código QR requiere un margen o una"zona quiet"a su alrededor para usarse. El margen es un área claro en torno a un símbolo de donde se imprime nada. Código QR requiere un amplio margen de cuatro módulos en todos los lados de un símbolo". Esto debe tener una anchura, en cada lado, de cuatro veces el tamaño de un módulo: un cuadrado negro único en el código. La página especificación contiene consejos sobre cómo imprimir los códigos QR y averiguar el área requerida para hacer un determinado tamaño código QR.

Actualmente calidad de detección de código QR es susceptible a distintos de iluminación y telón de fondo. Para combatir esta situación, tenga en cuenta la iluminación e imprimir el código adecuado. En una escena con iluminación especialmente brillante, imprimir un código de color negro sobre un fondo gris. En una escena poca luz, negra sobre blanco funciona. Del mismo modo, si el telón de fondo para el código es especialmente oscuro, pruebe un color negro en gris código si la tasa de detección es baja. En caso contrario, si el texto de fondo es más claro, un código normal debería funcionar bien.

## <a name="qrtracking-api"></a>QRTracking API

El complemento QRTracking expone las API para seguimiento del código QR. Para usar el complemento, deberá usar los siguientes tipos de la *QRCodesTrackerPlugin* espacio de nombres.

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementación de código QR de seguimiento en Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Ejemplo de segundo plano de Unity en MRTK (Kit de herramientas de realidad mixta)

Puede encontrar un ejemplo de cómo usar la API de seguimiento QR en el Kit de herramientas de realidad mixta [sitio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).

MRTK ha implementado los scripts necesarios para simpilify el seguimiento del uso de QR. Todos los recursos necesarios para desarrollar QR realizar seguimiento de aplicaciones están en la carpeta "QRTracker". Hay dos escenas: el primero es un ejemplo simplemente para mostrar los detalles de los códigos QR cuando se detectan y el segundo ejemplo muestra cómo usar el sistema de coordenadas que se adjunta al código QR para mostrar hologramas.
Hay un prefabricado "QRScanner" que agrega todos los scrips necesarias en segundo plano para utilizar QRCodes. El script QRCodeManager es una clase singileton que implementa la API de CódigoQR puede agregarlo a la escena. Las secuencias de comandos "AttachToQRCode" se utiliza para adjuntar hologramas a los sistemas de código QR coodridnate, esta secuencia de comandos se puede agregar a cualquiera de sus hologramas. El "SpatialGraphCoordinateSystem" muestra cómo usar el sistema de coordenadas CódigoQR. Estos scripts se pueden usar tal cual en escenas de su proyecto o puede escribir su propio directamente con el complemento como se describió anteriormente.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementar el seguimiento en Unity sin MRTK del código QR

También puede usar la API de seguimiento QR en Unity sin depender de MRTK. Para poder usar la API, deberá preparar el proyecto con la siguiente instrucción:

1. Crear una nueva carpeta en la carpeta activos del proyecto de unity con el nombre: "Complementos".
2. Copie todos los archivos necesarios de [esta carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) en la carpeta local de "Complementos" que acaba de crear.
3. Puede usar el QR seguimiento secuencias de comandos en el [carpeta de scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o escribir el suyo propio.
Nota: Estos complementos son solo para [10 de octubre de 2018 de Windows Update (también conocido como RS5)](release-notes-october-2018.md) compilaciones. Los complementos se actualizará con la próxima versión de windows. Los complementos actuales eran experimentales y no funcionará para una versión futura de windows. Se publicará nuevos complementos que puede usarse desde la próxima versión de windows y no será con versiones anteriores compatibles y no funcionará con RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementación de código QR en DirectX de seguimiento

Para usar el QRTrackingPlugin en Visual Studio, deberá agregar una referencia de la QRTrackingPlugin a la .winmd. Puede encontrar el [archivos necesarios para las plataformas admitidas aquí](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

## <a name="getting-a-coordinate-system"></a>Obtención de un sistema de coordenadas

Definimos un sistema de coordenadas derecho alineado con el código QR en la esquina superior izquierda del cuadrado detección rápida en la esquina superior izquierda. A continuación se muestra el sistema de coordenadas. Señala al eje z en el documento (no mostrado), pero en Unity es el eje z ha quedado sin el papel y zurdo.

Se define un SpatialCoordinateSystem que se alinea tal como se muestra. Se puede obtener este sistema de coordenadas de la plataforma mediante la API de *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

Desde CódigoQR ^ código objeto, el código siguiente muestra cómo crear un rectángulo y colóquelo en el sistema de coordenadas QR:

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

Puede usar el tamaño físico para crear un rectángulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

El sistema de coordenadas puede utilizarse para dibujar el código QR o adjuntar hologramas a la ubicación:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

En conjunto, su *QRCodesTrackerPlugin::QRCodeAddedHandler* es posible que este aspecto:

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

* ¿Es un equipo que ejecute Windows 10 de octubre de 2018 actualizar?
* ¿Ha establecido la clave del registro? ¿Reinicia el dispositivo más adelante?
* ¿Es una versión compatible de la versión del código QR? Admite la API actual hasta el 20 de versión de código QR. Se recomienda usar la versión 5 para el uso general. 
* ¿Son cerrar lo suficiente como para el código QR? Cuanto más se acerque la cámara es el código QR, cuanto mayor sea la versión de código la API de QR puede admitir.  

**¿Qué es necesario para el código QR para detectarlo?**

Esto dependerá del tamaño del código QR, y también qué versión es. Para un código QR de la versión 1 varía entre los lados 5 cm y lados 25 cm, la distancia mínima de detección se comprendido entre 0,15 metros y metros de 0,5. Más alejada inmediatamente estos se pueden detectar desde va de aproximadamente 0,3 metros para el destino del código QR más pequeño a 1,4 metros para el más grande. Para mayor los códigos QR, puede hacer una estimación; la distancia de detección para el tamaño aumenta linealmente. Nuestro rastreador no funciona con los códigos QR con lados menor que 5 cm.

**¿Hacer que los códigos QR con logotipos trabajo?**

Códigos QR con logotipos no se han probado y son compatibles actualmente.

**¿Cómo borrar los códigos QR desde mi aplicación por lo que no se conserva?**

* Códigos QR solo se conservan en la sesión de inicio. Una vez que se reinicie (o reinicie el controlador), pasado y se detectan como nuevos objetos próxima vez.
* Historial de código QR se guarda en el nivel de sistema en la sesión de controlador, pero puede configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específico, si desea. Actualmente, la API admite QR Borrar historial de código, como varias aplicaciones pueden estar interesadas en los datos.

**Los complementos para RS5 y las versiones futuras no están compatible** RS5 versión del complemento solo funciona para RS5 y no funcionará en versiones futuras. El complemento de expermental se reemplazará con el complemento real y debe ser el único que podemos usar en futuras versiones de windows.
