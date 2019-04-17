---
title: Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)
description: Cómo crear los iniciadores de aplicaciones 3D y los logotipos de aplicaciones de Win32 VR y juegos (que se distribuyen fuera de secuencia) por lo que se muestran en el entorno de página principal y el menú Inicio de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, iniciador 3D, mosaico, cubo en vivo, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600997"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)

> [!NOTE]
> Esta característica solo está disponible para los equipos que ejecutan la versión más reciente [Windows Insider](https://insider.windows.com) vuelos (RS5), la compilación 17704 y versiones más reciente.

El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones. De forma predeterminada, juegos y aplicaciones de Win32 VR envolvente deben iniciarse desde fuera de los auriculares y no aparecerán en la lista de "Todas las aplicaciones" en el menú Inicio de Windows Mixed Reality. Sin embargo, siguiendo las instrucciones de este artículo para implementar un iniciador de aplicaciones 3D, se puede iniciar su experiencia de realidad virtual Win32 envolvente desde dentro del menú Inicio de Windows Mixed Reality y entorno doméstico.

Esto sólo es cierto para distributied de experiencias envolvente de Win32 VR fuera de secuencia. Para experiencias VR [distribuidas a través de vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), hemos [actualiza Windows Mixed Reality para SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con la última RS5 Insider de Windows vuelos para que SteamVR titles show copia en el Windows Menú de inicio de realidad mixta en la lista de "Todas las aplicaciones" automáticamente mediante un selector de forma predeterminada. En otras palabras, el método descrito en este artículo no es necesario para los títulos de SteamVR y serán reemplazado por la realidad mixta de Windows para la funcionalidad de SteamVR Beta.

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación de una aplicación 3D del iniciador

Hay 3 pasos para crear un iniciador de aplicaciones 3D:
1. [Diseñar y concepting](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. La integración en la aplicación (en este artículo)

Recursos 3D que se usará como los iniciadores para su aplicación deben crearse mediante el [Windows Mixed Reality directrices de edición](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad. Los activos que no cumplan esta especificación de creación no se representará en el inicio de Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurar el iniciador de 3D

Aplicaciones Win32 aparecerá en la lista de "Todas las aplicaciones" en el menú Inicio de Windows Mixed Reality si creas un iniciador de aplicaciones 3D para ellos. Para ello, cree un [Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) archivo XML que hacen referencia al iniciador de aplicaciones 3D siguiendo estos pasos:

1. Crear un **archivo 3D de GLB de activos de iniciador de aplicaciones** (consulte [modelado o exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Crear un **[Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para su aplicación.
    1. Puede comenzar con la [siguiente ejemplo](#sample-visual-elements-manifest).  Ver toda [Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentación para obtener más detalles.
    2. Actualización **Square150x150Logo** y **Square70x70Logo** con un PNG o JPG o GIF para la aplicación.
        * Se utilizarán para el logotipo 2D de la aplicación en la lista de realidad mixta todas las aplicaciones de Windows y para el menú Inicio en el escritorio.
        * La ruta de acceso es relativa a la carpeta que contiene el manifiesto de elementos Visual.
        * Deberá proporcionar un icono del menú Inicio del escritorio para la aplicación a través de mecanismos estándares. Esto puede ser directamente en el archivo ejecutable o en el método abreviado de que crear (por ejemplo, mediante IShellLink::SetIconLocation).
        * *Opcional:* Puede usar un archivo resources.pri si desea MRT proporcionar varios tamaños de activos para las escalas de resolución diferente y temas de contraste alto.
    3. Actualización de la **MixedRealityModel ruta** para que apunte a la GLB para su iniciador de aplicaciones de 3D
    4. Guarde el archivo con el mismo nombre que el archivo ejecutable, con la extensión ". VisualElementsManifest.xml"y guárdela en el mismo directorio. Por ejemplo, para el archivo ejecutable "contoso.exe", el archivo XML se denomina "contoso.visualelementsmanifest.xml".
3. **Agregar un acceso directo** a la aplicación en el menú de inicio de Windows desktop. Consulte la [siguiente ejemplo](#sample-app-launcher-shortcut-creation) para obtener un ejemplo C++ implementación. 
    * Cree en %ALLUSERSPROFILE%\Microsoft\Windows\Start Inicio\Programas (equipo) o %APPDATA%\Microsoft\Windows\Start Inicio\Programas (usuario)
    * Si una actualización cambia el manifiesto de elementos visuales o los activos que se hace referencia a él, el instalador o del actualizador debe actualizar el método abreviado de tal manera que se vuelven a analizar el manifiesto y se actualizan los recursos almacenados en caché.
4. *Opcional:* Si el acceso directo del escritorio no apunta directamente al archivo EXE de la aplicación (por ejemplo, si invoca un controlador de protocolo personalizado, como "myapp: / /"), el menú Inicio automáticamente no encontrará el archivo VisualElementsManifest.xml de la aplicación. Para resolver este problema, el acceso directo debe especificar la ruta de acceso de los elementos Visual manifiesto mediante () System.AppUserModel.VisualElementsManifestHintPath. Esto se puede establecer en el método abreviado con las mismas técnicas como System.AppUserModel.ID. No es necesario usar System.AppUserModel.ID pero puede hacerlo si lo desea para que el acceso directo para que coincida con el identificador de modelo de usuario de aplicación explícito de la aplicación si se usa alguno.  Consulte la [creación de accesos directos del iniciador de aplicaciones de ejemplo](#sample-app-launcher-shortcut-creation) sección a continuación para un C++ ejemplo.

### <a name="sample-visual-elements-manifest"></a>Manifiesto de elementos visuales de ejemplo

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Creación de accesos directos de iniciador aplicación de ejemplo

El código de ejemplo siguiente muestra cómo puede crear un acceso directo en C++, incluida la sustitución de la ruta de acceso al archivo XML de manifiesto de elementos de Visual. Tenga en cuenta que la invalidación solo es necesario en casos donde el acceso directo no apunta directamente al ejecutable asociado con el manifiesto (p ej. el acceso directo usa un controlador de protocolo personalizado, como "myapp: / /").

#### <a name="sample-lnk-shortcut-creation-c"></a>Ejemplo. Creación de accesos directos LNK (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Ejemplo. Acceso directo del selector de URL 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Vea también

* [Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.
* [Guía de diseño de la aplicación 3D del iniciador](3d-app-launcher-design-guidance.md)
* [Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones UWP)](implementing-3d-app-launchers.md)
* [Navegar por el inicio de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
