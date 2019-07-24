---
title: Tabla periódica de los elementos
description: La tabla periódica de los elementos es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft, donde puede aprender a diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525353"
---
# <a name="periodic-table-of-the-elements"></a>Tabla periódica de los elementos

>[!NOTE]
>En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta. Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.

[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft. Con este proyecto, puede obtener información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una **[colección de objetos](object-collection.md)** . También aprenderá a crear objetos interactivos que respondan a entradas estándar de HoloLens. Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.

![Tabla de puntos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Acerca de la aplicación

La tabla periódica de los elementos visualiza los elementos químicos y cada una de sus propiedades en un espacio 3D. Incorpora las interacciones básicas de HoloLens, como mira fijamente y el aire TAP. Los usuarios pueden obtener información sobre los elementos con modelos 3D animados. Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protoneladas y neutrons.

## <a name="background"></a>Background

Después de la primera vez que se experimentó HoloLens, una aplicación de tabla periódica era una idea de la que quería experimentar en realidad mixta. Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería una buena cuestión para explorar la composición tipográfica en un espacio 3D. Ser capaz de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.

## <a name="design"></a>Diseño

En la vista predeterminada de la tabla periódica, se imaginan cuadros tridimensionales que contendrían el modelo de electrones de cada elemento. La superficie de cada cuadro sería traslúcida, de modo que el usuario podría obtener una idea aproximada del volumen del elemento. Con fijamente y TAP, el usuario podría abrir una vista detallada de cada elemento. Para que la transición entre la vista de tabla y la vista de detalles sea suave y natural, lo hice de manera similar a la interacción física de una caja de apertura en la vida real.

![Boceto de diseño](images/640px-sketch20170406.jpg)<br>
*Dibujos de diseño*

En la vista de detalle, quería visualizar la información de cada elemento con texto representado con un gran espacio en 3D. El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.

![Interacción](images/640px-periodictable-interaction.jpg)

![Prototipos](images/640px-periodictable-prototypes.jpg)<br>
*Prototipos de interacción*

El usuario puede cambiar el tipo de superficie mediante la pulsación de los botones de la parte inferior de la tabla. puede cambiar entre plano, cilindro, esfera y dispersión.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles comunes y patrones usados en esta aplicación

### <a name="interactable-object-button"></a>Objeto interactuable (botón)

[Objeto](interactable-object.md) interactuable es un objeto que puede responder a entradas básicas de HoloLens. Se proporciona como recurso prefabricado/script, que se puede aplicar fácilmente a cualquier objeto. Por ejemplo, puede hacer que una copa de café en la escena sea interactuable y responder a entradas como, por ejemplo, gestos de toque, pulsación de aire, navegación y manipulación. [Más información](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Colección de objetos

[Colección de objetos](object-collection.md) es un objeto que ayuda a diseñar varios objetos en varias formas. Admite plano, cilindro, esfera y dispersión. Puede configurar propiedades adicionales como RADIUS, el número de filas y el espaciado. [Más información](object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

De forma predeterminada, los hologramas se colocarán en la ubicación donde se Gazing el usuario en el momento en que se inicia la aplicación. En ocasiones, esto da lugar a resultados no deseados, como los hologramas que se colocan detrás de un muro o en el medio de una tabla. Un fitbox permite al usuario usar miradamente para determinar la ubicación donde se colocará el holograma. Se crea con una textura de imagen PNG simple que se puede personalizar fácilmente con sus propias imágenes o objetos 3D.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y Prefabs para la tabla periódica de la aplicación Elements en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Ejemplos de aplicaciones

Estas son algunas ideas sobre lo que podría crear aprovechando los componentes de este proyecto.

### <a name="stock-data-visualization-app"></a>Aplicación de visualización de datos bursátiles

Con los mismos controles y el mismo modelo de interacción que la tabla periódica del ejemplo de elementos, podría crear una aplicación que visualiza los datos de los mercados de acciones. En este ejemplo se usa el control de colección de objetos para diseñar los datos bursátiles en una forma esférica. Puede imaginarse una vista de detalle en la que se pueda mostrar información adicional sobre cada acción de forma interesante.

![Ejemplo de aplicación: Finance (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Ejemplo de aplicación: Finanzas (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Ejemplo de aplicación: Finanzas (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Un ejemplo de cómo se puede usar la colección de objetos utilizada en la tabla periódica de la aplicación de ejemplo Elements en una aplicación Finance*

### <a name="sports-app"></a>Aplicación Sports

Este es un ejemplo de visualización de datos deportivos mediante la colección de objetos y otros componentes de la tabla periódica de la aplicación de ejemplo Elements.

![Ejemplo de aplicación: Deportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Ejemplo de aplicación: Deportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Ejemplo de aplicación: Deportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Un ejemplo de cómo se usa la colección de objetos en la tabla periódica de los elementos de ejemplo appcould en una aplicación Sports*

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador de la experiencia del usuario@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también

* [Objeto con el que se puede interactuar](interactable-object.md)
* [Colección de objetos](object-collection.md)
