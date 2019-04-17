---
title: Guía de diseño de la aplicación 3D del iniciador
description: Un iniciador de aplicaciones 3D es un objeto "físico" en casa de realidad mixta del usuario que se puede seleccionar para iniciar una aplicación.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, el iniciador de aplicaciones 3D, auriculares envolventes, live cubo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598548"
---
# <a name="3d-app-launcher-design-guidance"></a>Guía de diseño de la aplicación 3D del iniciador

Cuando se coloca en un auriculares de Windows Mixed Reality envolventes (VR), escriba Windows Mixed Reality doméstica, visualizar como una casa en un precipicio rodeado por montañas y agua (aunque puede [elegir otros entornos e incluso crear sus propios](add-custom-home-environments.md)). Dentro del espacio de este inicio, un usuario tiene libertad para organizar y organizar los objetos 3D y las aplicaciones que les interesa de forma que deseen. Un **iniciador de aplicaciones 3D** es un objeto "físico" en el usuario del mixto casa realidad que se puede seleccionar para iniciar una aplicación.

![Ejemplo: Iniciador de aplicaciones 3D de pájaro flotante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo de iniciador una aplicación 3D Bird flotante (aplicación ficticia)*

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación de una aplicación 3D del iniciador

Hay 3 pasos para crear un iniciador de aplicaciones 3D:
1. Diseñar y concepting (este artículo)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. La integración en la aplicación:
    * [Aplicaciones para UWP](implementing-3d-app-launchers.md)
    * [Aplicaciones de Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceptos de diseño

### <a name="fantastic-yet-familiar"></a>Fantástico aún familiar

El iniciador de aplicaciones se encuentra en el entorno de Windows Mixed Reality es parte familiar, parte fantásticos/sci-fi. Los iniciadores mejor seguir las reglas de este mundo. Piense en cómo puede tomar un objeto conocido, representativo desde su aplicación, pero algunas de las reglas de realidad real de plegado. Dará como resultado la magia.

### <a name="intuitive"></a>Intuitiva

Al examinar el iniciador de aplicaciones, su finalidad - para iniciar la aplicación - debería ser obvio y no debe causar confusiones. Por ejemplo, asegúrese de que el iniciador es un representante de la aplicación que no se pueda confundir para una parte de la decoración de los Cliff House obvia suficientemente. El iniciador de aplicaciones debe invitar a personas a táctil o seleccionar.

![Ejemplo: Iniciador de aplicaciones 3D de nota nueva](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo de iniciador aplicación 3D de nueva nota (aplicación ficticia)*

### <a name="home-scale"></a>Escala principal

Los iniciadores de aplicaciones 3D en vivo en el Cliff House y su tamaño predeterminado debe sentido con los demás objetos "físicos" en el espacio. Si coloca el iniciador del lateral, por ejemplo, una planta de casa o algunos de los muebles, sentirá en casa, size-wise. Es un buen punto de partida ver su aspecto en 30 centímetros cúbicas, pero recuerde que los usuarios pueden escalar, arriba o hacia abajo si lo desean.

### <a name="own-able"></a>El propietario puede

El iniciador de aplicaciones debería sentir como un objeto de una persona sería encantada de tener en su espacio. Deberá ser prácticamente rodeando de estas cosas, por lo que el iniciador debe parecer algo la idea del usuario era lo suficientemente recomendable buscan y mantener cercanos.

![Ejemplo: Iniciador de aplicaciones 3D de Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Ejemplo del iniciador de aplicaciones 3D Astro Warp (aplicación ficticia)*

### <a name="recognizable"></a>Recognizable

El iniciador de aplicaciones 3D al instante debe expresar "marca de la aplicación" a las personas que lo ven. Si tiene un carácter de estrella o un objeto especialmente identificable en su aplicación, se recomienda usar como una parte importante de su diseño. En un mundo de realidad mixta, un objeto dibujará más interés de los usuarios que solo un logotipo por sí solo. Objetos reconocibles comunican marca rápidamente y con claridad.

### <a name="volumetric"></a>Volumétricos

La aplicación merece algo más que colocar su logotipo en un plano sin formato y dejarlo. El iniciador debe sentirse como un objeto emocionante, 3D, físico en el espacio del usuario. Un buen enfoque es imaginar que la aplicación se va a tener un globo en desfile de día de acción de gracias el Macy. Hágase, ¿cuál sería realmente wow personas como proceden calle abajo? ¿Cuál tendría el aspecto excelente en todos los ángulos de visión?


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

### <a name="best-practices"></a>Procedimiento recomendado
* Al planear las dimensiones para el iniciador de aplicaciones, merece la pena aspirar aproximadamente un cubo de 30cm. Por lo tanto, un 1: proporción de tamaño de 1:1.
* Los modelos deben ser menos de 10 000 polígonos. [Más información sobre recuentos de triángulo y niveles de detalles (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Probar en un auricular envolvente cuando sea posible.
* Detalles de la compilación en la geometría de su modelo siempre que sea posible: no se basan en las texturas para obtener información detallada.
* Crear geometría "agua estrecha" cerrado. No hay huecos que no se modelan en.
* Utilizar materiales naturales en el objeto. Imagine diseñar en el mundo real.
* Asegúrese de que el modelo se lee correctamente en los tamaños y distancias.
* Cuando el modelo está preparado para comenzar, lea el [exportar directrices activos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![El modelo con detalles sutiles en la textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*El modelo con detalles sutiles en la textura*

### <a name="what-to-avoid"></a>Lo que debe evitar
* No utilice los detalles de alto contraste o patrones pequeño, ocupados y texturas.
* No use fino geometría: no funcionan bien a una distancia y le alias incorrecto.
* No se permiten elementos del modelo ampliar mucho más allá de la 1: proporción de tamaño de 1:1. Crea problemas de escalado.

![Evitar pequeñas, de alto contraste patrones ocupados](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitar los patrones de alto contraste, pequeño, ocupados*

## <a name="how-to-handle-type"></a>Cómo controlar el tipo

### <a name="best-practices"></a>Procedimiento recomendado
* Se recomienda que el tipo consta de aproximadamente 1/3 de su iniciador de aplicaciones (o más). El tipo es lo más importante que ofrece una idea de que el iniciador es, de hecho, un selector, por lo que es bueno si resulta bastante considerable a las personas.
* Evitar la realización de tipo muy amplia: intenta que esté dentro de los confines de los iniciadores de aplicaciones de dimensiones principal (más o menos).
* Tipo sin formato puede funcionar, pero tenga en cuenta que puede ser difícil ver desde determinadas ángulos y en algunos entornos. Considere la posibilidad de colocarlo en un objeto sólido o telón de fondo detrás de él para ayudar con esto.
* Agregar dimensión a su tipo se siente bien en 3D. Los lados del tipo de sombreado un color diferente y más oscuro puede ayudar a mejorar la legibilidad.


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


**Colores de tipo que funcionan**
* Blanco
* Negro
* Color brillante de saturados parcial

![Escriba los colores que funcionan.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Colores de tipo que funcionan*

### <a name="what-to-avoid"></a>Lo que debe evitar

**Colores de tipo que causan problemas**
* Semitonos
* Gris
* Exceso saturados colores o colores desaturados

![Escriba los colores que provocan problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Colores de tipo que causan problemas*

## <a name="lighting"></a>Iluminación

La iluminación para su iniciador de aplicaciones procedentes del entorno de Cliff House. No olvide probar el iniciador en varios lugares de la casa por lo que se ve bien en claro y sombras. La buena noticia es que, si ha seguido la Guía de diseño otros en este documento, el iniciador debe estar en forma bastante bueno para la mayoría de iluminación en el Cliff House.

Buenos lugares para probar cómo se ve el iniciador en las diversas luces en el entorno son el estudio, la sala de medios, fuera de cualquier lugar y en el Patio atrás (el área concreto con el césped). Otra buena prueba es colocarlo en la mitad de luz y sombra mitad y ver su aspecto.

![Asegúrese de que el iniciador se ve bien en claro y sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Asegúrese de que el iniciador se ve bien en claro y sombras*

## <a name="texturing"></a>Las texturas

### <a name="authoring-your-textures"></a>Las texturas de creación

El formato de final de su iniciador de aplicaciones 3D será un archivo .glb, que se realiza mediante la canalización PBR (físicamente en función de representación). Esto puede ser un proceso complicado, ahora es un buen momento para emplear un artista técnico si no lo ha hecho ya. Si eres un feliz implementación personal-er, dedicar tiempo a [investigar y obtenga información sobre terminología PBR](http://wiki.polycount.com/wiki/PBR) y lo que sucede en segundo plano antes de comenzar le ayudará a evitar errores comunes. 

![Ejemplo: Aplicación de una nota nueva](images/pbr-freshnote1-640px-500px.png)<br>
*Ejemplo de iniciador aplicación 3D de nueva nota (aplicación ficticia)*

**Recomienda la herramienta de creación**

Se recomienda usar [sustancia pintor](https://www.allegorithmic.com/products/substance-painter) por Allegorithmic para crear el archivo final. Si no está familiarizado con la creación de sombreadores PBR en sustancia pintor, aquí un [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(O bien [3D Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), o [Marmoset Toolbag](https://www.marmoset.co/toolbag/) también funcionaría si está más familiarizado con uno de ellos.)

### <a name="best-practices"></a>Procedimiento recomendado

* Si el objeto de selector de aplicación se creó para PBR, debe ser bastante sencillo convertirlo para el entorno Cliff House.
* Nuestro sombreador espera un flujo de trabajo de rugosidad/sin sistema operativo: sombreador PBR Unreal el es un facsímil cerrar.
* Al exportar las texturas, tenga la [textura tamaños recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) en mente.
* Asegúrese de crear los objetos de la iluminación en tiempo real, esto significa que:
    * Evitar sombras al horno – o pintadas sombras
    * Evitar la iluminación al horno de las texturas
    * Use uno de los materiales PBR creación de paquetes para obtener los mapas derechos generados para nuestro sombreador de

## <a name="see-also"></a>Vea también

* [Crear modelos 3D para su uso en la realidad mixta principal](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)](implementing-3d-app-launchers.md)
* [Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
