---
title: Mapeo espacial en Unreal
description: Guía para el uso del mapeo espacial en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720411"
---
# <a name="spatial-mapping-in-unreal"></a>Mapeo espacial en Unreal

## <a name="overview"></a>Introducción
El mapeo espacial permite colocar objetos sobre superficies del mundo físico mediante la visualización del mundo de alrededor de HoloLens, lo que hace que los hologramas parezcan más reales al usuario. El mapeo espacial también ancla objetos en el mundo del usuario aprovechando las indicaciones detalladas del mundo real. Con ello, se ayuda a convencer al usuario de que estos hologramas están realmente en su espacio; los hologramas que flotan en el espacio o se mueven con el usuario no se verán como reales. Es aconsejable colocar elementos para mayor confort, siempre que sea posible.

Puede encontrar más información sobre la calidad del mapeo espacial, la ubicación, la oclusión, la representación, etc., en el documento [Asignación espacial](spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Habilitación del mapeo espacial

Para habilitar el mapeo espacial en HoloLens:
- Abra **Editar > Configuración del proyecto** y desplácese hacia abajo hasta la sección **Plataformas**.    
    + Seleccione **HoloLens** y marque **Percepción espacial**.

Para participar en el mapeo espacial y depurar **MRMesh** en un juego HoloLens:
1. Abra **ARSessionConfig** y expanda la sección **ARSettings > World Mapping (Mapeo del mundo)** . 

2. Active **Generate Mesh Data from Tracked Geometry** (Generar datos de malla a partir de la geometría de seguimiento), que indica al complemento de HoloLens que empiece a obtener los datos de mapeo espacial de forma asincrónica y los exponga en Unreal a través de **MRMesh**. 
3. Marque **Render Mesh Data in Wireframe (Representar datos de malla en contorno reticular)** para mostrar un contorno reticular blanco de cada triángulo de **MRMesh**. 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mapeo espacial en tiempo de ejecución
Puede modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución del mapeo espacial:

- Abra **Editar > Configuración del proyecto**, desplácese hacia abajo hasta la sección **Plataformas** y seleccione **HoloLens > Spatial Mapping (Mapeo espacial)** : 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

- **Max Triangles Per Cubic Meter** (Máximo de triángulos por metro cúbico) actualice la densidad de los triángulos en la malla de mapeo espacial.  
- **Spatial Meshing Volume Size** (Tamaño del volumen de la malla espacial) es el tamaño del cubo alrededor del jugador para representar y actualizar los datos de mapeo espacial.  
    + Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este valor tenga que ser grande para que coincida con el espacio del mundo real.  Por otro lado, este valor puede ser menor si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario. A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él. 

## <a name="working-with-mrmesh"></a>Utilización de MRMesh
Para obtener acceso a **MRMesh** en tiempo de ejecución:
1. Agregue un componente **ARTrackableNotify** a un actor de Blueprint. 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleccione el componente **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**. 
    - Haga clic en el botón **+** en los eventos que quiera supervisar. 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

En este caso, se supervisa el evento **On Add Tracked Geometry** (Al agregar geometría de seguimiento), que busca mallas del mundo válidas que coincidan con los datos de mapeo espacial. Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Puede cambiar el material de la malla en el gráfico de eventos de Blueprint o en C++. En la captura de pantalla siguiente se muestra la ruta de Blueprint: 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

En C++, puede suscribirse al delegado `OnTrackableAdded` para obtener el elemento `ARTrackedGeometry` en cuanto esté disponible, como se muestra en el código siguiente. 

> [!IMPORTANT]
> El archivo build.cs del proyecto **debe** contener **AugmentedReality** en la lista **PublicDependencyModuleNames**.
> - Esto incluye **ARBlueprintLibrary.h** y **MRMeshComponent.h**, que permite inspeccionar el componente **MRMesh** de **UARTrackedGeometry**. 

![Código C++ de ejemplo de anclajes espaciales](images/unreal-spatialmapping-examplecode.PNG)

El mapeo espacial no es el único tipo de datos que se muestra a través de **ARTrackedGeometries**. Puede comprobar que `EARObjectClassification` es `World`, lo que significa que se trata de una geometría de mapeo espacial. 

Hay delegados similares para eventos actualizados y quitados: 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`. 

Puede encontrar la lista completa de eventos en la API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Consulta también
* [Asignación espacial](spatial-mapping.md)
