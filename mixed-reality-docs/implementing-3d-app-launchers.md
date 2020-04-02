---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)
description: Cómo crear iniciadores de aplicaciones 3D y logotipos para aplicaciones y juegos UWP de Windows Mixed Reality (distribuidos a través de la Microsoft Store), tanto en los auriculares HoloLens como envolventes (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, selector 3D, mosaico, cubo activo, vínculo profundo, secondarytile, icono secundario, UWP
ms.openlocfilehash: 0a2e2177ffa7e381c461a58f373c818c9c5e72c4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549388"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)

> [!NOTE]
> Esta característica se agregó como parte de la actualización de 2017 Fall Creators Update (RS3) para los auriculares más envolventes y es compatible con HoloLens con la actualización de Windows 10 de abril de 2018. Asegúrese de que la aplicación tiene como destino una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo y 10.0.17125 en HoloLens. Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones. Al crear una aplicación para UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras bidimensionales con el logotipo de su aplicación. Al desarrollar experiencias para Windows Mixed Reality, opcionalmente se puede definir un selector 3D para invalidar el iniciador de 2D predeterminado de la aplicación. En general, los iniciadores 3D se recomiendan para iniciar aplicaciones envolventes que sacan provecho de la Página principal de Windows Mixed Reality, mientras que el selector de 2D predeterminado es preferible cuando la aplicación se activa en su lugar. También puede crear un [vínculo profundo en 3D (secondaryTile)](#3d-deep-links-secondarytiles) como un selector 3D para el contenido de una aplicación de UWP en 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:
1. [Diseño y concepto](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación (este artículo)

los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las [directrices de creación de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad. Los recursos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurar el iniciador 3D

Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación. Para reemplazar esta representación 2D por un modelo 3D personalizado, edite el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición del mosaico predeterminado. Para revertir al iniciador de 2D, solo tiene que quitar la definición de MixedRealityModel del manifiesto.

### <a name="xml"></a>XML

En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual. De forma predeterminada, el manifiesto se denominará package. appxmanifest. Si usa Visual Studio, haga clic con el botón derecho en el manifiesto en el visor de soluciones y seleccione **Ver código fuente** para abrir el código XML y editarlo. 

En la parte superior del manifiesto, agregue el esquema uap5 e inclúyalo como un espacio de nombres que se va a omitir:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

A continuación, especifique "MixedRealityModel" en el icono predeterminado de la aplicación:

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

Los elementos MixedRealityModel aceptan una ruta de acceso de archivo que apunta a un recurso 3D almacenado en el paquete de la aplicación. Actualmente solo se admiten los modelos 3D que se entregan con el formato de archivo. glb y se crean con las [instrucciones de creación de recursos de Windows Mixed Reality 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) . Los recursos deben almacenarse en el paquete de la aplicación y la animación no se admite actualmente. Si el parámetro "path" se deja en blanco, Windows mostrará la pizarra 2D en lugar del iniciador 3D. **Nota:** el recurso. glb debe estar marcado como "contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.


![seleccione. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación](images/buildsetting-content-300px.png)<br>
*Seleccione el. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación.*

### <a name="bounding-box"></a>Cuadro de límite

Un cuadro de límite se puede usar para agregar opcionalmente una región de búfer adicional alrededor del objeto. El cuadro de límite se especifica utilizando un punto central y extensiones que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje. Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro. Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto. Si el cuadro de límite proporcionado es menor que el modelo, se cambiará el tamaño para ajustarse a la malla.

La compatibilidad con el atributo de cuadro de límite incluirá la actualización de RS4 de Windows como una propiedad en el elemento MixedRealityModel. Para definir un cuadro de límite primero en la parte superior del manifiesto de la aplicación, agregue el esquema uap6 e inclúyalo como espacios de nombres que se puedan omitir:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
A continuación, en MixedRealityModel, establezca la propiedad SpatialBoundingBox para definir el cuadro de límite: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Uso de Unity

Al trabajar con Unity, el proyecto se debe compilar y abrir en Visual Studio para poder editar el manifiesto de la aplicación. 

>[!NOTE]
>El iniciador 3D debe volver a definirse en el manifiesto al compilar e implementar una nueva solución de Visual Studio desde Unity.

## <a name="3d-deep-links-secondarytiles"></a>vínculos profundos 3D (secondaryTiles)

> [!NOTE]
> Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para auriculares envolventes (VR) y como parte de la actualización de abril de 2018 (RS4) para HoloLens. Asegúrese de que la aplicación esté destinada a una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo (VR) y 10.0.17125 en HoloLens. Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>los vínculos profundos 3D (secondaryTiles) solo funcionan con aplicaciones UWP de 2D. Sin embargo, puede crear un [iniciador de aplicaciones 3D](implementing-3d-app-launchers.md) para iniciar una aplicación exclusiva desde la Página principal de Windows Mixed Reality.

Las aplicaciones 2D se pueden mejorar para Windows Mixed Reality agregando la capacidad de colocar modelos 3D desde la aplicación en la [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) como vínculos profundos al contenido dentro de la aplicación 2D, al igual que los [mosaicos secundarios 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) en el menú Inicio de Windows. Por ejemplo, puede crear fotoesferas 360 ° que se vinculan directamente a una aplicación de visor de fotos de 360 °, o bien permitir que los usuarios coloquen contenido 3D de una colección de recursos que abre una página de detalles sobre el autor. Se trata de un par de formas de ampliar la funcionalidad de la aplicación 2D con contenido 3D.

### <a name="creating-a-3d-secondarytile"></a>Crear un "secondaryTile" 3D

Puede colocar contenido 3D de la aplicación mediante "secondaryTiles" definiendo un modelo de realidad mixta en el momento de la creación. Los modelos de realidad mixta se crean haciendo referencia a un recurso 3D en el paquete de la aplicación y definiendo opcionalmente un cuadro de límite. 

> [!NOTE]
> Actualmente no se admite la creación de "secondaryTiles" desde una vista exclusiva.

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>Cuadro de límite

Un cuadro de límite se puede usar para agregar una región de búfer adicional alrededor del objeto. El cuadro de límite se especifica utilizando un punto central y extensiones que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje. Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro. Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto. Si el cuadro de límite proporcionado es menor que el modelo, se cambiará el tamaño para ajustarse a la malla.

### <a name="activation-behavior"></a>Comportamiento de activación

> [!NOTE]
> Esta característica se admitirá a partir de la actualización de RS4 de Windows. Asegúrese de que la aplicación tenga como destino una versión de la Windows SDK mayor o igual que 10.0.17125 si tiene previsto usar esta característica.

Puede definir el comportamiento de activación de un secondaryTile de 3D para controlar cómo reacciona cuando un usuario lo selecciona. Se puede usar para colocar objetos 3D en la Página principal de la realidad mixta que son meramente informativas o decorativas. Se admiten los siguientes tipos de comportamiento de activación:
1. Valor predeterminado: cuando un usuario selecciona el secondaryTile 3D, se activa la aplicación
2. Ninguno: cuando los usuarios seleccionan el secondaryTile 3D, no sucede nada y la aplicación no está activada.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Obtener y actualizar un "secondaryTile" existente

Los desarrolladores pueden volver a obtener una lista de los mosaicos secundarios existentes, que incluye las propiedades especificadas anteriormente. También pueden actualizar las propiedades cambiando el valor y llamando a UpdateAsync ().

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Comprobar que el usuario está en Windows Mixed Reality

solo se pueden crear vínculos profundos 3D (secondaryTiles) mientras la vista se muestra en un casco de realidad mixta de Windows. Cuando la vista no se presenta en un casco de realidad mixta de Windows, se recomienda controlarlo correctamente ocultando el punto de entrada o mostrando un mensaje de error. Para comprobarlo, consulte [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notificaciones de icono

Las notificaciones de icono no admiten actualmente el envío de una actualización con un recurso 3D. Esto significa que los desarrolladores no podrán hacer lo siguiente
* Notificaciones de inserción
* Sondeo periódico
* Notificaciones programadas

Para obtener más información sobre los demás iconos y características, y cómo se usan para los mosaicos de 2D, consulte la [documentación de iconos de aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Vea también

* [Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.
* [Guía de diseño del iniciador de aplicaciones 3D](3d-app-launcher-design-guidance.md)
* [Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
