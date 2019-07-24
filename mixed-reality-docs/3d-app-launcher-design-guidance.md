---
title: Guía de diseño del iniciador de aplicaciones 3D
description: Un iniciador de aplicaciones 3D es un objeto "físico" de la casa de la realidad mixta del usuario que puede seleccionar para iniciar una aplicación.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, iniciador de aplicaciones 3D, auriculares envolvente, cubo activo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517676"
---
# <a name="3d-app-launcher-design-guidance"></a>Guía de diseño del iniciador de aplicaciones 3D

Cuando se coloca en un casco de Windows Mixed Reality inmersivo (VR), se introduce la Página principal de Windows Mixed Reality, visualizada como una casa en un acantilado rodeado por montañas y agua (aunque puede [elegir otros entornos e incluso crear el suyo propio](add-custom-home-environments.md)). Dentro del espacio de este hogar, un usuario puede organizar y organizar los objetos 3D y las aplicaciones que le interesan de la forma que deseen. Un **iniciador de aplicaciones 3D** es un objeto "físico" de la casa de la realidad mixta del usuario que puede seleccionar para iniciar una aplicación.

![Ejemplo: Selector de aplicaciones 3D de pájaros de punto flotante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo de selector de aplicaciones 3D de pájaros de flotación (aplicación ficticia)*

## <a name="3d-app-launcher-creation-process"></a>proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:
1. Diseño y concepto (este artículo)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación:
    * [Aplicaciones para UWP](implementing-3d-app-launchers.md)
    * [Aplicaciones Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceptos de diseño

### <a name="fantastic-yet-familiar"></a>Fantástico, aún conocido

El entorno de Windows Mixed Reality en el que se encuentra su iniciador de aplicaciones es parte familiar, parte fantástica o Sci-Fi. Los mejores iniciadores siguen las reglas de este mundo. Piense en cómo puede tomar un objeto conocido y representativo de la aplicación, pero doblar algunas de las reglas de realidad real. Se generará una instrucción mágica.

### <a name="intuitive"></a>Intuitivo

Al mirar el iniciador de la aplicación, su finalidad es iniciar la aplicación: debe ser obvio y no debe causar ninguna confusión. Por ejemplo, asegúrese de que el iniciador es un representante tan obvio de la aplicación que no se confundirá con una pieza de Décor en el centro de acantilado. El iniciador de la aplicación debe invitar a los usuarios a que lo toquen o lo seleccionen.

![Ejemplo: Iniciador de aplicaciones 3D de nota nueva](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo de iniciador de aplicaciones 3D de nota nueva (aplicación ficticia)*

### <a name="home-scale"></a>Escala de inicio

los iniciadores de aplicaciones 3D viven en la casa de acantilado y su tamaño predeterminado deben tener sentido con los demás objetos "físicos" del espacio. Si coloca el iniciador junto a, por ejemplo, una planta de casa o algún mobiliario, debe sentir en casa y en el tamaño. Un buen punto de partida es ver cómo observa 30 centímetros cúbicos, pero recuerde que los usuarios pueden escalar o reducir verticalmente si lo desean.

### <a name="own-able"></a>Propiedad propia

El iniciador de aplicaciones debe sentirse como un objeto al que le encantaría tener una persona en su espacio. Se encontrarán prácticamente con estas cosas, por lo que el selector debe sentirse como algo que el usuario pensó que era lo suficientemente conveniente para buscar y mantener cerca.

![Ejemplo: Selector de aplicación de Astro Warp 3D](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Ejemplo de selector de aplicación de Astro Warp 3D (aplicación ficticia)*

### <a name="recognizable"></a>Reconocible

El selector de aplicaciones 3D debe expresar al instante "la marca de la aplicación" para las personas que lo ven. Si tiene un carácter de estrella o un objeto que se puede identificar especialmente en la aplicación, se recomienda usarlo como gran parte del diseño. En un mundo de realidad mixta, un objeto dibujará más interés de los usuarios que solo un logotipo por sí solo. Los objetos reconocibles comunican la marca rápida y claramente.

### <a name="volumetric"></a>Volumétricos

La aplicación merece más que simplemente colocar su logotipo en un plano plano y llamarlo un día. El iniciador debe sentirse como un objeto físico emocionante, 3D en el espacio del usuario. Un buen enfoque es imaginar que la aplicación iba a tener un globo en el día de Navidad de Macy. Pregúntese a sí mismo, ¿qué me gustaría que mis personas se tratara de la calle? ¿Qué aspecto sería fantástico en todos los ángulos de visualización?


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Sugerencias para buenos modelos 3D

### <a name="best-practices"></a>Procedimientos recomendados
* Cuando planee las dimensiones del iniciador de aplicaciones, capte aproximadamente un cubo 30cm. Por lo tanto, una relación de tamaño de 1:1:1.
* Los modelos deben tener menos de 10.000 polígonos. [Más información sobre recuentos de triángulos y niveles de detalles (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Pruebe en un casco inmersivo siempre que sea posible.
* Cree detalles en la geometría del modelo siempre que sea posible: no se base en las texturas para obtener detalles.
* Compilar la geometría cerrada con "ajuste del agua". Ningún hueco que no esté modelado en.
* Use materiales naturales en el objeto. Imagine que la diseña en el mundo real.
* Asegúrese de que el modelo se lea bien en diferentes distancias y tamaños.
* Cuando el modelo esté listo, lea las instrucciones de [exportación de activos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modelo con detalles sutiles en la textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modelo con detalles sutiles en la textura*

### <a name="what-to-avoid"></a>Qué evitar
* No utilice detalles de contraste alto ni texturas y patrones pequeños y ocupados.
* No use geometría fina: no funciona bien a la larga y dará un alias incorrecto.
* No permita que partes del modelo se extienda demasiado más allá de la relación de tamaño de 1:1:1. Se crearán problemas de escalado.

![Evitar patrones de alto contraste y pequeño ocupado](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evite patrones de alto contraste, pequeños y ocupados*

## <a name="how-to-handle-type"></a>Cómo controlar el tipo

### <a name="best-practices"></a>Procedimientos recomendados
* Se recomienda que el tipo comprenda aproximadamente 1/3 del iniciador de la aplicación (o más). El tipo es lo principal que da a los usuarios una idea de que el iniciador es, de hecho, un iniciador para que sea estupendo si es bastante importante.
* Evite hacer el tipo superwide: intente mantenerlo dentro de los límites de las dimensiones básicas de los iniciadores de aplicaciones (más o menos).
* El tipo plano puede funcionar, pero tenga en cuenta que puede ser difícil de ver desde determinados ángulos y en determinados entornos. Considere la posibilidad de colocarlo en un objeto sólido o telón de fondo para ayudarle con esto.
* La adición de una dimensión a su tipo se siente agradable en 3D. Sombrear los lados del tipo con un color más oscuro, puede ayudar a mejorar la legibilidad.


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**Tipos de colores que funcionan**
* Blanco
* Negro
* Color semisaturado brillante

![Escriba los colores que funcionan.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Tipos de colores que funcionan*

### <a name="what-to-avoid"></a>Qué evitar

**Colores de tipo que causan problemas**
* Tonos medios
* Gris
* Colores saturados o colores dessaturados

![Escriba los colores que causan problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Colores de tipo que causan problemas*

## <a name="lighting"></a>Iluminación

La iluminación del iniciador de la aplicación procede del entorno del centro de acantilado. Asegúrese de probar el iniciador en varios lugares de la casa para que tenga buenos puntos de luz y sombras. La buena noticia es que, si ha seguido las otras instrucciones de diseño de este documento, el iniciador debe tener una forma bastante buena para la mayor iluminación en la casa del acantilado.

Los buenos lugares para probar el aspecto del iniciador en las diversas luces del entorno son el estudio, la sala multimedia, en cualquier parte fuera y en el patio de vuelta (el área concreta con el césped). Otra buena prueba es colocarla en la mitad de la luz y la mitad de la sombra y ver su aspecto.

![Asegúrese de que el iniciador tiene buenos problemas tanto en las luces como en las sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Asegúrese de que el iniciador tiene buenos problemas tanto en las luces como en las sombras*

## <a name="texturing"></a>Texturización

### <a name="authoring-your-textures"></a>Crear las texturas

El formato final del iniciador de aplicaciones 3D será un archivo. glb, que se realiza mediante la canalización PBR (representación basada físicamente). Esto puede ser un proceso complicado; ahora es un buen momento para emplear un artista técnico si aún no lo ha hecho. Si es Brave implementación personal-ER, dedicar tiempo a [investigar y obtener información sobre la terminología de PBR](http://wiki.polycount.com/wiki/PBR) y lo que está ocurriendo en el capó antes de comenzar le ayudará a evitar errores comunes. 

![Ejemplo: Aplicación de notas nuevas](images/pbr-freshnote1-640px-500px.png)<br>
*Ejemplo de iniciador de aplicaciones 3D de nota nueva (aplicación ficticia)*

**Herramienta de creación recomendada**

Se recomienda usar el [pintor de sustancias](https://www.allegorithmic.com/products/substance-painter) de Allegorithmic para crear el archivo final. Si no está familiarizado con la creación de sombreadores de PBR en el pintor de sustancias, este es un [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Como alternativa [en 3D](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)o [marmoset toolbag](https://www.marmoset.co/toolbag/) también funcionaría si está más familiarizado con uno de ellos).

### <a name="best-practices"></a>Procedimientos recomendados

* Si el objeto iniciador de la aplicación se creó para PBR, debe ser bastante sencillo convertirlo en el entorno de la casa de acantilado.
* Nuestro sombreador espera un flujo de trabajo de metal/rugosidad: el sombreador de PBR inreal es un fax de cierre.
* Al exportar las texturas, tenga en cuenta los [tamaños de textura recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .
* Asegúrese de crear los objetos para la iluminación en tiempo real, lo que significa:
    * Evitar sombras cocidas (o sombras pintadas)
    * Evitar la iluminación horneada en las texturas
    * Use uno de los paquetes de creación de material de PBR para obtener los mapas correctos generados para nuestro sombreador

## <a name="see-also"></a>Vea también

* [Cree modelos 3D para su uso en la Página principal de la realidad mixta](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
