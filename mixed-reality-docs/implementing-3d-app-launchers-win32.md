---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)
description: Cómo crear iniciadores de aplicaciones 3D y logotipos para aplicaciones y juegos de Win32 VR (distribuidos fuera del vapor) para que aparezcan en el menú Inicio y en el entorno de inicio de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, selector 3D, mosaico, cubo activo, Win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515605"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)

> [!NOTE]
> Esta característica solo está disponible para los equipos que ejecutan la versión más reciente de [Windows](https://insider.windows.com) Insider (RS5), compilación 17704 y versiones más recientes.

La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones. De forma predeterminada, las aplicaciones y juegos envolventes de Win32 VR deben iniciarse desde fuera del casco y no aparecerán en la lista "todas las aplicaciones" del menú Inicio de Windows Mixed Reality. Sin embargo, al seguir las instrucciones de este artículo para implementar un iniciador de aplicaciones 3D, la experiencia de Win32 VR envolvente se puede iniciar desde el menú Inicio y el entorno de inicio de Windows Mixed Reality.

Esto solo es válido para las experiencias de Win32 VR envolventes distributied fuera de la secuencia. En el caso de las experiencias de VR [distribuidas a través de vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), hemos [actualizado Windows Mixed Reality para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con los vuelos de Windows Insider RS5 más recientes para que los títulos de SteamVR aparezcan en el menú Inicio de Windows Mixed Reality en la lista "todas las aplicaciones". usar automáticamente un iniciador predeterminado. En otras palabras, el método descrito en este artículo no es necesario para los títulos de SteamVR y se reemplazará por la funcionalidad de Windows Mixed Reality para SteamVR beta.

## <a name="3d-app-launcher-creation-process"></a>proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:
1. [Diseño y concepto](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación (este artículo)

los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las [directrices de creación de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad. Los recursos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurar el iniciador 3D

Las aplicaciones Win32 aparecerán en la lista "todas las aplicaciones" del menú Inicio de Windows Mixed Reality si crea un selector de aplicaciones 3D para ellas. Para ello, cree un archivo XML de [manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) que haga referencia al iniciador de aplicaciones 3D siguiendo estos pasos:

1. Cree un **archivo glb de activo del iniciador de aplicaciones 3D** (consulte [modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Cree un **[manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para la aplicación.
    1. Puede empezar con el [ejemplo siguiente](#sample-visual-elements-manifest).  Consulte la documentación del [manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) completos para obtener más detalles.
    2. Actualice **Square150x150Logo** y **Square70x70Logo** con un archivo PNG/JPG/GIF para la aplicación.
        * Se usarán para el logotipo de 2D de la aplicación en la lista todas las aplicaciones de Windows Mixed Reality y para el menú Inicio en el escritorio.
        * La ruta de acceso del archivo es relativa a la carpeta que contiene el manifiesto de elementos visuales.
        * Todavía tiene que proporcionar un icono de menú Inicio de escritorio para la aplicación a través de los mecanismos estándar. Puede estar directamente en el archivo ejecutable o en el acceso directo que cree (por ejemplo, a través de IShellLink:: SetIconLocation).
        * *Opta* Puede usar un archivo resources. PRI si desea que MRT proporcione varios tamaños de recursos para diferentes escalas de resolución y temas de contraste alto.
    3. Actualice la **ruta de acceso de MixedRealityModel** para que apunte al glb del iniciador de la aplicación 3D.
    4. Guarde el archivo con el mismo nombre que el archivo ejecutable, con la extensión ". VisualElementsManifest. xml "y guárdelo en el mismo directorio. Por ejemplo, para el archivo ejecutable "contoso. exe", el archivo XML que lo acompaña se denomina "contoso. visualelementsmanifest. xml".
3. **Agregue un acceso directo** a la aplicación en el menú Inicio de Windows de escritorio. Vea el [ejemplo siguiente](#sample-app-launcher-shortcut-creation) para obtener una C++ implementación de ejemplo. 
    * Créelo en%ALLUSERSPROFILE%\Microsoft\Windows\Start Inicio\programas (equipo) o en el Inicio\programas de%APPDATA%\Microsoft\Windows\Start (usuario)
    * Si una actualización cambia el manifiesto de los elementos visuales o los recursos a los que hace referencia, el instalador o actualizador debe actualizar el acceso directo para que el manifiesto se analice y se actualicen los recursos almacenados en caché.
4. *Opta* Si el acceso directo del escritorio no apunta directamente al archivo EXE de la aplicación (por ejemplo, si invoca un controlador de protocolo personalizado como "myapp://"), el menú Inicio no buscará automáticamente el archivo VisualElementsManifest. XML de la aplicación. Para resolverlo, el acceso directo debe especificar la ruta de acceso del archivo del manifiesto de elementos visuales con System. AppUserModel. VisualElementsManifestHintPath (). Se puede establecer en el acceso directo con las mismas técnicas que System.AppUserModel.ID. No es necesario usar System.AppUserModel.ID, pero puede hacerlo si desea que el acceso directo coincida con el identificador de modelo de usuario de aplicación explícito de la aplicación si se usa uno.  Vea la sección [creación de acceso directo](#sample-app-launcher-shortcut-creation) del iniciador de C++ aplicaciones de ejemplo siguiente para obtener un ejemplo.

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

### <a name="sample-app-launcher-shortcut-creation"></a>Creación de un acceso directo del iniciador de aplicaciones de ejemplo

En el código de ejemplo siguiente se muestra cómo se puede crear C++un acceso directo en, incluida la invalidación de la ruta de acceso al archivo XML de manifiesto de los elementos visuales. Tenga en cuenta que la invalidación solo es necesaria en los casos en los que el acceso directo no apunta directamente al archivo EXE asociado con el manifiesto (por ejemplo, el acceso directo usa un controlador de protocolo personalizado como "myapp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>AdventureWorks. Creación de accesosC++directos de lnk ()

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

#### <a name="sample-url-launcher-shortcut"></a>AdventureWorks. Acceso directo del iniciador de URL 

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
* [Guía de diseño del iniciador de aplicaciones 3D](3d-app-launcher-design-guidance.md)
* [Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
