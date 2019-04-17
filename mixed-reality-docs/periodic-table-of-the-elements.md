---
title: Tabla periódica de los elementos
description: Tabla periódica de los elementos es una aplicación de ejemplo de código abierto de laboratorios de Microsoft Mixed Reality diseño donde puede aprender a diseñar una matriz de objetos en el espacio 3D con distintos tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, la aplicación de ejemplo, los controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605581"
---
# <a name="periodic-table-of-the-elements"></a>Tabla periódica de los elementos

>[!NOTE]
>Este artículo describe un ejemplo de exploración que hemos creado en el [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde se comparten la información que recabemos sobre y sugerencias para mezclan el desarrollo de aplicaciones de realidad. Nuestros artículos relacionados con el diseño y código evolucionará a medida que introducimos nuevos descubrimientos.

[Tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de laboratorios de diseño de realidad mixta de Microsoft. Con este proyecto, puede aprender a diseñar una matriz de objetos en el espacio 3D con distintos tipos de superficie mediante un  **[colección de objetos](object-collection.md)**. También aprenderá a crear objetos interactuable que responden a entradas estándares de HoloLens. Puede usar los componentes de este proyecto para crear sus propios mixto experiencia de realidad la aplicación.

![Tabla de períodos de la aplicación de elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Acerca de la aplicación

Tabla periódica de los elementos se visualizan los elementos químicos y cada uno de sus propiedades en un espacio 3D. Incorpora las interacciones básicas de HoloLens como tap mirada y air. Los usuarios pueden obtener información acerca de los elementos con modelos 3D animados. Shell de electron que un elemento y su núcleo - que se compone de protons y neutrones puedan entender visualmente.

## <a name="background"></a>Background

Una vez que experimentó en primer lugar HoloLens, una aplicación de table periódico era una idea que sabía que quería experimenten en realidad mixta. Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería excelente en la materia para explorar la composición tipográfica en un espacio 3D. Poder visualizar el modelo del elemento electron fue otra parte interesante de este proyecto.

## <a name="design"></a>Diseño

Para la vista predeterminada de la tabla periódico, imaginó cuadros tridimensionales que contengan el modelo de electrones de cada elemento. La superficie de cada cuadro sería translúcida para que el usuario podría obtener una idea aproximada del volumen del elemento. Con solo pulsar mirada y aire, el usuario pudo abrir una vista detallada de cada elemento. Para realizar la transición entre la vista de tabla y vista de detalle suave y natural, he realizado similar a la interacción física de un cuadro de apertura en la vida real.

![Boceto de diseño](images/640px-sketch20170406.jpg)<br>
*Bocetos de diseño*

En la vista de detalle, quiero visualizar la información de cada elemento con el texto representado perfectamente en un espacio 3D. El modelo de electrones 3D animadas se muestra en el área central y puede verse desde distintos ángulos.

![Interacción](images/640px-periodictable-interaction.jpg)

![Prototipos](images/640px-periodictable-prototypes.jpg)<br>
*Prototipos de interacción*

El usuario puede cambiar el tipo de superficie por aire pulsando en los botones de la parte inferior de la tabla, puede cambiar entre el plano de cilindros, esfera y dispersión.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Patrones que se usan en esta aplicación y los controles comunes

### <a name="interactable-object-button"></a>Objeto interactuable (botón)

[Objeto interactuable](interactable-object.md) es un objeto que puede responder a entradas básicas de HoloLens. Se proporciona como un recurso prefabricado/script que se puede aplicar fácilmente a cualquier objeto. Por ejemplo, puede realizar una taza de café en su escena interactuable y responder a entradas, como la mirada, en el aire, gestos de navegación y manipulación. [Más información](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Colección de objetos

[Colección de objetos](object-collection.md) es un objeto que ayuda a diseñar varios objetos en varias formas. Admite el plano de cilindros, esfera y dispersión. Puede configurar propiedades adicionales, como el radio, el número de filas y el espaciado. [Más información](object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

De forma predeterminada, hologramas se colocarán en la ubicación donde se gazing el usuario en el momento en que se inicia la aplicación. A veces, esto conduce a resultados no deseados como hologramas colocadas detrás de una pared o en medio de una tabla. Un fitbox permite al usuario utilizar a mirada para determinar la ubicación donde se colocará el holograma. Se realiza con una textura de imagen PNG simple que se puede personalizar fácilmente con sus propias imágenes o los objetos 3D.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar prefabricados y secuencias de comandos para la tabla periódico de la aplicación de los elementos en el [GitHub de laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Ejemplos de aplicaciones

Presentamos algunas ideas sobre lo que puede crear mediante el aprovechamiento de los componentes de este proyecto.

### <a name="stock-data-visualization-app"></a>Aplicación de visualización de datos de acciones

Con los mismos controles y el modelo de interacción que la tabla periódico de la muestra de los elementos, podría crear una aplicación que visualiza los datos del mercado. En este ejemplo se usa el control de la colección de objetos para disponer de datos de acciones en una forma esférica. Puede imaginar una vista de detalle donde podría mostrarse información adicional sobre cada acción de una forma interesante.

![Ejemplo de aplicación: Finanzas (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Ejemplo de aplicación: Finanzas (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Ejemplo de aplicación: Finanzas (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Un ejemplo de cómo se podría usar la colección de objetos usada en la tabla periódico de la aplicación de ejemplo de los elementos en una aplicación de finanzas*

### <a name="sports-app"></a>Aplicación de deportes

Este es un ejemplo de visualización de datos deportivos mediante la colección de objetos y otros componentes de la tabla periódico de la aplicación de ejemplo de elementos.

![Ejemplo de aplicación: Deportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Ejemplo de aplicación: Deportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Ejemplo de aplicación: Deportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Un ejemplo de cómo usa la colección de objetos en la tabla periódico de la appcould de ejemplo de los elementos se usan en una aplicación de deportes*

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también

* [Objeto interactuable](interactable-object.md)
* [Colección de objetos](object-collection.md)
