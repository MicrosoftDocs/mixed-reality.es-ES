---
title: Mapeo espacial en Unreal
description: Guía para el uso del mapeo espacial en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840084"
---
# <a name="spatial-mapping-in-unreal"></a>Mapeo espacial en Unreal

Para habilitar el mapeo espacial en HoloLens, comprueba que la funcionalidad “Spatial Perception” (Percepción espacial) esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades).  

Para optar por recibir el uso de mapeo espacial en un juego de HoloLens, habilita “Generate Mesh Data from Tracked Geometry” (Generar datos de malla a partir de la geometría del seguimiento) en ARSessionConfig.  A continuación, el complemento de HoloLens recibirá de forma asincrónica los datos de mapeo espacial y los mostrará en Unreal mediante MRMesh. 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)

Para ver una visualización de depuración de la malla de mapeo espacial, habilita la casilla "Render Mesh Data in Wireframe" (Representar los datos de malla en trama de alambres) para ver un contorno de alambres en blanco de cada triángulo de MRMesh. 

En Project Settings > Platform > HoloLens > Spatial Mapping (Configuración de proyectos > Plataforma > HoloLens > Mapeo espacial), se pueden modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución de el mapeo espacial. 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

Max Triangles Per Cubic Meter (Máximo de triángulos por metro cúbico) actualizará la densidad de los triángulos en la malla de mapeo espacial.  Spatial Meshing Volume Size (Tamaño del volumen de la malla espacial) indica el tamaño del cubo alrededor del juego para representar y actualizar los datos de mapeo espacial.  Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este campo tenga que ser grande para que coincida con el espacio del mundo real.  Por el contrario, si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario, este campo puede ser más pequeño.  A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él. 

Para obtener acceso a MRMesh en tiempo de ejecución, agrega primero un componente de notificación supervisable de AR a un actor de plano técnico: 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

A continuación, ve a los detalles del componente y haz clic en el botón verde "+" de los eventos que se van a supervisar. 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

En este caso, supervisamos el evento On Add Tracked Geometry (Al agregar geometría con seguimiento) en busca de mallas del mundo válidas que se correspondan con los datos de mapeo espacial y se cambia el material de la malla: 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

En C++, se puede suscribir al delegado OnTrackableAdded para obtener ARTrackedGeometry en cuanto esté disponible.  Hay delegados similares para eventos actualizados y quitados: AddOnTrackableUpdatedDelegate_Handle y AddOnTrackableRemovedDelegate_Handle. 

![Código C++ de ejemplo de anclajes espaciales](images/unreal-spatialmapping-examplecode.PNG)

El elemento build.cs del proyecto debe tener "AugmentedReality" en la lista PublicDependencyModuleNames para incluir “ARBlueprintLibrary.h” y “MRMesh” para inspeccionar el componente MRMesh de UARTrackedGeometry. 

El mapeo espacial no es el único tipo de datos que se muestra mediante ARTrackedGeometries, por lo que primero comprobamos que el valor de EARObjectClassification es World (Mundo), lo que indica que se trata de una geometría de mapeo espacial. 

## <a name="see-also"></a>Consulta también
* [Asignación espacial](spatial-mapping.md)
