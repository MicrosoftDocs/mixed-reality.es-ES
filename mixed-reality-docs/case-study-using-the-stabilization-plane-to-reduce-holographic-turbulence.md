---
title: 'Caso práctico: uso del plano de estabilización para reducir la turbulencia holográfica'
description: Uso del plano de estabilización para reducir la turbulencia holográfica
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, estabilización, caso práctico
ms.openlocfilehash: d31f3128ba10d6fc7bd57f3068db3dd16b23f901
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436434"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Caso práctico: uso del plano de estabilización para reducir la turbulencia holográfica

Trabajar con hologramas puede resultar complicado. El hecho de que pueda desplazarse por el espacio y ver los hologramas de todos los ángulos distintos proporciona un nivel de inmersión que no se puede obtener con una pantalla normal del equipo. Mantener estos hologramas en su lugar y mirar de forma realista es una función técnica que se consigue con el hardware de Microsoft HoloLens y el diseño inteligente de aplicaciones holográficas.

## <a name="the-tech"></a>La tecnología

Para que los hologramas aparezcan como si realmente estuvieran compartiendo el espacio con usted, deben representarse correctamente, sin separación de colores. Esto se logra, en parte, mediante tecnología integrada en el hardware de HoloLens que mantiene los hologramas delimitados en lo que llamamos un [plano de estabilización](hologram-stability.md#reprojection).

Un plano se define mediante un punto y un valor normal, pero como siempre queremos que el plano se enfrente a la cámara, estamos realmente interesados en configurar el punto del plano. Podemos indicar a HoloLens que apunte a centrar su procesamiento en para mantener todo el contenido anclado y estable, pero establecer este punto de enfoque es específico de la aplicación y puede hacer o interrumpir la aplicación en función del contenido.

En pocas palabras, los hologramas funcionan mejor cuando el plano de estabilización se aplica correctamente, pero lo que realmente significa depende del tipo de aplicación que se está creando. Echemos un vistazo a cómo algunas de las aplicaciones disponibles actualmente para HoloLens abordan este problema.

## <a name="behind-the-scenes"></a>En segundo plano

Al desarrollar las siguientes aplicaciones, hemos observado que cuando no usamos el plano, los objetos se verían en Sway cuando nuestro cabezal se moviera y veremos la separación de colores con movimientos de encabezado rápido o de holograma. En el transcurso del período de tiempo de desarrollo, aprendimos a través de la evaluación y el error cómo usar mejor el plano de estabilización y cómo diseñar nuestras aplicaciones en torno a los problemas que no se pueden corregir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Explorador de Galaxy: contenido estacionario, interactividad 3D

El [Explorador de Galaxy](galaxy-explorer.md) tiene dos elementos principales en la escena: la vista principal del contenido de celestiales y la pequeña barra de herramientas de la interfaz de usuario que sigue a su mira. En cuanto a la lógica de estabilización, veremos lo que su vector de miración actual intersecta con en cada fotograma para determinar si llega a todo en una capa de colisión especificada. En este caso, las capas que le interesan son los planetas, por lo que si mira fijamente en un planeta, el plano de estabilización se coloca allí. Si no se alcanza ninguno de los objetos de la capa de colisión de destino, la aplicación usa una capa "Plan B" secundaria. Si no se mira nada, el plano de estabilización se mantiene a la misma distancia que cuando se Gazing en el contenido. Las herramientas de interfaz de usuario se dejan como un destino de plano, ya que encontramos el salto entre Near y Far reduce la estabilidad de la escena global.

El diseño de Galaxy Explorer se presta bien para mantener las cosas estables y reducir el efecto de la separación de colores. Se recomienda al usuario que camine y órbita el contenido en lugar de moverlo de lado a lado, y que los planetas estén en órbitas lo suficientemente lentamente como para que la separación de colores no se aprecie. Además, se mantiene una constante de 60 FPS, que es una forma larga de evitar que se produzca la separación del color.

Para desprotegerlo, busque un archivo llamado LSRPlaneModifier.cs en el código del [Explorador de Galaxy en github](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: contenido estacionario con el foco de la interfaz de usuario

En HoloStudio, pasa la mayor parte del tiempo examinando el mismo modelo en el que está trabajando. La mirada no mueve una cantidad significativa, excepto cuando se selecciona una nueva herramienta o se desea navegar por la interfaz de usuario, para que podamos mantener la lógica de la configuración del plano simple. Al examinar la interfaz de usuario, el plano se establece en el elemento de la interfaz de usuario al que se ajusta la mirada. Al examinar el modelo, el plano es una distancia fija, que se corresponde con la distancia predeterminada entre el usuario y el modelo.

![Plano de estabilización visualizado en HoloStudio cuando el usuario mira el botón Inicio](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour y visor 3D: contenido estacionario con animaciones y películas

En HoloTour y en el visor 3D, está examinando un objeto animado de solitarios o una película con efectos 3D agregados encima. La estabilización en estas aplicaciones se establece en lo que esté viendo actualmente.

HoloTour también evita que se aleje del mundo virtual, ya que se mueve con usted en lugar de permanecer en una ubicación fija. De este modo, se asegurará de que no quedará lo suficientemente lejos de otros hologramas para problemas de estabilidad en.

![En este ejemplo de HoloTour, el plano de estabilización se establecería en esta película de Pantheon de Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: interacciones de contenido dinámico y de entorno

Establecer el plano de estabilización en RoboRaid es sorprendentemente sencillo, a pesar de ser la aplicación que requiere el movimiento más repentino. El plano está orientado hacia las paredes o los objetos circundantes, y flotará a una distancia fija delante del usuario cuando esté lo suficientemente lejos de ellos.

RoboRaid se diseñó pensando en el plano de estabilización. El retículo, que saca el máximo partido, ya que está bloqueado por el encabezado, lo evita usando solo rojo y azul, lo que minimiza cualquier sangrado de color. También contiene un poco de profundidad entre las partes, lo que minimiza cualquier sangrado de color que se produciría si se enmascara con un efecto de Parallax ya esperado. Los robots no se mueven muy rápidamente y solo viajan distancias cortas en intervalos regulares. Tienden a permanecer en torno a 2 metros delante de usted, donde la estabilización está establecida de forma predeterminada.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmentos y conkers jóvenes: contenido dinámico con interacción del entorno

Escrito por Asobo Studio en C++, los fragmentos y los Conker jóvenes adoptan un enfoque diferente para establecer el plano de estabilización. Los puntos de interés (term) se definen en el código y se ordenan en términos de prioridad. Lo que es el contenido del juego, como el modelo Conker, en los conkers jóvenes, los menús, el retículo orientado y los logotipos. El recurso está intersectado por la mirada del usuario y el plano se establece en el centro del objeto con la prioridad más alta. Si no se produce ninguna intersección, el plano se establece en la distancia predeterminada.

Los fragmentos y conkers jóvenes también diseñan alrededor de los hologramas al pausar la aplicación si se mueve fuera de lo que se ha analizado anteriormente como espacio de juego. Como tal, le mantienen dentro de los límites que se encuentran para proporcionar la experiencia más estable.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Si tiene HoloLens y le gustaría experimentar con los conceptos que he descrito, puede descargar una escena de prueba y probar los ejercicios siguientes. Usa la API de Gizmo integrada de Unity y debe ayudarle a visualizar dónde se establece el plano. Este código también se utilizó para capturar las capturas de pantallas en este caso práctico.
1. Sincronice la versión más reciente de [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Abra la escena [HoloToolkit-examples/Utilities/Scenes/StabilizationPlaneSetting. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) .
3. Compilar y configurar el proyecto generado.
4. Ejecute en el dispositivo.

### <a name="exercise-1"></a>Ejercicio 1

Verá varios puntos blancos en torno a las distintas orientaciones. Delante, verá tres puntos en profundidades diferentes. Pulse para cambiar el punto en el que se establece el plano. Para este ejercicio, y para los otros dos, desplazarse por el espacio mientras Gazing en los puntos. Gire el cabezal a la izquierda, a la derecha, hacia arriba y hacia abajo. Muévase más cerca de los puntos. Vea cómo reaccionan cuando el plano de estabilización se establece en diferentes destinos.

### <a name="exercise-2"></a>Ejercicio 2

Ahora, vaya a su derecha hasta que vea dos puntos móviles, uno oscilante en una ruta de acceso horizontal y otro en un trazado vertical. Una vez más, pulse para cambiar el punto en el que se establece el plano. Observe cómo se reduce la separación de colores en el punto que está conectado al plano. Puntee de nuevo para usar la velocidad del punto en la función de configuración del plano. Este parámetro ofrece una sugerencia a HoloLens sobre el movimiento previsto del objeto. Es importante saber cuándo usar esto, ya que observará que la velocidad se usa en un punto; el otro punto en movimiento mostrará una separación de colores mayor. Tenga esto en cuenta al diseñar las aplicaciones: tener un flujo cohesivo al movimiento de los objetos puede ayudar a evitar que aparezcan los artefactos.

### <a name="exercise-3"></a>Ejercicio 3

Vaya a la derecha una vez más hasta que vea una nueva configuración de puntos. En este caso, hay puntos en la distancia y un punto en espiral hacia delante y hacia delante. Air TAP para cambiar el punto en el que se establece el plano, alternando entre los puntos del fondo y el punto en movimiento. Observe que la configuración de la posición del plano y la velocidad en la del punto en espiral hace que los artefactos aparezcan en todas partes.

**Útiles**
* Mantenga la lógica de la configuración del plano simple. Como ha visto, no necesita algoritmos complejos de configuración de plano para crear una experiencia envolvente. El plano de estabilización es solo una parte del rompecabezas.
* Cuando sea posible, mueva siempre el plano entre los destinos sin problemas. Cambiar de forma instantánea los destinos lejanos puede interrumpir visualmente la escena.
* Considere la posibilidad de tener una opción en la lógica de configuración del plano para bloquear en un destino muy específico. De este modo, puede hacer que el plano esté bloqueado en un objeto, como un logotipo o una pantalla de título, si es necesario.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>@Microsoft de Ingeniero de software</td>
</tr>
</table>

## <a name="see-also"></a>Consulta también
* [Sr Basics 100: Introducción a Unity](holograms-100.md)
* [Punto de enfoque en Unity](focus-point-in-unity.md)
* [Estabilidad de hologramas](hologram-stability.md)
