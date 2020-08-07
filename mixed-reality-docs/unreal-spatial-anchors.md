---
title: Anclajes espaciales locales en Unreal
description: Guía para el uso de anclajes espaciales en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376053"
---
# <a name="local-spatial-anchors-in-unreal"></a>Anclajes espaciales locales en Unreal

## <a name="overview"></a>Introducción

Los anclajes espaciales se usan para guardar los hologramas en el espacio del mundo real entre sesiones de aplicación. Aparecen mediante Unreal en forma de elementos **ARPin** y se guardan en el almacén de anclajes de HoloLens, que se carga en futuras sesiones. Los anclajes locales son ideales como plan B para cuando no hay conectividad a Internet.

> [!IMPORTANT]
> Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube. Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](unreal-azure-spatial-anchors.md). Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.

## <a name="checking-the-anchor-store"></a>Comprobación del almacén de anclajes

Antes de guardar o cargar anclajes, debe comprobar si el almacén de anclajes está listo.  Si se llama a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.  

![Almacén de anclajes espaciales listo](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>Guardar anclajes

Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia: 

![Guardar anclaje espacial](images/unreal-spatialanchors-save.PNG)

Desglose:
1. Genere un actor en una ubicación conocida.
2. Cree un elemento **ARPin** con esa ubicación y un nombre basado en la clase del actor. 
3. Agregue el actor al elemento **ARPin** y guarde el marcador en el almacén de anclajes de HoloLens.  
    * El nombre del anclaje que elija debe ser único, en este ejemplo, es la marca de tiempo actual. 

4. Si el anclaje se guarda correctamente en el almacén de anclajes, se puede inspeccionar en el portal de dispositivos de HoloLens en **System > Map manager > Anchor Files Saved On Device** (Sistema > Administrador de mapas > Archivos de anclajes guardados en el dispositivo). 

## <a name="loading-anchors"></a>Carga de anclajes

Cuando se inicia una aplicación, se puede usar el siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:

![Carga de anclajes espaciales](images/unreal-spatialanchors-load.PNG)

Desglose:
1. Recorra en iteración todos los anclajes del almacén de anclajes. 
2. Genere un actor en la identidad.
3. Marque ese actor en **ARPin** en el almacén de anclajes.  

    * Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó. Cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje. 

También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje. 

## <a name="removing-anchors"></a>Eliminación de anclajes 

Cuando haya terminado con un anclaje, puede borrar delimitadores individuales o todo el almacén de anclajes con los componentes **Remove ARPin from WMRAnchor Store** (Quitar ARPin del almacén WMRAnchor) y **Remove All ARPins from WMRAnchor Store** (Quitar todos los ARPin del almacén WMRAnchor).

![Quitar anclajes espaciales](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> Tenga en cuenta que Spatial Anchors todavía están en versión beta, por lo que debe asegurarse de consultar la información y las características actualizadas.

## <a name="see-also"></a>Consulta también
* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Sistemas de coordenadas](coordinate-systems.md)
