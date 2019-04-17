---
title: Cámara localizable en DirectX
description: Se explica cómo usar la cámara (PDV) de punto de vista en una aplicación de HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, cámara localizable, punto de vista, PDV, unporoject, foundation de medios, MF, receptores personalizados, el tutorial, el código de ejemplo
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602087"
---
# <a name="locatable-camera-in-directx"></a>Cámara localizable en DirectX

Este tema describe cómo configurar un [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) de canalización para tener acceso a la [cámara](locatable-camera.md) en una aplicación de DirectX, incluidos los metadatos de marco que le permitirá encontrar las imágenes de generado en el mundo real.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Captura de medios de Windows y desarrollo de Media Foundation: IMFAttributes

Cada marco de imagen [incluye un sistema de coordenadas](locatable-camera.md#images-with-coordinate-systems) , así como dos transformaciones importantes. La "vista" transformar mapas desde el sistema de coordenadas proporcionado a la cámara y el "proyección" se asigna desde la cámara a píxeles de la imagen. El sistema de coordenadas y las 2 transformaciones se incrustan como metadatos en cada fotograma de la imagen a través de Media Foundation [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Ejemplo de uso de lectura de atributos con los receptores personalizados MF y realizar la proyección

En la secuencia personalizada de receptor MF ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), obtendrá [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) con atributos de ejemplo:

El siguiente MediaExtensions debe definirse para código en función de WinRT:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

No se puede obtener acceso a estos atributos de WinRT APIs, pero requiere la implementación de extensión de medios de [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (para el efecto) o [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) y [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) () para los receptores personalizados). Cuando se procesa en el ejemplo de esta extensión ya sea en [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) o [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), puede consultar los atributos como en este ejemplo.

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

Para acceder a la textura de la cámara, necesita el mismo dispositivo D3D que crea la textura del marco de cámara. Este dispositivo D3D se encuentra en [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) en la canalización de captura. Para obtener el Administrador de dispositivos de DXGI desde medios de captura puede usar [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) y [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

También puede habilitar mouse y teclado como métodos de entrada opcionales para la aplicación de Windows Mixed Reality. Esto también puede ser una excelente característica de depuración para los dispositivos, como HoloLens y puede ser deseable para la entrada del usuario en aplicaciones de realidad mixta que se ejecutan en inmersivos adjunta a los equipos.
