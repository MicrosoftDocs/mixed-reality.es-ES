---
title: Permitir la colocación de los modelos 3D en la página principal
description: Cómo colocar los modelos 3D del sitio Web o aplicación en el inicio de Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar en la página principal, lugar, mundo, modelado, realidad mixta doméstica, web, aplicación
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829734"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Permitir la colocación de los modelos 3D en la realidad mixta principal

> [!NOTE]
> Esta característica se agregó como parte de la [Windows 10 de abril de 2018 Update](release-notes-april-2018.md). Las versiones anteriores de Windows no son compatibles con esta característica.

El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones. En algunos escenarios, las aplicaciones 2D (por ejemplo, la aplicación hologramas) permiten la colocación de los modelos 3D directamente en la página principal de realidad mixta como adornos, o para que lo inspeccione en 3D. El *Agregar modelo protocolo* le permite enviar un modelo 3D desde su sitio Web o aplicación directamente en el hogar de Windows Mixed Reality donde conservará como [los iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md), aplicaciones 2D y hologramas. 

Por ejemplo, si está desarrollando una aplicación que muestre un catálogo de muebles 3D para el diseño de un espacio, puede usar el *Agregar modelo protocolo* para permitir que los usuarios que coloquen esos modelos 3D muebles desde el catálogo. Una vez colocado en el mundo, los usuarios pueden mover, cambiar el tamaño y quitar estos modelos 3D, al igual que otros hologramas en la página principal. Este artículo proporciona información general de la implementación de la *Agregar modelo protocolo* para que pueda empezar permitiendo a los usuarios decorar su mundo con objetos 3D de la aplicación o la web.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Agregue el protocolo del modelo</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Información general

Hay 2 pasos para habilitar la colocación de los modelos 3D en Windows Mixed Reality principal:
1. [Asegúrese de que el modelo en 3D es compatible con el inicio de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implemente el *Agregar modelo protocolo* en su aplicación o página Web (en este artículo).

## <a name="implementing-the-add-model-protocol"></a>Implementar el *Agregar protocolo del modelo*

Una vez que tenga un [modelo 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), puede implementar la *Agregar modelo protocolo* activando el siguiente URI desde cualquier página Web o aplicación:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Si el URI apunta a un recurso remoto, a continuación, automáticamente se descargan y coloca en la página principal. Los recursos locales se copiará en la carpeta de datos de aplicación de la casa de realidad mixta antes de que se va a colocar en la página principal. Se recomienda diseñar su experiencia a la cuenta para escenarios donde el usuario podría estar ejecutando una versión anterior de Windows que no es compatible con esta característica mediante el botón de ocultación o deshabilitación de, si es posible. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Invocar el *Agregar modelo protocolo* desde una aplicación de plataforma Universal de Windows:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Invocar el *Agregar modelo protocolo* desde una página Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Consideraciones para inmersivos (VR)

* Para inmersivos (VR), el Portal de realidad mixta no tiene que estar ejecutándose antes de invocar el *Agregar modelo protocolo*. En este caso, el *Agregar modelo protocolo* iniciará el Portal de realidad mixta y colocar el objeto directamente donde los auriculares está buscando una vez que llegue a la realidad mixta principal. 
* Al invocar el *Agregar modelo protocolo* desde el escritorio con el Portal de realidad mixta ya está ejecutando, asegúrese de que los auriculares está "activo". Si no es así, la selección de ubicación no se realizará correctamente. 

## <a name="see-also"></a>Vea también

* [Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
