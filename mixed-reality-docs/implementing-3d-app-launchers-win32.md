---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)
description: Cómo crear iniciadores de aplicaciones 3D y logotipos para aplicaciones y juegos de Win32 VR (distribuidos fuera del vapor) para que aparezcan en el menú Inicio y en el entorno de inicio de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, selector 3D, mosaico, cubo activo, Win32
ms.openlocfilehash: 87eadfb5184f9fb5f8d513ab00a2a954e71df376
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438576"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="a9366-104">Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="a9366-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="a9366-105">Esta característica solo está disponible para los equipos que ejecutan la versión más reciente de [Windows Insider](https://insider.windows.com) (RS5), compilación 17704 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="a9366-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="a9366-106">La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a9366-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="a9366-107">De forma predeterminada, las aplicaciones y juegos envolventes de Win32 VR deben iniciarse desde fuera del casco y no aparecerán en la lista "todas las aplicaciones" del menú Inicio de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9366-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="a9366-108">Sin embargo, al seguir las instrucciones de este artículo para implementar un iniciador de aplicaciones 3D, la experiencia de Win32 VR envolvente se puede iniciar desde el menú Inicio y el entorno de inicio de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9366-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="a9366-109">Esto solo es válido para las experiencias de Win32 VR envolventes distributied fuera de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="a9366-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="a9366-110">En el caso de las experiencias de VR [distribuidas a través de vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), hemos [actualizado Windows Mixed Reality para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con los vuelos de Windows Insider RS5 más recientes para que los títulos de SteamVR aparezcan en el menú Inicio de Windows Mixed Reality en la lista "todas las aplicaciones". usar automáticamente un iniciador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="a9366-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="a9366-111">En otras palabras, el método descrito en este artículo no es necesario para los títulos de SteamVR y se reemplazará por la funcionalidad de Windows Mixed Reality para SteamVR beta.</span><span class="sxs-lookup"><span data-stu-id="a9366-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="a9366-112">proceso de creación del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="a9366-112">3D app launcher creation process</span></span>

<span data-ttu-id="a9366-113">Hay tres pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="a9366-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="a9366-114">Diseño y concepto</span><span class="sxs-lookup"><span data-stu-id="a9366-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="a9366-115">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="a9366-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="a9366-116">Integrarlo en la aplicación (este artículo)</span><span class="sxs-lookup"><span data-stu-id="a9366-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="a9366-117">los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las [directrices de creación de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="a9366-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="a9366-118">Los recursos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a9366-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="a9366-119">Configurar el iniciador 3D</span><span class="sxs-lookup"><span data-stu-id="a9366-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="a9366-120">Las aplicaciones Win32 aparecerán en la lista "todas las aplicaciones" del menú Inicio de Windows Mixed Reality si crea un selector de aplicaciones 3D para ellas.</span><span class="sxs-lookup"><span data-stu-id="a9366-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="a9366-121">Para ello, cree un archivo XML de [manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) que haga referencia al iniciador de aplicaciones 3D siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a9366-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="a9366-122">Cree un **archivo glb de activo del iniciador de aplicaciones 3D** (consulte [modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="a9366-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="a9366-123">Cree un **[manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9366-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="a9366-124">Puede empezar con el [ejemplo siguiente](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="a9366-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="a9366-125">Consulte la documentación del [manifiesto de elementos visuales](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) completos para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="a9366-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="a9366-126">Actualice **Square150x150Logo** y **Square70x70Logo** con un archivo PNG/JPG/GIF para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9366-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="a9366-127">Se usarán para el logotipo de 2D de la aplicación en la lista todas las aplicaciones de Windows Mixed Reality y para el menú Inicio en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="a9366-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="a9366-128">La ruta de acceso del archivo es relativa a la carpeta que contiene el manifiesto de elementos visuales.</span><span class="sxs-lookup"><span data-stu-id="a9366-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="a9366-129">Todavía tiene que proporcionar un icono de menú Inicio de escritorio para la aplicación a través de los mecanismos estándar.</span><span class="sxs-lookup"><span data-stu-id="a9366-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="a9366-130">Puede estar directamente en el archivo ejecutable o en el acceso directo que cree (por ejemplo, a través de IShellLink:: SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="a9366-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="a9366-131">*Opcional:* Puede usar un archivo resources. PRI si desea que MRT proporcione varios tamaños de recursos para diferentes escalas de resolución y temas de contraste alto.</span><span class="sxs-lookup"><span data-stu-id="a9366-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="a9366-132">Actualice la **ruta de acceso de MixedRealityModel** para que apunte al glb del iniciador de la aplicación 3D.</span><span class="sxs-lookup"><span data-stu-id="a9366-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="a9366-133">Guarde el archivo con el mismo nombre que el archivo ejecutable, con la extensión ". VisualElementsManifest. xml "y guárdelo en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="a9366-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="a9366-134">Por ejemplo, para el archivo ejecutable "contoso. exe", el archivo XML que lo acompaña se denomina "contoso. visualelementsmanifest. xml".</span><span class="sxs-lookup"><span data-stu-id="a9366-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="a9366-135">**Agregue un acceso directo** a la aplicación en el menú Inicio de Windows de escritorio.</span><span class="sxs-lookup"><span data-stu-id="a9366-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="a9366-136">Vea el [ejemplo siguiente](#sample-app-launcher-shortcut-creation) para obtener una C++ implementación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a9366-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="a9366-137">Créelo en%ALLUSERSPROFILE%\Microsoft\Windows\Start Inicio\programas (equipo) o en el Inicio\programas de%APPDATA%\Microsoft\Windows\Start (usuario)</span><span class="sxs-lookup"><span data-stu-id="a9366-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="a9366-138">Si una actualización cambia el manifiesto de los elementos visuales o los recursos a los que hace referencia, el instalador o actualizador debe actualizar el acceso directo para que el manifiesto se analice y se actualicen los recursos almacenados en caché.</span><span class="sxs-lookup"><span data-stu-id="a9366-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="a9366-139">*Opcional:* Si el acceso directo del escritorio no apunta directamente al archivo EXE de la aplicación (por ejemplo, si invoca un controlador de protocolo personalizado como "myapp://"), el menú Inicio no buscará automáticamente el archivo VisualElementsManifest. XML de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9366-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="a9366-140">Para resolverlo, el acceso directo debe especificar la ruta de acceso del archivo del manifiesto de elementos visuales con System. AppUserModel. VisualElementsManifestHintPath ().</span><span class="sxs-lookup"><span data-stu-id="a9366-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="a9366-141">Se puede establecer en el acceso directo con las mismas técnicas que System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="a9366-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="a9366-142">No es necesario usar System.AppUserModel.ID, pero puede hacerlo si desea que el acceso directo coincida con el identificador de modelo de usuario de aplicación explícito de la aplicación si se usa uno.</span><span class="sxs-lookup"><span data-stu-id="a9366-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="a9366-143">Vea la sección [creación de acceso directo del iniciador de aplicaciones de ejemplo](#sample-app-launcher-shortcut-creation) siguiente para obtener un C++ ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a9366-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="a9366-144">Manifiesto de elementos visuales de ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9366-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="a9366-145">Creación de un acceso directo del iniciador de aplicaciones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9366-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="a9366-146">En el código de ejemplo siguiente se muestra cómo se puede crear C++un acceso directo en, incluida la invalidación de la ruta de acceso al archivo XML de manifiesto de los elementos visuales.</span><span class="sxs-lookup"><span data-stu-id="a9366-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="a9366-147">Tenga en cuenta que la invalidación solo es necesaria en los casos en los que el acceso directo no apunta directamente al archivo EXE asociado con el manifiesto (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="a9366-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="a9366-148">el acceso directo usa un controlador de protocolo personalizado como "myapp://").</span><span class="sxs-lookup"><span data-stu-id="a9366-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="a9366-149">AdventureWorks. Creación de accesosC++directos de lnk ()</span><span class="sxs-lookup"><span data-stu-id="a9366-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="a9366-150">AdventureWorks. Acceso directo del iniciador de URL</span><span class="sxs-lookup"><span data-stu-id="a9366-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="a9366-151">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a9366-151">See also</span></span>

* <span data-ttu-id="a9366-152">[Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="a9366-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="a9366-153">Guía de diseño del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="a9366-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="a9366-154">Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a9366-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="a9366-155">Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)</span><span class="sxs-lookup"><span data-stu-id="a9366-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="a9366-156">Desplazamiento por la página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a9366-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
