---
title: 'Caso práctico: uso el plano de estabilización para reducir turbulencias holográfica'
description: Con el plano de estabilización para reducir turbulencias holográfica
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, estabilización, caso práctico
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597528"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Caso práctico: uso el plano de estabilización para reducir turbulencias holográfica

Trabajar con hologramas puede resultar complicado. El hecho de que puede moverse por el espacio y ver sus hologramas desde todos los distintos ángulos proporciona un nivel de inmersión que no se puede obtener con la pantalla de un equipo normal. Mantener estos hologramas en su lugar y buscando realista son una hazaña técnica logra el hardware de Microsoft HoloLens y el diseño de aplicaciones holográficas inteligente.

## <a name="the-tech"></a>La tecnología

Para que hologramas aparezca como si realmente que están compartiendo el espacio con usted, deben representarse correctamente, sin separación de colores. Esto se logra parcialmente, por la tecnología integrada en el hardware de HoloLens que mantiene hologramas anclados en lo que llamamos un [plano estabilización](hologram-stability.md#stabilization-plane).

Un plano se define mediante un punto y normal, pero puesto que siempre deseamos que el plano de la cámara se enfrentan, estamos interesados en realidad con la configuración de punto del plano. Podemos indicar a HoloLens que apunten a centrar su procesamiento en mantener que todos los elementos anclados y estable, pero es específico de la aplicación, cómo establecer este punto de enfoque y puede realizar o se interrumpa la aplicación según el contenido.

En pocas palabras, hologramas funcionan mejor cuando el plano de estabilización se aplica correctamente, pero lo que realmente significa depende del tipo de aplicación que se va a crear. Echemos un vistazo a cómo algunas de las aplicaciones disponibles actualmente para HoloLens abordar este problema.

## <a name="behind-the-scenes"></a>En segundo plano

Al desarrollar las aplicaciones siguientes, hemos observado que cuando no usamos el plano, ¿sway objetos cuando el encabezado movido y se vería la separación de colores con la cabeza rápido o movimientos holograma. En el transcurso de la franja temporal de desarrollo, hemos aprendido a través de la prueba y error cómo aprovechar mejor el plano de estabilización y cómo diseñar nuestras aplicaciones en torno a los problemas que no pudo corregir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Explorador de Galaxy: Contenido estático, interactividad 3D

[Explorador de Galaxy](galaxy-explorer.md) tiene dos elementos principales de la escena: La vista principal del contenido celeste y la barra de herramientas de interfaz de usuario pequeño que sigue a su mirada. Para la lógica de estabilización, veremos lo que su mirada objeto vector actual tiene una intersección con en cada fotograma para determinar si llega a nada en una capa de colisión especificado. En este caso, las capas que nos interesa son los planetas, por lo que si su mirada cae en un planeta, el plano de estabilización se coloca allí. Si se produce ninguno de los objetos en la capa de colisión de destino, la aplicación usa un nivel secundario de "plan B". Si no hay nada que se está gazed en, el plano de estabilización se mantiene en la misma distancia igual que cuando gazing el contenido. Las herramientas de interfaz de usuario se omitiera como destino plano cuando se encuentra el salto entre casi y reduce mucho la estabilidad de la escena general.

El diseño del explorador de Galaxy se presta bien para mantener las cosas estable y reducir el efecto de separación de colores. Se anima al usuario a andar y orbital el contenido en lugar de siguen de lado a lado y los planetas están en órbita bastante lenta que la separación de color no es apreciable. Además, se mantiene una constante 60 FPS, que queda un largo camino para evitar que ocurra la separación de colores.

Para comprobar esto por su cuenta, busque un archivo denominado LSRPlaneModifier.cs en el [código del explorador de Galaxy en GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Contenido estático con un enfoque de interfaz de usuario

En HoloStudio, pasará la mayor parte de su tiempo a buscar en el mismo modelo que está trabajando. Su mirada no mueve una cantidad significativa, excepto cuando activa una nueva herramienta o va a explorar la interfaz de usuario, por lo que podemos mantener la lógica de la configuración de plano simple. Al observar la interfaz de usuario, el plano se establece en cualquier elemento de interfaz de usuario se ajusta su mirada a. Al examinar el modelo, el plano es una conjunto de distancia, correspondiente a la distancia predeterminada entre usted y el modelo.

![Visualiza el plano de estabilización en gazes HoloStudio como el usuario en el botón de inicio](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour y Visor 3D: Contenido estático con animación y películas

En el Visor 3D y HoloTour, busca un objeto animado solitario o una película con efectos 3D agregados en la parte superior. La estabilización en estas aplicaciones se establece en lo que está viendo actualmente.

HoloTour también impide que pueda straying demasiado lejos de su mundo virtual haciendo que mover con usted en lugar de permanecer en una ubicación fija. Esto garantiza que no obtendrá lo suficientemente lejos de otras hologramas para problemas de estabilidad acuesta.

![En este ejemplo de HoloTour, se establecería el plano de estabilización esta película de Pantheon de Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Interacciones de contenido y del entorno dinámicas

Establecer el plano de estabilización en RoboRaid es sorprendentemente sencillo, a pesar de que se va a la aplicación que requiere el movimiento repentino más. El plano está orientado a seguir usando las paredes o que la rodean los objetos y va a flotar a una distancia fija delante de usted cuando esté lo suficientemente fuera de ellas.

RoboRaid se diseñó teniendo en cuenta el plano de estabilización. El retículo, que mueve la mayor parte, ya que es bloqueado por head, esto evita utilizando solo rojo y azul, lo que minimiza el sangrado de cualquier color. También contiene un poco de profundidad entre las partes, minimizando cualquier sangrado de color que se produciría mediante su enmascaramiento con un efecto de paralaje ya esperado. Los robots no se mueven muy rápido y solo viajes distancias cortas en intervalos regulares. Tienden a ser alrededor de 2 metros delante de usted, donde la estabilización se establece de forma predeterminada.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Los fragmentos y Conker joven: Contenido dinámico con una interacción del entorno

Escrito por Asobo Studio en C++, fragmentos y Young Conker adoptan un enfoque diferente para establecer el plano de estabilización. Puntos de interés (POI) se definen en el código y ordenan en términos de prioridad. Puntos interés son el contenido en el juego como el modelo de Conker en Conker Young, menús, apuntar retículo y logotipos. Los puntos de interés intersecta mirada del usuario y el plano se establece en el centro del objeto con la prioridad más alta. Si se produce ninguna intersección, el plano se establece la distancia de forma predeterminada.

También diseñan fragmentos y Young Conker alrededor de straying demasiado lejos de la hologramas deteniendo la aplicación si se mueve fuera de lo que se ha analizado anteriormente como su espacio de juego. Por lo tanto, le mantienen dentro de los límites que se encuentran para ofrecer una experiencia más estable.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Si tiene un HoloLens y le gustaría experimentar con los conceptos que he tratado, puede descargar una escena de prueba y probar los ejercicios siguientes. Usa integrados artículo tiene un Unity API y debería ayudarle a visualizar dónde se está estableciendo el plano. Este código también se usó para capturar las capturas de pantalla en este caso práctico.
1. Sincronizar la versión más reciente de [MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Abra el [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) escena.
3. Crear y configurar el proyecto generado.
4. Ejecutar en el dispositivo.

### <a name="exercise-1"></a>Ejercicio 1

Verá varios puntos blancos que le rodea en diferentes orientaciones. Delante de usted, verá tres puntos al profundidades diferentes. En el aire para cambiar lo que el plano de punto se establece en. Para este ejercicio y los otros dos, moverse por el espacio al gazing en los puntos. Active su principal izquierda, derecha, arriba y abajo. Mover más cerca de y padre de los puntos. Ver cómo reaccionan cuando se establece el plano de estabilización en distintos destinos.

### <a name="exercise-2"></a>Ejercicio 2

Ahora, dirigirse a la derecha hasta que vea dos puntos mover uno oscilantes en una ruta de acceso horizontal y otro en una ruta de acceso vertical. Una vez más, aire punteo para cambiar qué punto el plano se establece en. Tenga en cuenta cómo se disminuye la separación de color aparece en el punto que está conectado al plano. Pulse de nuevo para usar la velocidad del punto en la función de la configuración de plano. Este parámetro proporciona una sugerencia a HoloLens sobre el movimiento del objeto deseado. Es importante saber cuándo utilizarlo, como podrá observar cuando se usa la velocidad en un punto, el otro punto móvil mostrará mayor separación de colores. Téngalo en cuenta al diseñar sus aplicaciones, tener un flujo coherente para el movimiento de los objetos puede ayudar a impedir que aparezcan los artefactos.

### <a name="exercise-3"></a>Ejercicio 3

Dirigirse a la derecha una vez más hasta que vea una nueva configuración de puntos. En este caso hay puntos en la distancia y un punto de entrada y salida aumento delante de ellas. Pulse para cambiar qué punto el plano se establece en, alternando entre los puntos que aparecen en la parte posterior y el punto en movimiento en el aire. Tenga en cuenta cómo establecer la posición del plano y la velocidad a la de la espiral punto hace que los artefactos aparezca en todas partes.

**Sugerencias**
* Simplificar la lógica de configuración del plano. Como ha visto, no es necesario plano complejo algoritmos de configuración para que sea una experiencia envolvente. El plano de estabilización es sólo una pieza del rompecabezas.
* Cuando está en todas las posibles siempre mover el plano entre destinos sin problemas. Cambiar al instante destinos distantes visualmente puede interrumpir la escena.
* Considere la posibilidad de tener una opción en la lógica de la configuración de plano para bloquear a un objetivo muy específico. De este modo, puede tener el plano bloqueado en un objeto, como una pantalla de logotipo o el título, si es necesario.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Ingeniero de software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Conceptos básicos de MR 100: Introducción a Unity](holograms-100.md)
* [Punto de enfoque en Unity](focus-point-in-unity.md)
* [Estabilidad holograma](hologram-stability.md)
