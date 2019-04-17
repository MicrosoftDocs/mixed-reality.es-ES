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
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="95788-104">Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="95788-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="95788-105">Esta característica solo está disponible para los equipos que ejecutan la versión más reciente [Windows Insider](https://insider.windows.com) vuelos (RS5), la compilación 17704 y versiones más reciente.</span><span class="sxs-lookup"><span data-stu-id="95788-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="95788-106">El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="95788-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="95788-107">De forma predeterminada, juegos y aplicaciones de Win32 VR envolvente deben iniciarse desde fuera de los auriculares y no aparecerán en la lista de "Todas las aplicaciones" en el menú Inicio de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="95788-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="95788-108">Sin embargo, siguiendo las instrucciones de este artículo para implementar un iniciador de aplicaciones 3D, se puede iniciar su experiencia de realidad virtual Win32 envolvente desde dentro del menú Inicio de Windows Mixed Reality y entorno doméstico.</span><span class="sxs-lookup"><span data-stu-id="95788-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="95788-109">Esto sólo es cierto para distributied de experiencias envolvente de Win32 VR fuera de secuencia.</span><span class="sxs-lookup"><span data-stu-id="95788-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="95788-110">Para experiencias VR [distribuidas a través de vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), hemos [actualiza Windows Mixed Reality para SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con la última RS5 Insider de Windows vuelos para que SteamVR titles show copia en el Windows Menú de inicio de realidad mixta en la lista de "Todas las aplicaciones" automáticamente mediante un selector de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="95788-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="95788-111">En otras palabras, el método descrito en este artículo no es necesario para los títulos de SteamVR y serán reemplazado por la realidad mixta de Windows para la funcionalidad de SteamVR Beta.</span><span class="sxs-lookup"><span data-stu-id="95788-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="95788-112">Proceso de creación de una aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="95788-112">3D app launcher creation process</span></span>

<span data-ttu-id="95788-113">Hay 3 pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="95788-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="95788-114">Diseñar y concepting</span><span class="sxs-lookup"><span data-stu-id="95788-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="95788-115">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="95788-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="95788-116">La integración en la aplicación (en este artículo)</span><span class="sxs-lookup"><span data-stu-id="95788-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="95788-117">Recursos 3D que se usará como los iniciadores para su aplicación deben crearse mediante el [Windows Mixed Reality directrices de edición](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="95788-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="95788-118">Los activos que no cumplan esta especificación de creación no se representará en el inicio de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="95788-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="95788-119">Configurar el iniciador de 3D</span><span class="sxs-lookup"><span data-stu-id="95788-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="95788-120">Aplicaciones Win32 aparecerá en la lista de "Todas las aplicaciones" en el menú Inicio de Windows Mixed Reality si creas un iniciador de aplicaciones 3D para ellos.</span><span class="sxs-lookup"><span data-stu-id="95788-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="95788-121">Para ello, cree un [Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) archivo XML que hacen referencia al iniciador de aplicaciones 3D siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="95788-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="95788-122">Crear un **archivo 3D de GLB de activos de iniciador de aplicaciones** (consulte [modelado o exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="95788-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="95788-123">Crear un **[Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="95788-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="95788-124">Puede comenzar con la [siguiente ejemplo](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="95788-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="95788-125">Ver toda [Visual elementos manifiesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentación para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="95788-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="95788-126">Actualización **Square150x150Logo** y **Square70x70Logo** con un PNG o JPG o GIF para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="95788-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="95788-127">Se utilizarán para el logotipo 2D de la aplicación en la lista de realidad mixta todas las aplicaciones de Windows y para el menú Inicio en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="95788-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="95788-128">La ruta de acceso es relativa a la carpeta que contiene el manifiesto de elementos Visual.</span><span class="sxs-lookup"><span data-stu-id="95788-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="95788-129">Deberá proporcionar un icono del menú Inicio del escritorio para la aplicación a través de mecanismos estándares.</span><span class="sxs-lookup"><span data-stu-id="95788-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="95788-130">Esto puede ser directamente en el archivo ejecutable o en el método abreviado de que crear (por ejemplo, mediante IShellLink::SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="95788-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="95788-131">*Opcional:* Puede usar un archivo resources.pri si desea MRT proporcionar varios tamaños de activos para las escalas de resolución diferente y temas de contraste alto.</span><span class="sxs-lookup"><span data-stu-id="95788-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="95788-132">Actualización de la **MixedRealityModel ruta** para que apunte a la GLB para su iniciador de aplicaciones de 3D</span><span class="sxs-lookup"><span data-stu-id="95788-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="95788-133">Guarde el archivo con el mismo nombre que el archivo ejecutable, con la extensión ". VisualElementsManifest.xml"y guárdela en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="95788-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="95788-134">Por ejemplo, para el archivo ejecutable "contoso.exe", el archivo XML se denomina "contoso.visualelementsmanifest.xml".</span><span class="sxs-lookup"><span data-stu-id="95788-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="95788-135">**Agregar un acceso directo** a la aplicación en el menú de inicio de Windows desktop.</span><span class="sxs-lookup"><span data-stu-id="95788-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="95788-136">Consulte la [siguiente ejemplo](#sample-app-launcher-shortcut-creation) para obtener un ejemplo C++ implementación.</span><span class="sxs-lookup"><span data-stu-id="95788-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="95788-137">Cree en %ALLUSERSPROFILE%\Microsoft\Windows\Start Inicio\Programas (equipo) o %APPDATA%\Microsoft\Windows\Start Inicio\Programas (usuario)</span><span class="sxs-lookup"><span data-stu-id="95788-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="95788-138">Si una actualización cambia el manifiesto de elementos visuales o los activos que se hace referencia a él, el instalador o del actualizador debe actualizar el método abreviado de tal manera que se vuelven a analizar el manifiesto y se actualizan los recursos almacenados en caché.</span><span class="sxs-lookup"><span data-stu-id="95788-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="95788-139">*Opcional:* Si el acceso directo del escritorio no apunta directamente al archivo EXE de la aplicación (por ejemplo, si invoca un controlador de protocolo personalizado, como "myapp: / /"), el menú Inicio automáticamente no encontrará el archivo VisualElementsManifest.xml de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="95788-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="95788-140">Para resolver este problema, el acceso directo debe especificar la ruta de acceso de los elementos Visual manifiesto mediante () System.AppUserModel.VisualElementsManifestHintPath.</span><span class="sxs-lookup"><span data-stu-id="95788-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="95788-141">Esto se puede establecer en el método abreviado con las mismas técnicas como System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="95788-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="95788-142">No es necesario usar System.AppUserModel.ID pero puede hacerlo si lo desea para que el acceso directo para que coincida con el identificador de modelo de usuario de aplicación explícito de la aplicación si se usa alguno.</span><span class="sxs-lookup"><span data-stu-id="95788-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="95788-143">Consulte la [creación de accesos directos del iniciador de aplicaciones de ejemplo](#sample-app-launcher-shortcut-creation) sección a continuación para un C++ ejemplo.</span><span class="sxs-lookup"><span data-stu-id="95788-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="95788-144">Manifiesto de elementos visuales de ejemplo</span><span class="sxs-lookup"><span data-stu-id="95788-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="95788-145">Creación de accesos directos de iniciador aplicación de ejemplo</span><span class="sxs-lookup"><span data-stu-id="95788-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="95788-146">El código de ejemplo siguiente muestra cómo puede crear un acceso directo en C++, incluida la sustitución de la ruta de acceso al archivo XML de manifiesto de elementos de Visual.</span><span class="sxs-lookup"><span data-stu-id="95788-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="95788-147">Tenga en cuenta que la invalidación solo es necesario en casos donde el acceso directo no apunta directamente al ejecutable asociado con el manifiesto (p ej.</span><span class="sxs-lookup"><span data-stu-id="95788-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="95788-148">el acceso directo usa un controlador de protocolo personalizado, como "myapp: / /").</span><span class="sxs-lookup"><span data-stu-id="95788-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="95788-149">Ejemplo. Creación de accesos directos LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="95788-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="95788-150">Ejemplo. Acceso directo del selector de URL</span><span class="sxs-lookup"><span data-stu-id="95788-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="95788-151">Vea también</span><span class="sxs-lookup"><span data-stu-id="95788-151">See also</span></span>

* <span data-ttu-id="95788-152">[Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="95788-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="95788-153">Guía de diseño de la aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="95788-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="95788-154">Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="95788-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="95788-155">Implementación de iniciadores de aplicaciones 3D (aplicaciones UWP)</span><span class="sxs-lookup"><span data-stu-id="95788-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="95788-156">Navegar por el inicio de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="95788-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
