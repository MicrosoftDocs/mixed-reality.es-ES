---
title: Anclajes espaciales en Unreal
description: Guía para el uso de anclajes espaciales en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840144"
---
# <a name="spatial-anchors-in-unreal"></a>Anclajes espaciales en Unreal

Los anclajes espaciales se usan para conservar los hologramas en el espacio del mundo real entre sesiones de aplicación.  Aparecen mediante Unreal en forma de elementos ARPin y se guardan en el almacén de anclajes de HoloLens para cargarse en futuras sesiones. 

Antes de guardar o cargar anclajes, comprueba que el almacén de anclajes está listo.  Si intentas llamar a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.  

![Almacén de anclajes espaciales listo](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>Guardar anclajes

Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia: 

![Guardar anclaje espacial](images/unreal-spatialanchors-save.PNG)

En este caso, vamos a generar un actor en una ubicación conocida. Para hacerlo, crearemos un elemento ARPin con esa ubicación y un nombre basado en la clase del actor, agregaremos el actor al elemento ARPin y guardaremos la marca en el almacén de anclajes de HoloLens.  El nombre del anclaje que elijamos debe ser único, por lo que, en este ejemplo, hemos anexado la marca de tiempo actual.  Si el anclaje se guarda correctamente en el almacén de anclajes, se puede inspeccionar en el portal de dispositivos de HoloLens en System > Map manager > Anchor Files Saved On Device (Sistema > Administrador de mapas > Archivos de anclaje guardados en el dispositivo). 

## <a name="load-anchors"></a>Cargar anclajes

Cuando se inicia una aplicación, se puede llamar al siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:

![Carga de anclajes espaciales](images/unreal-spatialanchors-load.PNG)

En este ejemplo, se recorren en iteración todos los anclajes del almacén, se genera un actor en la identidad y se ancla ese actor al elemento ARPin del almacén.  Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó, de modo que cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje. 

También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje. 

## <a name="remove-anchors"></a>Quitar anclajes 

Cuando acabe con un anclaje, se puede borrar todo el almacén de anclajes o bien se pueden quitar anclajes individuales del almacén para que no se incluyan en sesiones futuras: 

![Quitar anclajes espaciales](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>Consulta también
* [Delimitadores espaciales](spatial-anchors.md)
* [Sistemas de coordenadas](coordinate-systems.md)
