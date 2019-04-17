---
title: Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)
description: Cómo crear los iniciadores de aplicaciones 3D y los logotipos de Windows Mixed Reality UWP aplicaciones y juegos (que se distribuyen a través de la Microsoft Store), tanto en HoloLens e inmersivos (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, iniciador 3D, mosaico, cubo en vivo, vínculo profundo, secondarytile, mosaico secundario, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605735"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)

> [!NOTE]
> Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para inmersivos y es compatible con HoloLens con Windows Update 10 de abril de 2018. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.16299 en Inmersivos y 10.0.17125 en HoloLens. Puede encontrar el SDK de Windows más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones. Al crear una aplicación de UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras 2D con el logotipo de su aplicación. Al desarrollar experiencias para Windows Mixed Reality, opcionalmente, puede definirse un iniciador 3D para invalidar el iniciador 2D predeterminado para la aplicación. En general, se recomiendan los iniciadores de 3D para iniciar aplicaciones envolventes que llevará a los usuarios fuera de Windows Mixed Reality principal, mientras que el iniciador 2D predeterminada es preferible cuando se activa la aplicación en su lugar. También puede crear un [vínculo profundo 3D (secondaryTile)](#3d-deep-links-secondarytiles) como un selector de 3D al contenido dentro de una aplicación para UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación de una aplicación 3D del iniciador

Hay 3 pasos para crear un iniciador de aplicaciones 3D:
1. [Diseñar y concepting](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. La integración en la aplicación (en este artículo)

Recursos 3D que se usará como los iniciadores para su aplicación deben crearse mediante el [Windows Mixed Reality directrices de edición](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad. Los activos que no cumplan esta especificación de creación no se representará en el inicio de Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurar el iniciador de 3D

Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación. Para reemplazar este 2D representación con un modelo 3D personalizado editar el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición de mosaico predeterminado. Para revertir a la 2D iniciador simplemente quite la definición de MixedRealityModel del manifiesto.

### <a name="xml"></a>XML

En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual. De forma predeterminada, el manifiesto se denominará Package.appxmanifest. Si usa Visual Studio, a continuación, haga clic en el manifiesto en el Visor de la solución y seleccione **ver código fuente** para abrir el código xml para su edición. 

En la parte superior del manifiesto, agregue el esquema uap5 e inclúyalo como un espacio de nombres puede pasar por alto:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

A continuación, especifique el "MixedRealityModel" en el icono predeterminado para la aplicación:

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

Los elementos MixedRealityModel acepta una ruta de acceso que apunta a un recurso 3D almacenado en el paquete de aplicación. Actualmente los modelos 3D sólo entregan mediante el formato de archivo .glb y escriben contra la [instrucciones de creación de activos 3D de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) son compatibles. Activos deben almacenarse en el paquete de aplicación y la animación no se admite actualmente. Si se deja en blanco el parámetro "Path" Windows mostrará la Pizarra 2D en lugar del iniciador de 3D. **Nota:** .glb activo debe estar marcado como "Contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.


![Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarla como "Contenido" en la configuración de compilación](images/buildsetting-content-300px.png)<br>
*Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarla como "Contenido" en la configuración de compilación*

### <a name="bounding-box"></a>Cuadro de límite

Un cuadro de límite se puede usar para agregar, opcionalmente, una región de un búfer adicional alrededor del objeto. El cuadro de límite se especifica mediante un punto central y las extensiones que indican la distancia desde el centro del cuadro de límite para los bordes en cada eje. Se pueden asignar unidades para el cuadro de límite a 1 unidad = 1 metro. Si no se proporciona un cuadro de límite, a continuación, uno se se ajustan automáticamente a la malla del objeto. Si el rectángulo proporcionado es menor que el modelo, se ajustará para ajustarse a la malla.

Compatibilidad con el atributo de cuadro de límite viene con la actualización de Windows RS4 como una propiedad en el elemento MixedRealityModel. Para definir un rectángulo en primer lugar en la parte superior de la aplicación de manifiesto, agregue el esquema uap6 e inclúyalo como espacios de nombres puede pasar por alto:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
A continuación, en el MixedRealityModel establezca la propiedad SpatialBoundingBox para definir el cuadro de límite: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Uso de Unity

Cuando se trabaja con Unity el proyecto debe compilado y se abre en Visual Studio antes de que se puede editar el manifiesto de aplicación. 

>[!NOTE]
>Debe volver a definir el iniciador de 3D en el manifiesto al compilar e implementar una nueva solución de Visual Studio desde Unity.

## <a name="3d-deep-links-secondarytiles"></a>3D profundo vincula (secondaryTiles)

> [!NOTE]
> Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para inmersivos (VR) y como parte de la de abril de 2018 actualización (RS4) para HoloLens. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.16299 en inmersivos (VR) y 10.0.17125 en HoloLens. Puede encontrar el SDK de Windows más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>Vínculos profundos 3D (secondaryTiles) solo funcionan con las aplicaciones para UWP 2D. Sin embargo, puede crear un [iniciador de aplicaciones 3D](implementing-3d-app-launchers.md) para iniciar una aplicación desde el inicio de Windows Mixed Reality exclusivo.

Se pueden mejorar sus aplicaciones 2D para Windows Mixed Reality agregando la capacidad para colocar los modelos 3D de la aplicación en el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) como vínculos profundos a contenido dentro de la aplicación 2D, al igual que [secundaria 2D iconos](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) en el menú Inicio de Windows. Por ejemplo, puede crear photospheres de 360° que vinculan directamente en una aplicación de Visor de fotos de 360° o que los usuarios puedan colocar contenido 3D de una colección de recursos que se abre una página de detalles acerca del autor. Estos son sólo un par de formas para expandir la funcionalidad de la aplicación 2D con contenido 3D.

### <a name="creating-a-3d-secondarytile"></a>Creación de un "secondaryTile" 3D

Puede colocar contenido 3D de la aplicación mediante "secondaryTiles" mediante la definición de un modelo de realidad mixta en tiempo de creación. Se crean modelos de realidad mixta haciendo referencia a un recurso de 3D en el paquete de aplicación y, opcionalmente, definir un rectángulo de selección. 

> [!NOTE]
> No se admite actualmente la creación de "secondaryTiles" desde dentro de una vista exclusiva.

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

Un cuadro de límite se puede usar para agregar una región de un búfer adicional alrededor del objeto. El cuadro de límite se especifica mediante un punto central y las extensiones que indican la distancia desde el centro del cuadro de límite para los bordes en cada eje. Se pueden asignar unidades para el cuadro de límite a 1 unidad = 1 metro. Si no se proporciona un cuadro de límite, a continuación, uno se se ajustan automáticamente a la malla del objeto. Si el rectángulo proporcionado es menor que el modelo, se ajustará para ajustarse a la malla.

### <a name="activation-behavior"></a>Comportamiento de activación

> [!NOTE]
> Esta característica se admitirá a partir de la actualización de Windows RS4. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor que o igual que 10.0.17125 si va a usar esta característica

Puede definir el comportamiento de activación para un secondaryTile 3D controlar cómo reacciona cuando un usuario lo selecciona. Esto puede utilizarse para colocar objetos 3D en la realidad mixta principal que son purley decorativo o informativo. Se admiten los siguientes tipos de comportamiento de activación:
1. Default: Cuando un usuario selecciona el secondaryTile 3D se activa la aplicación
2. Ninguno: No se activa cuando el usuario selecciona el secondaryTile 3D no ocurre nada y la aplicación.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Obtener y actualizar una existente "secondaryTile"

Los desarrolladores pueden obtener una lista de sus iconos secundarios existentes, que incluye las propiedades que ha especificado anteriormente. También puede actualizar las propiedades cambiando el valor y, a continuación, llamar a UpdateAsync().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Comprobando que el usuario está en Windows Mixed Reality

Solo se pueden crear vínculos profundos 3D (secondaryTiles) mientras se muestra la vista en auriculares de realidad mixta de Windows. Cuando la vista no es que se presenta en auriculares de realidad mixta de Windows, se recomienda tratar correctamente de eso por ocultar el punto de entrada o mostrar un mensaje de error. Puede comprobarlo mediante la consulta [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notificaciones de icono

Las notificaciones de icono no admiten actualmente enviar una actualización con un recurso de 3D. Esto significa que los desarrolladores no podrán hacer lo siguiente
* Notificaciones de inserción
* Sondeo periódico
* Notificaciones programadas

Para obtener más información sobre los otros iconos de las características y los atributos y cómo se usan para los iconos 2D hacen referencia a la [iconos para la documentación de aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Vea también

* [Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.
* [Guía de diseño de la aplicación 3D del iniciador](3d-app-launcher-design-guidance.md)
* [Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Navegar por el inicio de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
