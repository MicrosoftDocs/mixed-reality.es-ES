---
title: Comodidad
description: Durante la vista natural, el sistema visual humano se basa en varios orígenes de información o "indicaciones" para interpretar las formas 3D y la posición relativa de los objetos.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Realidad mixta, diseño, confort, HoloLens 2, HoloLens (1º gen)
ms.openlocfilehash: e71b8d73a37a5d10a07d37d91cf14c88b7a85687
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436386"
---
# <a name="comfort"></a>Comodidad

Durante la vista natural, el sistema visual humano se basa en varios orígenes de información o "indicaciones" para interpretar las formas 3D y las posiciones relativas de los objetos. Algunas pilas solo se basan en un solo ojo (guías de uso ocular), como [perspectiva lineal](https://en.wikipedia.org/wiki/Perspective_(graphical)), [tamaño conocido](https://en.wikipedia.org/wiki/Size#Perception_of_size), oclusión, [desenfoque de profundidad de campo](https://en.wikipedia.org/wiki/Depth_of_field)y [alojamiento](https://en.wikipedia.org/wiki/Accommodation_(eye)). Otros tipos de pila dependen de los ojos (señales binoculares) e incluyen [vergence](https://en.wikipedia.org/wiki/Vergence) (esencialmente las rotaciones relativas de los ojos necesarios para examinar un objeto) y la [disparidad binocular](https://en.wikipedia.org/wiki/Stereopsis) (el patrón de diferencias entre las proyecciones de la escena en el parte posterior de los dos ojos). Para garantizar la máxima comodidad de los cascos de realidad virtual, es importante que los diseñadores y los desarrolladores puedan crear y presentar contenido imitando el funcionamiento de estas señales en el mundo real. Desde una perspectiva física, también es importante diseñar contenido que no requiera movimiento de fatiguing del cuello o de los brazos. En este artículo, analizaremos las consideraciones clave que hay que tener en cuenta para lograr estos objetivos.

## <a name="vergence-accommodation-conflict"></a>Vergence: conflicto de alojamiento

Para ver claramente los objetos, los seres humanos deben [acomodar](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)o ajustar el foco de los ojos a la distancia del objeto. Al mismo tiempo, el giro de ambos ojos debe [converger](https://en.wikipedia.org/wiki/Convergence_(eye)) en la distancia del objeto para evitar que aparezcan imágenes dobles. En la vista natural, se vinculan vergence y alojamientos. Al ver algo cercano (por ejemplo, un Housefly cerca de la nariz), los ojos se cruzan y se acomodan a un punto cercano. Por el contrario, si ve algo en infinito óptico (aproximadamente a partir de 6 m o más lejano para una visión normal), las líneas de visión de los ojos pasan a ser paralelas y los lentes de los ojos se acomodan al infinito. 

En la mayoría de las pantallas de montaje, los usuarios siempre se acomodan a la distancia focal de la pantalla (para obtener una imagen nítida), pero convergen a la distancia del objeto de interés (para obtener una sola imagen). Cuando los usuarios se acomodan y convergen en distintas distancias, el vínculo natural entre las dos señales debe romperse y esto puede dar lugar a una molestia visual o una fatiga.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

Las pantallas de HoloLens se corrigen a una distancia óptica de aproximadamente 2,0 m del usuario. Por lo tanto, los usuarios siempre deben acomodarse cerca de 2,0 m para mantener una imagen clara en el dispositivo. Los desarrolladores de aplicaciones pueden guiar el lugar en el que los usuarios convergen colocando contenido y hologramas en varias profundidades. La descomodidad del conflicto de alojamiento de vergence se puede evitar o minimizar manteniendo el contenido en el que los usuarios convergen lo más cerca posible de 2,0 m (es decir, en una escena con mucha profundidad, coloque las áreas de interés cerca de 2,0 m del usuario cuando sea posible). Cuando el contenido no se puede colocar cerca de 2,0 m, la molestia del conflicto de alojamiento de Vergence es mayor cuando los interruptores de los usuarios avanzan y retrocediendo entre distintas distancias. En otras palabras, es mucho más cómodo ver un holograma estacionario que se mantiene 50CM fuera de la vista de un holograma 50CM que se desplaza hacia el usuario con el tiempo.

![distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-950px.png)<br>
*Distancia óptima para colocar hologramas del usuario*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedimientos recomendados para HoloLens (1ª generación) y HoloLens 2

Para obtener la máxima comodidad, **la zona óptima para la colocación de hologramas es de entre 1,25 m y 5 m**. En todos los casos, los diseñadores deben intentar estructurar las escenas de contenido para animar a los usuarios a interactuar con 1m o más lejos del contenido (por ejemplo, ajustar [el tamaño del contenido y los parámetros de ubicación predeterminados](gaze-and-commit.md)). 

Aunque en ocasiones es posible que sea necesario mostrar el contenido más cerca de 1 millón, se recomienda no presentar ningún holograma más cercano a 40cm. Por lo tanto, se recomienda empezar a **atenuar el contenido en 40cm y colocar un plano de recorte de representación en 30cm** para evitar cualquier objeto más cercano.

Los objetos que se mueven en profundidad son más probables que los objetos estacionales para producir la molestia debido al conflicto de alojamiento de vergence. Del mismo modo, solicitar a los usuarios que cambien rápidamente entre el enfoque cercano y el foco (por ejemplo, debido a que un holograma emergente que requiere interacción directa) puede provocar una molestia visual y una fatiga. Por lo tanto, **se debe tener especial cuidado para minimizar la frecuencia de los usuarios: ver el contenido que se está moviendo en profundidad o cambiar rápidamente el foco entre hologramas cercanos y Far**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Consideraciones adicionales para las distancias de interacción cercana y de HoloLens 2

Al diseñar contenido para la interacción directa (cercana) en HoloLens 2 o **en cualquier aplicación en la que el contenido se debe colocar más cerca de 1 millón, se debe tener cuidado adicional para garantizar la comodidad del usuario**. La probabilidad de que se produzca la molestia debido al conflicto de alojamiento de vergence aumenta exponencialmente con una distancia de visualización decreciente. Además, los usuarios pueden experimentar un mayor desvanecimiento al ver el contenido a distancias de interacción cercanos, por lo que se recomienda probar el contenido representado tanto en la zona de la ubicación óptima del holograma como más cerca (menos de 1,0 m hasta el plano de recorte). Asegúrese de que sigue siendo claro y cómodo de ver. 

Se **recomienda crear un "presupuesto de profundidad" para aplicaciones en función de la cantidad de tiempo que se espera que un usuario vea el contenido que está cerca (menos de 1,0 m) y que se mueve en profundidad**. Un ejemplo es evitar colocar el usuario en esas situaciones más del 25% del tiempo. Si se supera el presupuesto de profundidad, se recomienda realizar pruebas de usuario cuidadosas para asegurarse de que sigue siendo una experiencia cómoda. 

En general, también se recomienda realizar pruebas exhaustivas para asegurarse de que todos los requisitos de interacción (por ejemplo, la velocidad de movimiento, la disponibilidad, etc.) a distancias de interacción cercanos sigan siendo cómodos para los usuarios. 


### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

En el caso de los dispositivos envolventes, se siguen aplicando las instrucciones y los procedimientos recomendados para HoloLens, pero los valores específicos de la zona de confort se desplazan en función de la distancia focal a la pantalla. En general, las distancias focales a estas pantallas están entre 1,25 m-2,5 m. En el sentido de duda, evite la representación de objetos de interés demasiado cerca de los usuarios y, en su lugar, intente mantener la mayor parte del contenido de 1m o más lejos.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distancia interpupillary y desplazamiento vertical

Al ver el contenido digital de las pantallas montadas por el cabezal (HMD), la posición de los ojos de un espectador con respecto a la posición de presentación del contenido digital es fundamental. En concreto, Interpupillary Distance ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) y el desplazamiento vertical (VO) son importantes para ver con comodidad el contenido digital en HMDs. 

IPD hace referencia a la distancia entre los alumnos, o centros, de los ojos de un individuo. VO hace referencia al posible desplazamiento vertical del contenido digital que se muestra en cada ojo en relación con el eje horizontal de los ojos del espectador (en particular, no es lo mismo que el desplazamiento horizontal o la disparidad binocular). La falta de coincidencia de uno o ambos factores con un usuario individual puede empeorar los efectos de la molestia causada por un conflicto de alojamiento de vergence, pero incluso puede dar lugar a la molestia cuando se minimiza un conflicto de V-A (por ejemplo, para el contenido que se muestra en el centro de 2,0 m distancia de HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

#### <a name="hololens-1st-gen"></a>HoloLens (1.ª generación)

En el caso de HoloLens (1ª generación), se calcula IPD y se establece durante la [calibración](calibration.md)del dispositivo. Para los nuevos usuarios a un dispositivo que ya está configurado, se debe ejecutar la calibración o se debe establecer IPD manualmente. VO depende completamente del ajuste del dispositivo. En concreto, para minimizar VO, el dispositivo debe estar en el encabezado de un usuario de modo que las pantallas estén niveladas con el eje de sus ojos. 

#### <a name="hololens-2"></a>HoloLens 2

En el caso de HoloLens 2, se estima el valor de IPD y se establece durante la [calibración](calibration.md)del dispositivo o el ojo. En el caso de los nuevos usuarios a un dispositivo que ya está configurado, se debe ejecutar la calibración para asegurarse de que IPD está correctamente configurado. VO se cuenta automáticamente en HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

Windows Mixed Reality HMDs no tiene calibración automática para IPD o VO. IPD se puede establecer manualmente en el software (en la configuración del portal de realidad mixta, consulte [calibración](calibration.md)) o algunos HMDs tienen un control deslizante mecánico que permite al usuario ajustar el espaciado de los lentes a una posición cómoda (es decir, que coincide aproximadamente con IPD). 

## <a name="rendering-rates"></a>Tasas de representación

Las aplicaciones de realidad mixta son únicas, ya que los usuarios pueden moverse libremente en el mundo e interactuar con el contenido virtual como si fueran objetos reales. Para mantener esta impresión, es fundamental representar los hologramas para que parezcan estables en el mundo y animarse sin problemas. La representación como [mínimo de 60 fotogramas por segundo (FPS)](understanding-performance-for-mixed-reality.md) ayuda a lograr este objetivo. Hay algunos dispositivos de realidad mixta que admiten la representación en framerate superior a 60 FPS y para estos dispositivos, se recomienda encarecidamente que se representen en el framerate superior para proporcionar una experiencia de usuario óptima.

**Profundizar más**

Para dibujar hologramas para que parezca [que son estables en el mundo real o virtual](hologram-stability.md), las aplicaciones deben representar imágenes desde la posición del usuario. Dado que la representación de imágenes lleva tiempo, HoloLens y otros dispositivos de Windows Mixed Reality predicen dónde se encuentra el encabezado de un usuario cuando las imágenes se muestran en las pantallas. Este algoritmo de predicción es una aproximación. El hardware y los algoritmos de realidad mixta de Windows ajustan la imagen representada para que tenga en cuenta la discrepancia entre la posición principal prevista y la posición principal real. Este proceso hace que la imagen que muestra el usuario aparezca como si se representara desde la ubicación correcta y los hologramas se sienten estables. Las actualizaciones funcionan mejor para los pequeños cambios en la posición principal y no pueden tener en cuenta las diferencias de las imágenes representadas, como las causadas por el efecto parallax de movimiento.

**Al representar una velocidad de fotogramas mínima de 60 FPS, está haciendo dos cosas para ayudar a crear hologramas estables:**
1. Reducir la apariencia de Judder, que se caracteriza por un movimiento e imágenes dobles desiguales. El movimiento de hologramas más rápido y las tasas de representación inferiores están asociadas a Judder más pronunciados. Por lo tanto, el esfuerzo de mantener siempre 60 FPS (o la velocidad de representación máxima del dispositivo) ayuda a evitar Judder para mover hologramas.
2. Minimizar la latencia total. En un motor con un subproceso de juego y un subproceso de representación que se ejecuta en lógico, que se ejecuta en 30 fps puede Agregar 33.3 ms de latencia adicional. Al reducir la latencia, se reduce el error de predicción y se aumenta la estabilidad del holograma.

**Análisis de rendimiento**

Hay una gran variedad de herramientas que se pueden usar para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, por ejemplo:
* GPUView
* Depurador de gráficos de Visual Studio
* Generación de perfiles integrada en motores 3D como el depurador de fotogramas en Unity

## <a name="self-motion-and-user-locomotion"></a>Automovimiento y Locomotion de usuario

La única limitación es el tamaño del espacio físico; Si desea permitir que los usuarios se muevan más lejos en el entorno virtual que en sus salones reales, se debe implementar una forma de movimiento puramente virtual. Sin embargo, el movimiento virtual sostenido que no coincide con el movimiento físico real del usuario puede inducir a menudo a la enfermedad de movimiento. Este resultado se debe a las *indicaciones visuales* para la automovimiento del *mundo virtual* en conflicto con las [indicaciones de vestibular](https://en.wikipedia.org/wiki/Vestibular_system) para el automovimiento procedente del *mundo real*.

Afortunadamente, hay sugerencias para implementar Locomotion de usuario que pueden ayudar a evitar el problema:
* Ponga siempre al usuario en el control de sus movimientos; la degradación automática inesperada es especialmente problemática
* Los seres humanos son muy sensibles a la dirección de la gravedad. Por lo tanto, se deben evitar los movimientos verticales no iniciados por el usuario en especial.

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

Un método para permitir que el usuario se mueva a otra ubicación en un entorno virtual de gran tamaño es dar la impresión de que está moviendo un objeto pequeño de la escena. Este efecto se puede lograr de la siguiente manera:
   1. Proporcione una interfaz en la que el usuario pueda seleccionar una zona en el entorno virtual al que desea moverse.
   2. Tras la selección, reduzca la representación de la escena a un disco alrededor del punto deseado.
   3. Manteniendo la zona seleccionada, permite al usuario moverla como si fuera un objeto pequeño. A continuación, el usuario puede subir la selección cerca de las patas.
   4. Tras la anulación de la selección, reanude la representación de toda la escena.

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

El enfoque de dispositivo holográfica anterior no funciona también en un dispositivo inmersivo porque requiere que la aplicación represente un gran espacio de color negro u otro entorno predeterminado mientras se mueve el "disco". Este tratamiento interrumpe una sensación de inmersión. Un truco para el usuario Locomotion en un casco inmersivo es el enfoque de "parpadeo". Esta implementación proporciona al usuario control sobre su movimiento y proporciona una breve impresión del movimiento, pero hace que sea tan breve que el usuario tenga menos probabilidades de sentirse desorientado por el propio movimiento virtual:
   1. Proporcione una interfaz en la que el usuario pueda seleccionar una zona en el entorno virtual al que desea moverse.
   2. Una vez realizada la selección, comience un movimiento simulado muy rápido (100 m/s) hacia esa ubicación mientras se difumina rápidamente la representación.
   3. Atenuar la representación después de finalizar la traducción.

## <a name="heads-up-displays"></a>Pantallas emergentes

En videojuegos de primera persona, las pantallas de visualización (HUDs) presentan de forma persistente información como el estado del jugador, las asignaciones mínimas y los inventarios directamente en la pantalla. HUDs funcionan bien para mantener informado al jugador sin intrusión en la experiencia del juego. En las experiencias de realidad mixta, HUDs tiene la posibilidad de producir una molestia significativa y debe adaptarse al contexto más envolvente. En concreto, es probable que los HUDs que están bloqueados de forma rígida en la orientación del encabezado del usuario produzcan molestias. Si una aplicación requiere un HUD, se recomienda el bloqueo *del cuerpo* en lugar del bloqueo del encabezado. Este tratamiento se puede implementar como un conjunto de pantallas que se trasladan inmediatamente con el usuario, pero no se giran con el encabezado del usuario hasta que se alcanza un umbral de rotación. Una vez que se consigue el giro, el HUD puede reorientarse para presentar la información en el campo de vista del usuario. Siempre se debe evitar la implementación de la rotación y la traslación de HUD 1:1 en relación con los movimientos de cabeza del usuario.

## <a name="text-legibility"></a>Legibilidad del texto

La legibilidad del texto óptima puede ayudar a reducir la presión ocular y mantener la comodidad del usuario, especialmente en las aplicaciones o escenarios que requieren que los usuarios lean mientras están en un HMD. La legibilidad del texto depende de varios factores, entre los que se incluyen varias propiedades de pantalla (por ejemplo, densidad de píxeles, brillo, contraste), propiedades de la lente (por ejemplo, aberración cromática) y propiedades de texto/fuente (por ejemplo, la fuente específica). características como el peso, el espaciado, los serifs, etc., el color de la fuente, el color de fondo.  

En general, se recomienda probar las aplicaciones específicas para mejorar la legibilidad y hacer que los tamaños de fuente sean lo más grandes posible para una experiencia cómoda. A continuación se ofrecen instrucciones generales como punto de partida para el desarrollo. Tenga en cuenta que todos los tamaños de fuente se informan en grados de [ángulo visual](https://en.wikipedia.org/wiki/Visual_angle) en lugar de tamaños físicos específicos, lo que proporciona una guía para cualquier distancia dentro de la zona de colocación de hologramas óptima, porque cuenta tanto el tamaño del texto como la distancia aparece en el visor. 

Consulte [tipografía](typography.md) y [texto en](text-in-unity.md) páginas de Unity para obtener instrucciones más detalladas.

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

En el caso de los dispositivos holográficas, la representación de texto negro/oscuro en un fondo blanco/claro proporciona la relación de contraste más coherente, ya que el fondo tapaba interferencias del mundo real detrás de la representación. La representación de texto blanco/claro en un fondo negro/oscuro permite que se muestre más del entorno real, lo que puede interferir con la legibilidad del texto. 

#### <a name="hololens-1st-gen"></a>HoloLens (1.ª generación)

El tamaño mínimo de fuente legible (medida de la línea de base de la fuente hacia el ascendente) es de aproximadamente 0,35 ° y un tamaño de fuente cómodo es de al menos 0,5 ° para leer el contenido presentado a una distancia de 2 m para el usuario. 

#### <a name="hololens-2"></a>HoloLens 2

El tamaño mínimo de fuente legible (medida de la línea de base de la fuente a la de ascendente) es al menos aproximadamente: 
   - 0,4 °-0,5 ° a 45CM (distancia de manipulación directa) 
   - 0.35 °-0,4 ° a 2,0 m
   
El tamaño de fuente cómodamente legible (medida de la línea de base de la fuente a la de ascendente) es al menos aproximadamente: 
   - 0,65 °-0,8 ° a 45CM (distancia de manipulación directa)
   - 0,6 °-0,75 ° a 2,0 m

Tenga en cuenta que los tamaños de fuente deben ser ligeramente mayores para el texto en distancias de manipulación directa debido al conflicto de alojamiento de vergence descrito anteriormente (los ojos de los usuarios están acomodando a una distancia de 2,0 m en la pantalla de HoloLens, por lo que el contenido se representa en, por ejemplo, 45CM puede parecer más borrosa para los usuarios). 

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

Los dispositivos envolventes suelen tener relaciones de contraste mayores debido a la oclusión completa del entorno externo, pero pueden tener una densidad de píxeles más baja efectiva en parte debido a la ampliación de las lentes delante de las pantallas. 

En el caso de HMDs de realidad mixta de Windows, el tamaño mínimo de fuente vertical legible (medida de la línea base de la fuente hacia el ascendente) es aproximadamente 0,7-0.9 ° y un tamaño de fuente vertical muy cómodo es de aproximadamente 1,0 ° para leer el contenido presentado a una distancia de 2 m al usuario.

## <a name="gaze-direction"></a>Dirección de miración

Para evitar que el contenido de la presión ocular y el cuello se haya diseñado de modo que se eviten los movimientos excesivos de ojos y cuellos.
* **Evite** los ángulos de miración de más de 10 grados por encima del horizonte (movimiento vertical)
* **Evite** los ángulos de miración de más de 60 grados por debajo del horizonte (movimiento vertical)
* **Evite** rotaciones de cuellos de más de 45 grados fuera del centro (movimiento horizontal)

El ángulo de miración óptimo (en adelante) se considera entre 10-20 grados por debajo de la horizontal, ya que el encabezado tiende a inclinarse hacia abajo ligeramente, especialmente durante las actividades.

![campo de vista (hipercampo) permitido según lo determinado por el intervalo de movimiento de la](images/optimal-field-of-view-2.png)<br>
*Campo de vista (campo de visualización) permitido según lo determinado por el intervalo de movimiento del cuello*

## <a name="arm-positions"></a>Posiciones de ARM

Se puede acumular fatiga en los casos en los que se espera que los usuarios mantengan una mano a lo largo de la duración de una experiencia. También puede ser fatiguing para requerir que el usuario realice repetidas veces gestos de pulsaciones de aire durante largos períodos de tiempo. Por lo tanto, se recomienda que evite la necesidad de una entrada de gestos constante y repetida. Este objetivo puede lograrse mediante la incorporación de saltos cortos o la oferta de una combinación de entradas de gestos y voz para interactuar con la aplicación.

## <a name="see-also"></a>Consulta también
* [Gaze](gaze-and-commit.md)
* [Estabilidad de hologramas](hologram-stability.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Marco holográfico](holographic-frame.md)
* [Calibración](calibration.md)
