---
title: Comodidad
description: Durante la visualización natural, el sistema visual humano se basa en varios orígenes de información o "pilas", para interpretar las formas 3D y la posición relativa de los objetos.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Diseño, la realidad mixta reconfortantes, 2 de HoloLens, HoloLens (gen 1)
ms.openlocfilehash: e3a78e9a990d207b19b287e1897897a5d6dee3ca
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024443"
---
# <a name="comfort"></a>Comodidad

Durante la visualización natural, el sistema visual humano se basa en varios orígenes de información o "pilas", para interpretar las formas 3D y las posiciones relativas de los objetos. Algunas indicaciones se basan únicamente en un único efecto de ojos (pilas monoculares), incluidos [perspectiva lineal](https://en.wikipedia.org/wiki/Perspective_(graphical)), [tamaño familiar](https://en.wikipedia.org/wiki/Size#Perception_of_size), oclusión, [desenfoque de profundidad de campo](https://en.wikipedia.org/wiki/Depth_of_field), y [ alojamiento](https://en.wikipedia.org/wiki/Accommodation_(eye)). Otras indicaciones dependen de ambas ojos (indicaciones binocular) e incluir [vergence](https://en.wikipedia.org/wiki/Vergence) (básicamente las rotaciones relativas de los ojos necesarios para ver un objeto) y [disparidad binocular](https://en.wikipedia.org/wiki/Stereopsis) (el patrón de diferencias entre las proyecciones de la escena en la parte posterior de los dos ojos). Para garantizar la máxima comodidad en pantallas montada head, es importante para los diseñadores y desarrolladores a crear y presentar el contenido de forma que se asemeje a cómo funcionan estas indicaciones del mundo natural. Desde una perspectiva física, también es importante diseñar el contenido que no requiera la fatiga de los movimientos del cuello o armas. En este artículo, vamos a través de las consideraciones clave a tener en cuenta para lograr estos objetivos.

## <a name="vergence-accommodation-conflict"></a>Conflicto de alojamiento de vergence

Para ver con claridad los objetos, seres humanos deben [dar cabida a](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), o ajustar el foco de sus ojos, la distancia del objeto. Al mismo tiempo, la rotación de ambos ojos debe [convergen](https://en.wikipedia.org/wiki/Convergence_(eye)) a distancia del objeto para evitar la aparición de las imágenes de double. En la visualización natural, están vinculadas vergence y alojamiento. Cuando ve algo (p. ej. mosca común cerca de la nariz) cerca de sus ojos cross y adaptarse a un punto cercano. Por el contrario, si ve algo en medios óptico infinito (aproximadamente empezando en 6m o aleja para visión normal), las líneas de visión de los ojos convertirse en paralelo y lentes le los ojos alojar hasta el infinito. 

En más montado en el encabezado muestra los usuarios siempre acomoda la distancia focal de la presentación (para obtener una imagen de sharp), pero convergen en la distancia del objeto de interés (para obtener una única imagen). Cuando los usuarios dar cabida a y convergen en distancias diferentes, debe interrumpirá el vínculo natural entre las dos pilas y esto puede provocar fatiga ni incomodidad visual.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

Muestra de HoloLens se fija en una distancia óptica aproximadamente 2.0m alejándose del usuario. Por lo tanto, los usuarios siempre deben dar cabida a cerca de 2.0m para mantener una imagen clara en el dispositivo. Los desarrolladores de aplicaciones pueden guiarle donde convergen los ojos de los usuarios mediante la colocación de contenido y hologramas en diversos profundidades. Malestar desde el conflicto vergence alojamiento puede evitarse o minimizada al mantener el contenido al que los usuarios convergen lo más cerca de 2.0 m como sea posible (es decir, en una escena con gran profundidad, coloque las áreas de interés cerca 2.0 m al usuario cuando sea posible). Cuando no se puede colocar contenido cerca 2.0 m, malestar desde el conflicto de alojamiento de vergence es mayor cuando mirada del usuario se cambia y hacia atrás entre diferentes distancias. En otras palabras, es mucho más cómodo mirar un holograma estacionario que permanece 50cm distancia que al mirar un holograma 50cm distancia que se mueve hacia y lejos de usted con el tiempo.

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-950px.png)<br>
*Distancia óptima para colocar hologramas del usuario*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedimientos recomendados para HoloLens (gen 1) y 2 de HoloLens

Para obtener la máxima comodidad **es la zona de colocación holograma óptimo entre 1,25 y 5 millones**. En todos los casos, deberían intentar diseñadores escenas de contenido de estructura para animar a los usuarios interactuar 1 millón o más alejada del contenido (por ejemplo, ajustar [parámetros de selección de ubicación predeterminados y el tamaño de contenido](gaze-targeting.md)). 

Aunque en ocasiones puede necesitar mostrarse en menos de 1 millón de contenido, se recomienda no presentar alguna vez hologramas menos de 40cm. Por lo tanto, se recomienda empezar a **atenuar contenido en 40cm y la colocación de un plano de recorte de representación en 30cm** para evitar cualquier cercana a los objetos.

Los objetos que se mueven en profundidad son más probables que objetos fijos para producir malestar debido al conflicto vergence alojamiento. De forma similar, requerir que los usuarios cambiar rápidamente entre cerca de foco y enfocado extremo (por ejemplo, debido a un holograma emergente que requieren una interacción directa) puede provocar fatiga y malestar visual. Por lo tanto, **adicional debe tener cuidado para minimizar la frecuencia con los usuarios son: visualización de contenido que se mueven en profundidad; o cambiar rápidamente el foco entre hologramas far y near**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Consideraciones adicionales para el 2 de HoloLens y cerca de las distancias de interacción

Al diseñar el contenido directamente (casi) de la interacción en HoloLens 2, o **en las aplicaciones donde el contenido debe colocarse más cerca que 1 millón, debe tener cuidado adicional para garantizar la comodidad del usuario**. Las probabilidades de malestar debido al conflicto vergence alojamiento aumentan exponencialmente con reduce la distancia de visualización. Además, los usuarios pueden experimentar un aumento bluriness cuando viendo contenido en cerca de las distancias de interacción, por lo que recomendamos probar contenido representa tanto dentro de la zona de colocación de holograma óptimo, así como más cercano (menor que 1,0 m hasta el plano de recorte) para Asegúrese de que permanece claras y cómodo ver. 

**Se recomienda crear un "presupuesto profundidad" para las aplicaciones según la cantidad de tiempo que se espera que un usuario para ver el contenido que está a punto (menor que 1,0 m) y mover en profundidad**. Un ejemplo es evitar colocar el usuario en esas situaciones más del 25% del tiempo. Si se supera el presupuesto de profundidad, se recomienda probar usuario cuidado para asegurarse de que sigue siendo una experiencia cómoda. 

En general, también se recomienda una cuidadosa de pruebas para garantizar los requisitos para la interacción (por ejemplo, la velocidad de movimiento, accesibilidad, etc.) en cerca de las distancias de interacción permanecen cómodo para los usuarios. 


### <a name="guidance-for-immersive-devices"></a>Guía para dispositivos envolventes

Para dispositivos envolventes, sigue siendo aplicable la orientación y procedimientos recomendados para HoloLens, pero se desplazan a dependiendo de la distancia focal los valores específicos de la zona de comodidad a la pantalla. En general, las distancias focal a estas pantallas son entre millones de 1,25-2,5 millones. En caso de duda, evitar la representación de objetos de interés demasiado cerca a los usuarios y en su lugar intentan mantener la mayor parte del contenido 1m o más lejos.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distancia interpupillary y el desplazamiento vertical

Cuando vean el contenido digital head montado muestra (HMD), la posición de los ojos de un usuario con respecto a la posición de visualización de contenido digital es fundamental. En concreto, ambos distancia interpupillary ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) y el desplazamiento vertical (VO) son importantes para su visualización cómoda de contenido digital en HMDs. 

IPD hace referencia a la distancia entre los alumnos o centros de ojos de un individuo. VO hace referencia al desplazamiento vertical del contenido digital que se muestra para todos los ojos en relación con el eje horizontal de los ojos del potencial (en concreto, esto no es el mismo como el desplazamiento horizontal o disparidad binocular). No coincidencia de uno o ambos de estos factores a un usuario individual puede empeorar los efectos de malestar debe al conflicto vergence alojamiento, pero puede incluso causa malestar cuando se minimizan los conflictos de V-A (por ejemplo, para el contenido que se muestra en el punto focal m 2.0 distancia de la HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

#### <a name="hololens-1st-gen"></a>HoloLens (gen 1)

Para HoloLens (gen 1), IPD es estimado y establecer durante dispositivo [calibración](calibration.md). Para que los nuevos usuarios ya está establecida el dispositivo, se debe ejecutar la calibración o IPD debe establecerse manualmente. VO depende enteramente de ajustar el dispositivo. En concreto, para minimizar VO, el dispositivo debe ser descansando sobre head de un usuario que la muestra es nivel con el eje de sus ojos. 

#### <a name="hololens-2"></a>HoloLens 2

Para 2 HoloLens, IPD es estimado y establecer durante los ojos o dispositivo [calibración](calibration.md). Para que los nuevos usuarios ya está establecida el dispositivo, se debe ejecutar la calibración para asegurarse de IPD se ha establecido correctamente. VO se recoge automáticamente en HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Guía para dispositivos envolventes

Windows Mixed Reality envolventes HMDs no tengan ningún calibración automático de IPD o VO. IPD puede establecerse manualmente en el software (en configuración del Portal de realidad mixta, consulte [calibración](calibration.md)), o algunos HMDs tienen un control deslizante mecánico que permite al usuario ajustar el espaciado de los modos a una posición cómoda (es decir, es más o menos coincide con su IPD). 

## <a name="rendering-rates"></a>Tasas de procesamiento

Las aplicaciones de realidad mixta son únicas, ya que los usuarios pueden mover libremente en el mundo e interactuar con contenido virtual como como si fueran objetos reales. Para mantener esta impresión, es fundamental para representar hologramas para que aparezcan estables en el mundo y se animación sin problemas. Representación en un [mínimo de 60 fotogramas por segundo (FPS)](understanding-performance-for-mixed-reality.md) ayuda a lograr este objetivo. Hay algunos dispositivos de realidad mixta que admiten la representación de los valores de frameRate mayor que 60 FPS y para estos dispositivos se recomienda encarecidamente para representar en los valores de frameRate superior para proporcionar una experiencia de usuario óptima.

**Estudio más profundo**

Para dibujar hologramas sea similar a [está estables en el mundo real o virtual](hologram-stability.md), las aplicaciones que necesitan representar imágenes desde la posición del usuario. Puesto que la representación en imágenes lleva tiempo, HoloLens y otros dispositivos de Windows Mixed Reality predicen donde será head de un usuario cuando las imágenes se muestran en la muestra. Este algoritmo de predicción es una aproximación. Hardware y los algoritmos de Windows Mixed Reality ajustarán la imagen representada para tener en cuenta la discrepancia entre la posición principal prevista y la posición real principal. Este proceso hace que la imagen que se ve el usuario aparezcan como si lo se procesan a partir de la ubicación correcta y hologramas sentir estables. Las actualizaciones funcionan mejor para pequeños cambios en la posición principal y que no se representan completamente algunas diferencias de la imagen representada, como las causadas por el movimiento de paralaje.

**Por representación a una velocidad de fotogramas mínimo de 60 FPS, hacen dos cosas que ayuden a tomar hologramas estables:**
1. Lo que reduce la apariencia de judder, que se caracteriza por movimiento desigual e imágenes dobles. Judder más rápido movimiento holograma y representación inferior están asociadas con las tarifas más pronunciadas. Por lo tanto, esforzándose mantener siempre 60 FPS (o la tasa de procesamiento máximo del dispositivo) ayudará a evitar judder para mover hologramas.
2. Minimizar la latencia total. En un motor con un subproceso de juego y un subproceso de representación que se ejecuta en modo "lockstep", que se ejecuta en 30FPS puede agregar 33.3ms de latencia adicional. Al reducir la latencia, esto reduce los errores de predicción y aumenta la estabilidad holograma.

**Análisis de rendimiento**

Hay una variedad de herramientas que puede usarse para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, como:
* GPUView
* Depurador de gráficos de Visual Studio
* Generadores de perfiles integradas en los motores de 3D como el depurador de marco de Unity

## <a name="self-motion-and-user-locomotion"></a>El movimiento y el desplazamiento del usuario

La única limitación es el tamaño de su espacio físico; Si desea permitir que los usuarios se alejan en el entorno virtual que lo pueden hacer en las habitaciones real, debe implementar un formulario de movimiento puramente virtual. Sin embargo, sostenida movimiento virtual que no coincide con el movimiento del usuario real, físico puede inducir a menudo cinetosis. Este resultado es debido a la *indicaciones visuales* para movimiento automáticamente desde el *mundo virtual* entra en conflicto con el [vestibular indicaciones](https://en.wikipedia.org/wiki/Vestibular_system) para automática de movimiento procedentes de la *reales*.

Afortunadamente, hay sugerencias para implementar el desplazamiento del usuario que puede ayudar a evitar el problema:
* Coloque siempre el usuario en el control de sus movimientos; inesperado es especialmente problemático, automáticamente de movimiento
* Los seres humanos son muy sensibles a la dirección de la gravedad. Por lo tanto, no iniciada por el usuario los movimientos verticales especialmente deben evitarse.

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

Un método para permitir al usuario mover a otra ubicación en un entorno virtual grande es dar la impresión de un pequeño objeto están en movimiento en la escena. Este efecto puede lograrse como sigue:
   1. Proporcionar una interfaz que el usuario puede seleccionar una zona en el entorno virtual en la que desean mover.
   2. Tras la selección, reducir la representación de escenas hasta un disco en torno a la posición deseada.
   3. Manteniendo la zona seleccionada, permite al usuario moverla como si fuese un objeto pequeño. El usuario, a continuación, puede mover la selección cerca de sus pies.
   4. Tras la desactivación, reanudar representar toda la escena.

### <a name="guidance-for-immersive-devices"></a>Guía para dispositivos envolventes

El enfoque de dispositivo holográfica anterior no funciona también en un dispositivo envolvente porque requiere la aplicación para representar un gran void negro u otro entorno predeterminado al mover el "disco". Este tratamiento interrumpe la sensación de inmersión. Un truco para el desplazamiento del usuario en un auricular envolvente es el enfoque de "blink". Esta implementación ofrece control sobre su movimiento al usuario y ofrece una breve visión del movimiento, pero resulta tan breves que el usuario es menos probable que sienta pronunciado por puramente virtual automática de movimiento:
   1. Proporcionar una interfaz que el usuario puede seleccionar una zona en el entorno virtual en la que desean mover.
   2. Tras la selección, comenzar un movimiento muy rápida simulado (100 m/s) para esa ubicación mientras se está desvaneciendo rápidamente la representación.
   3. Atenuación de la representación de nuevo después de finalizar la traducción.

## <a name="heads-up-displays"></a>Muestra de aviso

En primera persona-juego de disparos en videogames, muestra Heads-Up (arvense) persistentemente presentan información como el estado del jugador, mini mapas e inventarios directamente en la pantalla. Arvense funciona bien para mantener el Reproductor informado sin intromisión en la experiencia de juego. En las experiencias de realidad mixta, arvense tiene el potencial de provocar malestar importante y debe ser adaptados para el contexto envolvente más. En concreto, arvense que se bloquea de forma rígida en orientación principal del usuario es probable que produzcan molestias. Si una aplicación requiere un HUD, se recomienda *cuerpo* bloqueo en lugar de bloqueo principal. Este tratamiento puede implementarse como un conjunto de pantallas que inmediatamente traducir con el usuario, pero no giran con principal del usuario hasta que se alcanza un umbral de rotación. Una vez que se logra ese rotación, puede orientar el HUD para presentar la información en el campo de visión del usuario. Implementación de la rotación de HUD de 1:1 y traducción en relación con la cabeza del usuario movimientos deben evitarse siempre.

## <a name="text-legibility"></a>Legibilidad del texto

Mejorar la legibilidad óptima de texto puede ayudar a reducir fatiga visual y mantener la comodidad del usuario, especialmente en escenarios que requieren los usuarios puedan leer mientras se encuentra en un HMD o aplicaciones. Depende de legibilidad del texto en una variedad de factores incluyen diversas propiedades de presentación (por ejemplo, densidad de píxeles, brillo, contraste) lente propiedades (por ejemplo, aberración cromática) y las propiedades de fuente del texto (por ejemplo, la fuente específica características como el peso, espaciado, serifs, etc., color de fuente, color de fondo).  

En general, se recomienda probar las aplicaciones específicas para mejorar la legibilidad y realizar los tamaños de fuente tan grande que sea viable para su comodidad. A continuación se ofrecen instrucciones generales como punto de partida para el desarrollo. Tenga en cuenta que se notifiquen todos los tamaños de fuente en grados de [ángulo visual](https://en.wikipedia.org/wiki/Visual_angle) en lugar de tamaños específicos de físicos, que ofrece información orientativa para cualquier distancia dentro de la zona de colocación holograma óptimo porque tiene en cuenta el tamaño de la texto y la distancia aparece en el Visor. 

Consulte [tipografía](typography.md) y [texto en Unity](text-in-unity.md) páginas para obtener más instrucciones.

### <a name="guidance-for-holographic-devices"></a>Guía para dispositivos holográficas

Para dispositivos holográficas, representación de texto oscuro o negro sobre un fondo blanco/ligero proporciona la relación de contraste más coherente ya que el fondo occlude interferencias procedentes del mundo real detrás de la representación. Representación de texto en blanco o claro sobre un fondo oscuro o negro permite más de entorno real a través, que puede interferir con la legibilidad del texto. 

#### <a name="hololens-1st-gen"></a>HoloLens (gen 1)

El tamaño mínimo de fuente legible (que se mide desde la línea de base de fuente a ascender) es aproximadamente 0,35 ° y un tamaño de fuente cómodo es aproximadamente al menos 0,5 ° para leer contenido presentado a una distancia de 2 millones al usuario. 

#### <a name="hololens-2"></a>HoloLens 2

El tamaño mínimo de fuente legible (que se mide desde la línea de base de fuente a ascender) es al menos aproximadamente: 
   - 0,4 ° - 0,5 ° a 45cm (distancia manipulación directa) 
   - ° 0,35-0.4° de m 2.0
   
El tamaño de fuente cómodamente legibles (que se mide desde la línea de base de fuente a ascender) es al menos aproximadamente: 
   - ° 0,65-0,8 ° a 45cm (distancia manipulación directa)
   - 0,6 ° - 0,75 ° de m 2.0

Tenga en cuenta que los tamaños de fuente deben ser un poco más grande de texto a una distancia de la manipulación directa debido al conflicto vergence alojamientos se ha descrito anteriormente (los ojos de los usuarios están ajustando a una distancia de m 2.0 en la pantalla de HoloLens, por lo que representa el contenido, por ejemplo, 45 cm puede aparecer más borrosos a los usuarios). 

### <a name="guidance-for-immersive-devices"></a>Guía para dispositivos envolventes

Dispositivos envolventes generalmente tienen una relación de contraste debido a la ocultación completa del entorno externo, pero pueden tener menor densidad de píxeles efectivos en parte debido a la ampliación de la lente delante de la muestra. 

Windows Mixed Reality HMDs envolventes, el tamaño mínimo de fuente vertical legibles (que se mide desde la línea de base de fuente a ascender) es aproximadamente 0,7 y 0,9 ° y un tamaño de fuente vertical cómodo es aproximadamente 1.0° para leer contenido presentado a una distancia de 2m a la usuario.

## <a name="gaze-direction"></a>Dirección de mirada

Para evitar la presión de ojo y cuello contenido debe diseñarse para que se evitan los movimientos de ojo y cuello excesivo.
* **Evitar** mirada ángulos de más de 10 grados anteriormente el horizonte (movimiento vertical)
* **Evitar** mirada ángulos de más de 60 grados a continuación el horizonte (movimiento vertical)
* **Evitar** rotaciones cuello más de 45 grados desactivar center (movimiento horizontal)

El ángulo de mirada óptimo (definitiva de almacenamiento) se considera entre 10 y 20 grados por debajo de horizontal, como el encabezado tiende a Inclinar hacia abajo un poco, especialmente durante las actividades.

![Campo de visión (FOV) según lo determinado por el intervalo de cuello del movimiento permitido](images/optimal-field-of-view-2-750px.png)<br>
*Campo de visión (FOV) según lo determinado por el intervalo de cuello del movimiento permitido*

## <a name="arm-positions"></a>Posiciones de ARM

Cuando se esperan que los usuarios a mantener una mano que se genera durante la duración de una experiencia se puede acumular fatiga de los músculos. También se cansado para requerir que el usuario realice varias veces aire pulse gestos durante largos períodos. Por lo tanto, se recomienda que evitan la intervención del gesto de constante, repetidas experiencias. Este objetivo puede lograrse mediante la incorporación de breves interrupciones u ofrece una combinación de gestos y voz de entrada para interactuar con la aplicación.

## <a name="see-also"></a>Vea también
* [Gaze](gaze.md)
* [Estabilidad de hologramas](hologram-stability.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Marco holográfico](holographic-frame.md)
* [Calibración](calibration.md)
