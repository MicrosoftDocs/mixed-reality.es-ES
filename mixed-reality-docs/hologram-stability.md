---
title: Estabilidad holograma
description: HoloLens automáticamente estabilice hologramas, pero hay pasos que los desarrolladores pueden aprovechar para mejorar la estabilidad de holograma aún más.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: hologramas, estabilidad, hololens
ms.openlocfilehash: b35b904e3c662c5ebd0670a98044706fe208e348
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974938"
---
# <a name="hologram-stability"></a>Estabilidad holograma

Para lograr hologramas estables, HoloLens tiene una canalización de estabilización de la imagen integrada. La canalización de estabilización funciona automáticamente en segundo plano, por lo que no hay ningún paso adicional necesario para habilitarla. Sin embargo, los desarrolladores deben ejercer las técnicas que mejoran la estabilidad holograma y evitar escenarios que reducen la estabilidad.

## <a name="hologram-quality-terminology"></a>Terminología de calidad holograma

La calidad de hologramas es el resultado de entorno buena y desarrollo de aplicaciones buenas. Las aplicaciones que alcancen una constante 60 fotogramas por segundo en un entorno donde HoloLens pueden realizar un seguimiento de los alrededores garantizará que el holograma y el sistema de coordenadas coincidente están sincronizadas. Desde la perspectiva de un usuario, no se moverán hologramas que están diseñadas para ser fijos en relación con el entorno.

Cuando se emite el entorno, las tasas de procesamiento incoherentes o baja u otros problemas de la aplicación se muestran, la siguiente terminología resulta útil para identificar el problema.
* **Precisión.** Una vez que el holograma es bloqueado por el mundo y se coloca en el mundo real, deben permanecer en que se encuentra, en relación con el entorno circundante, independientemente de movimiento de usuario o los cambios de entorno pequeño y dispersos. Si un holograma aparece más adelante en una posición inesperada, es un *precisión* problema. Estos escenarios pueden ocurrir si dos distintas salas son idénticas.
* **Vibración.** Los usuarios observarse como agita alta frecuencia de un holograma. Esto puede ocurrir cuando se degrada el seguimiento del entorno. Para los usuarios, se ejecuta la solución [optimización sensor](sensor-tuning.md).
* **Judder.** Como resultado las frecuencias de representación de baja en movimiento desigual y las imágenes de dobles de hologramas. Esto es especialmente evidente en hologramas con un movimiento. Los desarrolladores necesitan mantener un [constante 60 FPS](hologram-stability.md#frame-rate).
* **Desfase.** Los usuarios ven esto como holograma aparece para alejar donde se colocó originalmente. Esto sucede cuando hologramas se colocan muy lejos del [delimitadores espaciales](spatial-anchors.md), especialmente en las partes del entorno que no se han asignado completamente. Crear hologramas cerca de los anclajes espaciales reduce la probabilidad de desfase.
* **Jumpiness.** Cuando un holograma "POP" o "salta" fuera de su ubicación ocasionalmente. Esto puede ocurrir como seguimiento ajusta hologramas para que coincida con la descripción actualizada de su entorno.
* **Calles.** Cuando un holograma parece sway correspondiente para el movimiento de head del usuario. Esto se produce cuando no estén en hologramas el [plano estabilización](hologram-stability.md#stabilization-plane), y si no se encuentra el HoloLens [calibrados](calibration.md) para el usuario actual. El usuario puede volver a ejecutar el [calibración](calibration.md) aplicación para solucionar este problema. Los desarrolladores pueden actualizar el plano de estabilización para mejorar la estabilidad.
* **Separación de colores.** Las visualizaciones en HoloLens son una visualización secuencial de color, que flash canales de color de rojo rojo-verde-azul verde a 60Hz (color individual se muestran los campos a 240Hz). Cada vez que un usuario realiza un seguimiento de un holograma móvil con sus ojos, de sus colores constituyentes, produciendo un efecto de arco iris separar ese holograma bordes inicial y final. El grado de separación depende de la velocidad de la holograma. En algunos casos excepcionales, moverlas head rápidamente al examinar un holograma estacionario también puede producir un efecto de arco iris. Esto se denomina  *[separación de colores](hologram-stability.md#color-separation)*.

## <a name="frame-rate"></a>Velocidad de fotogramas

Velocidad de fotogramas es el primer pilar de estabilidad holograma. Para que hologramas aparezcan estable en el mundo, cada imagen que se presentan al usuario debe tener el hologramas dibujadas en el lugar correcto. Las pantallas de actualización de HoloLens 240 veces por segundo, que muestra cuatro campos de color por separado para cada uno recién representa la imagen, lo que resulta en una experiencia de usuario de 60 FPS (fotogramas por segundo). Para proporcionar la mejor experiencia posible, los desarrolladores de aplicaciones deben mantener 60 FPS, que se traduce en forma coherente que proporciona una nueva imagen del sistema operativo cada 16 milisegundos.

**60 FPS** para dibujar hologramas para que parezca que se encontraran en el mundo real, HoloLens deben representar imágenes desde la posición del usuario. Puesto que la representación en imágenes lleva tiempo, HoloLens predice donde será head de un usuario cuando las imágenes se muestran en la muestra. Este algoritmo de predicción es una aproximación. HoloLens tiene hardware que se ajusta la imagen representada en cuenta la discrepancia entre la posición de principal de predicción y la posición real principal. Esto hace que la imagen, el usuario ve aparece como si se representó desde la ubicación correcta y hologramas sentir estables. La imagen actualiza el trabajo mejor con pequeños cambios y no pudo corregir algunas cosas en la imagen representada como movimiento paralaje completamente.

Por representación a 60 FPS, hacen tres cosas que ayuden a tomar hologramas estables:
1. Minimizar la latencia general entre la representación de una imagen y esa imagen que se ve el usuario. En un motor con un subproceso de juego y un subproceso de representación que se ejecuta en modo "lockstep", que se ejecuta en 30FPS puede agregar 33.3ms de latencia adicional. Al reducir la latencia, esto reduce los errores de predicción y aumenta la estabilidad holograma.
2. Lo que, por lo que cada imagen de llegar a la vista del usuario tiene una cantidad de latencia coherente. Si representa a 30fps, la visualización muestra imágenes a 60 FPS. Esto significa que la misma imagen que se mostrará dos veces seguidas. El segundo fotograma tendrá 16.6ms más latencia que el primer fotograma y tendrá que corregir una cantidad de errores más pronuncia. Esta incoherencia en la magnitud del error puede provocar no deseados judder de 60 hz.
3. Lo que reduce la apariencia de judder, que se caracteriza por movimiento desigual e imágenes dobles. Judder más rápido movimiento holograma y representación inferior están asociadas con las tarifas más pronunciadas. Por lo tanto, esfuerza por mantener 60 FPS en absoluto veces ayudará a evitar judder para un determinado holograma móvil.

**Coherencia de la velocidad de fotogramas** coherencia de la velocidad de fotogramas es tan importante como un alta fotogramas por segundo. En ocasiones, puede quitar marcos son inevitables para cualquier aplicación de contenido enriquecido y la HoloLens implementa algunos algoritmos sofisticados para recuperarse de problemas ocasionales. Sin embargo, una velocidad de fotogramas que fluctúan constantemente es mucho más evidente a un usuario que la ejecución de forma coherente a velocidades de fotogramas inferior. Por ejemplo, una aplicación que se representa sin problemas para 5 fotogramas (60 FPS para la duración de estos 5 marcos) y, a continuación, quita todos los marcos para los 10 siguientes marcos (30 FPS para la duración de estas 10 fotogramas) aparecerán inestables más que una aplicación de forma constante representa a 30 FPS.

En una nota relacionada, el sistema operativo limita las aplicaciones hasta 30 FPS cuando [mixto captura realidad](mixed-reality-capture.md) se está ejecutando.

**Análisis de rendimiento** hay una gran variedad de herramientas que puede usarse para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, como:
* GPUView
* Depurador de gráficos de Visual Studio
* Generadores de perfiles integradas en los motores de 3D como Unity

## <a name="hologram-render-distances"></a>Distancias de representación holograma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

El sistema visual humano integra varias señales depende de la distancia cuando se fija la mirada y se centra en un objeto.
* [Alojamiento](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -el foco de un ojo individual.
* [Convergencia](https://en.wikipedia.org/wiki/Convergence_(eye)) : dos ojos mover hacia dentro o hacia fuera para centrar en un objeto.
* [Visión binocular](https://en.wikipedia.org/wiki/Stereopsis) -disparidad entre las imágenes de la izquierda y derecha ojo que dependen de la distancia de un objeto fuera de su punto de fijación.
* Sombreado, tamaño relativo de angular y otras indicaciones monocular (ojos único).

Convergencia y alojamiento son únicos porque son muy retina pilas relacionadas con cómo cambian los ojos para percibir objetos a distancias diferentes. En la visualización natural, están vinculadas convergencia y alojamiento. Cuando ve los ojos algo (por ejemplo, la nariz) cerca de los ojos cross y adaptarse a un punto cercano. Cuando los ojos ven algo parecido a infinito los ojos se convierten en paralelo y el efecto de ojos se adapta a hasta el infinito. Los usuarios gastando de HoloLens siempre se alojará a m 2.0 para mantener una imagen clara dado que muestra el HoloLens se corrigen a una distancia óptica aproximadamente 2.0m alejándose del usuario. Control de los desarrolladores de aplicaciones donde convergen los ojos de los usuarios mediante la colocación de contenido y hologramas en diversos profundidades. Cuando los usuarios dar cabida a y convergen en distancias diferentes, se interrumpe el vínculo entre las dos señales natural y esto puede provocar malestar visual o fatiga, especialmente cuando la magnitud del conflicto es grande. Malestar desde el conflicto vergence alojamiento puede evitarse o minimizada al mantener el contenido que los usuarios convergen en lo más cerca de 2.0 m como sea posible (es decir, en una escena con gran profundidad colocar las áreas de interés cerca 2.0 m cuando sea posible). Cuando no se puede colocar contenido casi malestar de 2.0 m desde el conflicto de alojamiento de vergence es mayor al usuario del que mirar atrás y hacia delante entre distancias diferentes. En otras palabras, es mucho más cómodo mirar un holograma estacionario que permanece 50cm distancia que al mirar un holograma 50cm distancia que se mueve hacia y lejos de usted con el tiempo.

Colocación de contenido de m 2.0 también resulta ventajoso porque las dos pantallas están diseñadas para totalmente se superponen a esa distancia. Para imágenes colocadas desactivar este plano, cuando se mueven fuera del marco holográfico desaparecerá de una pantalla mientras sigue siendo visible en el otro. Este rivalidad entre binocular pueden interrumpir a la percepción de profundidad de la holograma.

**Distancia óptima para colocar hologramas del usuario**

![Distancia óptima para colocar hologramas del usuario](images/distanceguiderendering-750px.png)

**Planos de recorte** para su comodidad máxima, se recomienda distancia de representación de recorte en 85 cm con fadeout empezando por 1 m de contenido. En aplicaciones donde hologramas y los usuarios son ambos hologramas estacionarios se puede ver cómodamente lo más cerca como 50cm. En esos casos, las aplicaciones deben incluir un plano de recorte no menos de 30cm y difuminar debería empezar al menos 10cm fuera del plano de recorte. Cada vez que el contenido está más cerca que 85cm es importante para asegurarse de que los usuarios mover no con frecuencia más cerca o más lejos hologramas o que hologramas frecuentemente no acercarse a o aleje el usuario como estas situaciones suelen provocar malestar desde el conflicto de alojamiento de vergence. Contenido debe estar diseñado para minimizar la necesidad de interacción de menos de 85cm en el usuario, pero cuando el contenido se debe representar más próximo que 85cm una buena regla general para los desarrolladores diseñar escenarios donde los usuarios y hologramas no se mueven en profundidad más del 25% de t tiempo que.

**Procedimientos recomendados** cuando no se puede colocar hologramas en 2 minutos y no se puede evitar conflictos entre la convergencia y alojamiento, es la zona de colocación holograma óptimo entre 1,25 y 5 millones. En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios interactúen más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y predeterminado de los parámetros de colocación).

## <a name="stabilization-plane"></a>Plano de estabilización
> [!NOTE]
> Para inmersivos escritorio, la configuración de un plano de estabilización es normalmente contraproducente, ya que ofrece menos calidad visual que proporciona el búfer de profundidad de la aplicación en el sistema para habilitar reprojection de basado en profundidad por píxel. A menos que se ejecutan en un HoloLens, por lo general debe evitar establecer el plano de estabilización.

HoloLens realiza una técnica de sofisticadas estabilización holográfica asistida por hardware. Esto es en gran medida automático y tiene que ver con el movimiento o cambio de la perspectiva (CameraPose) como anima la escena y el usuario mueve su cabeza. Un único plano, denominado el plano de estabilización, se eligieron para maximizar la estabilización de este. Mientras todos los hologramas en la escena reciben algunos estabilización, hologramas en el plano de estabilización reciben la estabilización de hardware máximas.

![Plano de estabilización de objetos 3D](images/stab-plane-500px.jpg)

El dispositivo intentará automáticamente elija este plano, pero la aplicación puede ayudar en este proceso mediante la selección del punto de enfoque en la escena. Las aplicaciones de Unity que se ejecutan en un HoloLens deben elegir la mejor centrarse punto basándose en la escena y pasa esto a [SetFocusPoint()](focus-point-in-unity.md). Un ejemplo de cómo configurar el punto de enfoque de DirectX se incluye en la plantilla predeterminada del cubo de giro.

Tenga en cuenta que cuando la aplicación de Unity se ejecuta en un auricular envolvente conectado a un PC de escritorio, Unity enviará el búfer de profundidad para Windows para habilitar reprojection por píxel, que normalmente proporcionará aún mejor calidad de imagen sin trabajo explícita por la aplicación. Si proporciona un punto de enfoque, que reemplazarán la reprojection por píxel, por lo tanto debería hacerlo sólo cuando la aplicación se ejecuta en un HoloLens.




```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Selección de ubicación del punto de enfoque depende en gran medida el holograma está viendo. La aplicación tiene el vector mirada de referencia y el Diseñador de aplicaciones sabe qué contenido desean que el usuario para observar.

Es el único más importante que un desarrollador puede hacer para estabilizar hologramas representar a 60 FPS. Soltar bajo 60 FPS reducirá considerablemente la estabilidad holograma, independientemente de la optimización de plano de estabilización.

**Procedimientos recomendados** hay ninguna manera universal para configurar el plano de estabilización y es específico de la aplicación, por tanto, la recomendación principal es experimentar y ver qué funciona mejor para sus escenarios. Sin embargo, puede intentar alinear el plano de estabilización con tanta contenido como sea posible, ya que todo el contenido de este plano se estabiliza perfectamente.

Por ejemplo:
* Si tiene contenido sólo planar (la aplicación de lectura, la aplicación de reproducción de vídeo), alinear el plano de estabilización con el plano que tiene el contenido.
* Si hay 3 esferas pequeños que están bloqueados por el mundo, que el avión de estabilización "Cortar" aunque los centros de todos los ámbitos que están actualmente en la vista del usuario.
* Si la escena tiene contenido en las profundidades sustancialmente diferentes, favorecer aún más los objetos.
* Asegúrese de ajustar cada fotograma para que coincida con el holograma el usuario está viendo el punto de estabilización

**Cosas que evite** el plano de estabilización es una excelente herramienta para lograr hologramas estables, pero si se utiliza incorrectamente puede producir inestabilidad imagen graves.
* No "desencadenar y omitir", puesto que terminan con la estabilización plano detrás del usuario o se conecta a un objeto que ya no está en la vista del usuario. Asegúrese del que plano de estabilización normal está establecido opuesto cámara hacia delante (p. ej.: camera.forward)
* No cambiar rápidamente el plano de estabilización y hacia atrás entre extremos
* No deje el plano de estabilización establecido en una distancia fija y orientación
* No permita que el plano de estabilización Cortar a través del usuario
* No establecer el punto de foco cuando se ejecuta en un equipo de escritorio de PC en lugar de un HoloLens y en su lugar, dependen de reprojection de basado en profundidad por píxel.

## <a name="color-separation"></a>Separación de colores 

Dada la naturaleza de las pantallas de HoloLens, a veces se puede percibir un artefacto que se denomina "separación de colores". Manifiesta como la imagen de separar en individuales bases colores: rojos, verde y azules. El artefacto puede ser especialmente visible al mostrar los objetos blancos, puesto que tienen grandes cantidades de rojo, verde y azul. Es más pronunciada cuando un usuario realiza un seguimiento visualmente un holograma que está moviendo por el marco holographic a alta velocidad. Otra manera, se puede producir el artefacto es deformar/deformación de objetos. Si un objeto tiene el contraste alto o puros colores (rojo, verde y azul), separación de colores se percibirá como Deformar de distintas partes del objeto.

**Como un usuario gira su cabeza al lado, ejemplo de lo que la separación de color de un cursor de redondeo blanco head bloqueado podría ser similar a:**

![Ejemplo de lo que la separación de color de un cursor de redondeo blanco head bloqueado podría ser similar como un usuario gira su cabeza al lado.](images/colorseparationofroundwhitecursor-300px.png)

Aunque es difícil de evitar por completo la separación de colores, hay varias técnicas mitigarlo.

**Separación de colores se puede ver en:**
* Los objetos que se va a mover rápidamente, incluidos objetos bloqueado a la cabeza como el [cursor](cursors.md).
* Los objetos que son esencialmente lejos de la [plano estabilización](hologram-stability.md#stabilization-plane).

**Para atenuar los efectos de separación de colores:**
* Hacer que el objeto de retrasar la mirada del usuario. Debe aparecer como si tiene algún inercia y se adjunta a la mirada "en springs". Esto ralentiza el cursor (lo que reduce la distancia de separación) y lo coloca detrás del punto de mirada probable del usuario. Siempre y cuando lo rápidamente se ponga al día cuando el usuario deja de desplazar a su mirada parece bastante natural.
* Si desea mover un holograma, intente mantener la velocidad de movimiento de TI por debajo de 5 grados por segundo si prevé que el usuario lo seguirá con los ojos.
* Use *luz* en lugar de *geometría* para el cursor. Una fuente de iluminación virtual conectado a la mirada se percibirá como un puntero interactivo, pero no hará que la separación de colores.
* Ajustar para que coincida con el hologramas en que es gazing el usuario el plano de estabilización.
* Asegúrese de la red de objeto, verde o azul.
* Cambiar a una versión del contenido difuminada. Por ejemplo, un cursor de blanco round podría ser el cambio a una línea ligeramente difuminada orientada a servicios en la dirección del movimiento.

Como antes, 60 FPS de representación y establecer el plano de estabilización son las técnicas más importantes para mejorar la estabilidad holograma. Si se enfrenta a la separación de colores notable, primero debe asegurarse de que la velocidad de fotogramas cumple las expectativas.

## <a name="see-also"></a>Vea también
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Color, luz y materiales](color,-light-and-materials.md)
* [Interacciones instintivas](interaction-fundamentals.md)