---
title: Estabilidad de holograma
description: HoloLens estabiliza automáticamente los hologramas, pero hay pasos que los desarrolladores pueden realizar para mejorar aún más la estabilidad de los hologramas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: hologramas, estabilidad, hololens
ms.openlocfilehash: 65ea1c456ae6713e7718c3591cb3ba5759390735
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926686"
---
# <a name="hologram-stability"></a>Estabilidad de holograma

Para lograr hologramas estables, HoloLens tiene una canalización de estabilización de imágenes integrada. La canalización de estabilización funciona automáticamente en segundo plano, por lo que no se requieren pasos adicionales para habilitarla. Sin embargo, los desarrolladores deben practicar técnicas que mejoren la estabilidad del holograma y eviten escenarios que reduzcan la estabilidad.

## <a name="hologram-quality-terminology"></a>Terminología de calidad de hologramas

La calidad de los hologramas es el resultado de un buen entorno y un buen desarrollo de aplicaciones. Las aplicaciones que alcanzaron una constante 60 fotogramas por segundo en un entorno en el que HoloLens puede realizar un seguimiento del entorno garantizarán que el holograma y el sistema de coordenadas de coincidencia estén sincronizados. Desde la perspectiva del usuario, los hologramas que están diseñados para ser estacionarios no se mueven en relación con el entorno.

Cuando surjan problemas de entorno, tasas de representación incoherentes o bajas, u otros problemas de la aplicación, la terminología siguiente resulta útil para identificar el problema.
* **Precisión.** Una vez que el holograma está bloqueado mundialmente y colocado en el mundo real, debe permanecer donde se colocó, en relación con el entorno circundante, independientemente del movimiento del usuario o de los cambios de entorno pequeños y dispersos. Si más adelante aparece un holograma en una ubicación inesperada, se trata de un problema de *precisión* . Estos escenarios pueden producirse si dos salones distintos parecen idénticos.
* **Vibrante.** Los usuarios observan esto como una sacudida de alta frecuencia de un holograma. Esto puede ocurrir cuando el seguimiento del entorno se degrada. Para los usuarios, la solución está ejecutando el [ajuste del sensor](sensor-tuning.md).
* **Judder.** Las frecuencias de representación bajas dan como resultado una imagen de movimiento y dos veces inuniformes de hologramas. Esto es especialmente evidente en los hologramas con movimiento. Los desarrolladores necesitan mantener una [constante de 60 fps](hologram-stability.md#frame-rate).
* **Fase.** Los usuarios ven que el holograma desaparece de donde se colocó originalmente. Esto sucede cuando los hologramas se colocan lejos de los [delimitadores espaciales](spatial-anchors.md), especialmente en las partes del entorno que no se han asignado completamente. La creación de hologramas cercanos a los delimitadores espaciales reduce la probabilidad de derivación.
* **Puesta en marcha.** Cuando un holograma "extrae" o "salta" fuera de su ubicación en ocasiones. Esto puede ocurrir cuando el seguimiento ajusta los hologramas para que coincidan con el conocimiento actualizado de su entorno.
* **Nada.** Cuando aparece un holograma en Sway que corresponde al movimiento del encabezado del usuario. Esto se produce cuando la aplicación no ha implementado completamente la [Reproyección](hologram-stability.md#reprojection)y si HoloLens no está [calibrado](calibration.md) para el usuario actual. El usuario puede volver a ejecutar la aplicación de [calibración](calibration.md) para corregir este. Los desarrolladores pueden actualizar el plano de estabilización para mejorar la estabilidad.
* **Separación de colores.** Las pantallas de HoloLens son una pantalla secuencial de color, que muestra los canales de color rojo, verde y azul-verde a 60 Hz (los campos de color individuales se muestran en 240Hz). Cada vez que un usuario realiza un seguimiento de un holograma móvil con sus ojos, los bordes inicial y final de un holograma se separan en sus colores constituyentes, lo que produce un efecto de arco iris. El grado de separación depende de la velocidad del holograma. En algunos casos más raros, mover unos con rapidez mientras se examina un holograma estacionario también puede producir un efecto de arco iris. Esto se denomina *[separación de colores](hologram-stability.md#color-separation)* .

## <a name="frame-rate"></a>Velocidad de fotogramas

La velocidad de fotogramas es el primer pilar de estabilidad del holograma. Para que los hologramas parezcan estables en el mundo, cada imagen presentada al usuario debe tener los hologramas dibujados en el lugar correcto. Se muestra en la actualización de HoloLens 240 veces por segundo, que muestra cuatro campos de color independientes para cada imagen recién representada, lo que da lugar a una experiencia de usuario de 60 FPS (fotogramas por segundo). Para proporcionar la mejor experiencia posible, los desarrolladores de aplicaciones deben mantener 60 FPS, lo que se traduce para proporcionar de forma coherente una nueva imagen al sistema operativo cada 16 milisegundos.

**60 fps** Para dibujar hologramas para que parezca que están sentados en el mundo real, HoloLens debe representar imágenes de la posición del usuario. Dado que la representación de imágenes lleva tiempo, HoloLens predice dónde estará el encabezado de un usuario cuando las imágenes se muestren en las pantallas. Este algoritmo de predicción es una aproximación. HoloLens tiene hardware que ajusta la imagen representada para tener en cuenta la discrepancia entre la posición principal prevista y la posición principal real. Esto hace que la imagen que ve el usuario aparezca como si se representara desde la ubicación correcta y los hologramas se sienten estables. La imagen se actualiza mejor con pequeños cambios y no puede corregir por completo algunas cosas en la imagen representada como motion-Parallax.

Al representar a 60 FPS, está haciendo tres cosas para ayudar a crear hologramas estables:
1. Minimizar la latencia total entre la representación de una imagen y la visualización de la imagen por parte del usuario. En un motor con un subproceso de juego y un subproceso de representación que se ejecuta en lógico, que se ejecuta en 30 fps puede Agregar 33.3 ms de latencia adicional. Al reducir la latencia, se reduce el error de predicción y se aumenta la estabilidad del holograma.
2. Hacer que cada imagen que llega a los ojos del usuario tenga una cantidad de latencia coherente. Si se representa en 30 fps, la pantalla todavía muestra imágenes en 60 FPS. Esto significa que la misma imagen se mostrará dos veces en una fila. El segundo fotograma tendrá 16.6 ms más de latencia que el primer fotograma y tendrá que corregir una cantidad de errores más pronunciada. Esta incoherencia en la magnitud del error puede producir 60Hz Judder no deseados.
3. Reducir la apariencia de Judder, que se caracteriza por un movimiento e imágenes dobles desiguales. El movimiento de hologramas más rápido y las tasas de representación inferiores están asociadas a Judder más pronunciados. Por lo tanto, si se intenta mantener 60 FPS en todo momento, se evitará la Judder para un holograma móvil determinado.

**Coherencia de velocidad de fotogramas** La coherencia de velocidad de fotogramas es tan importante como fotogramas altos por segundo. Ocasionalmente, los fotogramas quitados son inevitables para cualquier aplicación de contenido enriquecido y HoloLens implementa algunos algoritmos sofisticados para recuperarse de problemas ocasionales. Sin embargo, una velocidad de fotogramas oscilante constantemente es mucho más evidente para un usuario que la ejecución coherente con velocidades de fotogramas inferiores. Por ejemplo, una aplicación que se representa sin problemas para 5 fotogramas (60 FPS para la duración de estos 5 fotogramas) y, a continuación, quita cada fotograma de los 10 fotogramas siguientes (30 FPS para la duración de estos 10 fotogramas) parecerá más inestable que una aplicación que de forma coherente representa a 30 FPS.

En una nota relacionada, el sistema operativo limitará las aplicaciones a 30 FPS cuando se esté ejecutando una [captura de realidad mixta](mixed-reality-capture.md) .

**Análisis de rendimiento** Hay una gran variedad de herramientas que se pueden usar para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, por ejemplo:
* GPUView
* Depurador de gráficos de Visual Studio
* Generación de perfiles integrada en motores 3D como Unity

## <a name="hologram-render-distances"></a>Distancias de representación de hologramas

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

El sistema visual humano integra varias señales dependientes de la distancia cuando se fixates y se centra en un objeto.
* [Adaptación](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) : el foco de un ojo individual.
* [Convergencia](https://en.wikipedia.org/wiki/Convergence_(eye)) : dos ojos que se mueven hacia adentro o hacia afuera hasta el centro de un objeto.
* [Visión binocular](https://en.wikipedia.org/wiki/Stereopsis) : disparidades entre las imágenes de la izquierda y la derecha que dependen de la distancia de un objeto desde el punto de fijación.
* Sombreado, tamaño de angular relativo y otras indicaciones de los anteojos (ojo único).

La convergencia y el alojamiento son únicos porque son guías retinas adicionales relacionadas con el modo en que los ojos cambian para percibir objetos en distintas distancias. En la vista natural, se vinculan la convergencia y el ajuste. Cuando el ojo ve algo cerca (por ejemplo, su nariz), los ojos se cruzan y se acomodan a un punto cercano. Cuando los ojos ven algo en infinito, los ojos se convierten en paralelo y el ojo se adapta al infinito. Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se corrigen a una distancia óptica aproximadamente a 2,0 m del usuario. Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades. Cuando los usuarios se acomodan y convergen en distintas distancias, se rompe el vínculo natural entre las dos señales y esto puede dar lugar a una molestia visual o a una fatiga, especialmente cuando la magnitud del conflicto es grande. La descomodidad del conflicto de alojamiento de vergence se puede evitar o minimizar manteniendo el contenido al que los usuarios convergen de la manera más cercana a la versión 2.0 m (es decir, en una escena con mucha profundidad, las áreas de interés cerca de 2,0 m cuando sea posible). Cuando el contenido no se puede colocar cerca de la 2,0 m del conflicto con el alojamiento de vergence, es más grande cuando el usuario mira hacia atrás y hacia delante entre distintas distancias. En otras palabras, es mucho más cómodo ver un holograma estacionario que se mantiene 50CM fuera de la vista de un holograma 50CM que se desplaza hacia el usuario con el tiempo.

Colocar contenido en 2,0 m también es ventajoso porque las dos pantallas están diseñadas para superponerse completamente a esta distancia. En el caso de las imágenes que se colocan fuera de este plano, cuando se mueven fuera del lateral del marco holográfica, desaparecen de una pantalla mientras siguen siendo visibles en la otra. Este rival puede ser perjudicial para la percepción de profundidad del holograma.

**Distancia óptima para colocar hologramas del usuario**

![Distancia óptima para colocar hologramas del usuario](images/distanceguiderendering-750px.png)

**Planos de recortes** Para obtener la máxima comodidad, se recomienda el recorte de la distancia de representación en 85cm con fadeout de contenido a partir de 1m. En las aplicaciones donde los hologramas y los usuarios son los hologramas estacionales, se pueden ver de forma cómoda como 50CM. En estos casos, las aplicaciones deben colocar un plano de recorte de forma que no sea más cerca de 30cm y el fundido de salida debe empezar al menos 10cm fuera del plano de recorte. Siempre que el contenido sea más cercano a 85cm, es importante asegurarse de que los usuarios no se mueven con frecuencia más cerca o más lejos de los hologramas o que los hologramas no se mueven más cerca o más lejos del usuario, ya que es más probable que estas situaciones resulten molestas en el vergence: conflicto de alojamiento. El contenido debe diseñarse para minimizar la necesidad de interacción más cercana a 85cm del usuario, pero cuando el contenido se debe presentar más cerca que 85cm, una buena regla general para los desarrolladores es diseñar escenarios en los que los usuarios o los hologramas no se mueven en profundidad más del 25% del tiempo.

**Procedimientos recomendados** Cuando los hologramas no se pueden colocar en 2m y no se pueden evitar conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m. En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).

## <a name="reprojection"></a>Reproyección
HoloLens realiza una sofisticada técnica de estabilización holográfica asistida por hardware conocida como reproyecto. Esto tiene en cuenta el movimiento y el cambio del punto de vista (CameraPose) a medida que la escena se anima y el usuario mueve su cabeza.  Las aplicaciones deben realizar acciones específicas para el mejor uso de la Reproyección.


Hay cuatro tipos principales de Reproyección
* **Reproyección de profundidad:**  Esto produce los mejores resultados con la menor cantidad de esfuerzo de la aplicación.  Todas las partes de la escena representada se estabilizan de forma independiente en función de su distancia del usuario.  Algunos artefactos de representación pueden estar visibles en los que hay cambios bruscos en profundidad.  Esta opción solo está disponible en HoloLens 2 y en auriculares envolvente.
* **Reproyección plana:**  Esto permite un control preciso de la aplicación sobre la estabilización.  La aplicación establece un plano y todo lo que se encuentra en dicho plano será la parte más estable de la escena.  Además, el holograma está fuera del plano, el menos estable será.  Esta opción está disponible en todas las plataformas de Windows MR.
* **Reproyección plana automática:**  El sistema establece un plano de estabilización usando información en el búfer de profundidad.  Esta opción está disponible en la generación 1 de HoloLens y en HoloLens 2.
* **Ninguno:** Si la aplicación no realiza ninguna acción, la Reproyección plana se usa con el plano de estabilización fijado a 2 metros en la dirección del cabezal del usuario.  Normalmente, se generarán resultados subestándars.

Las aplicaciones deben realizar acciones específicas para habilitar los distintos tipos de Reproyección.
* **Reproyección de profundidad:** La aplicación envía su búfer de profundidad al sistema para cada fotograma representado.  En Unity esto se hace con la opción "habilitar el uso compartido del búfer de profundidad" en el panel de configuración del reproductor.  Las aplicaciones de DirectX llaman a CommitDirect3D11DepthBuffer.  La aplicación no debe llamar a SetFocusPoint.
* **Reproyección plana:** En cada fotograma, las aplicaciones indican al sistema la ubicación de un plano para estabilizar.  Las aplicaciones de Unity llaman a SetFocusPointForFrame y deben tener deshabilitada la opción "habilitar el uso compartido del búfer de profundidad".  Las aplicaciones de DirectX llaman a SetFocusPoint y no deben llamar a CommitDirect3D11DepthBuffer.
* **Reproyección plana automática:** Para habilitar esto, la aplicación debe enviar su búfer de profundidad al sistema como lo haría para la reproyección de profundidad.  En HoloLens 2, la aplicación necesita SetFocusPoint con un punto de 0, 0 para cada fotograma.  En el caso de la generación 1 de HoloLens, la aplicación no debe llamar a SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Elección de la técnica de Reproyección

Tipo de estabilización |    Auriculares inmersivo |    Generación 1 de HoloLens | HoloLens 2
--- | --- | --- | ---
Reproyección de profundidad |    Recomendaciones |   N/D |   Recomendaciones<br/><br/>Las aplicaciones de Unity deben usar Unity 2018.4.12 o posterior o Unity 2019,3 o posterior. De lo contrario, use la Reproyección plana automática.
Reproyección plana automática | N/D |   Valor predeterminado recomendado |   Recomendado si la reproyección de profundidad no da los mejores resultados<br/><br/>Se recomienda que las aplicaciones de Unity usen Unity 2018.4.12 o posterior o Unity 2019,3 o posterior.  Las versiones anteriores de Unity funcionarán con resultados de Reproyección ligeramente reducidos.
Reproyección plana |   No recomendado |   Recomendado si el plano automático no da los mejores resultados |    Use si ninguna de las opciones de profundidad proporciona los resultados deseados.    

### <a name="verifying-depth-is-set-correctly"></a>La comprobación de profundidad está establecida correctamente
            
Cuando un método de Reproyección usa el búfer de profundidad, es importante comprobar que el contenido del búfer de profundidad representa la escena representada de la aplicación.  Algunos factores pueden causar problemas.  Si hay una segunda cámara que se usa para representar, por ejemplo, superposiciones de la interfaz de usuario, es probable que sobrescriba toda la información de profundidad de la vista real.  A menudo, los objetos transparentes no establecen profundidad.  Algunas representaciones de texto no establecerán la profundidad de forma predeterminada.  Habrá problemas visibles en la representación cuando la profundidad no coincida con los hologramas representados.
            
HoloLens 2 tiene un visualizador para mostrar donde Depth es y no se establece.  Habilítelo en el portal de dispositivos.  En la pestaña **vistas** > **estabilidad de holograma** , active la casilla Mostrar la **visualización de profundidad en auriculares** .  Las áreas con la profundidad establecida correctamente serán azules.  Los elementos representados que no tienen un conjunto de profundidad estarán en rojo y, por lo tanto, se deberán corregir.  Tenga en cuenta que la visualización de la profundidad no se muestra en la captura de realidad mixta.  Solo es visible a través del dispositivo.
            
Algunas herramientas de visualización de GPU permitirán la visualización del búfer de profundidad.  Los desarrolladores de aplicaciones pueden usar estas herramientas para asegurarse de que la profundidad se establece correctamente.  Consulte la documentación de las herramientas de la aplicación.

### <a name="using-planar-reprojection"></a>Usar la Reproyección plana
> [!NOTE]
> En el caso de los auriculares que incluyen el escritorio, el establecimiento de un plano de estabilización suele ser productivo, ya que ofrece menos calidad visual que proporcionar el búfer de profundidad de la aplicación al sistema para habilitar una Reproyección basada en la profundidad por píxel. A menos que se ejecute en HoloLens, normalmente debe evitar establecer el plano de estabilización.

![Plano de estabilización para objetos 3D](images/stab-plane-500px.jpg)

El dispositivo intentará automáticamente elegir este plano, pero la aplicación debería ayudar en este proceso seleccionando el punto de enfoque en la escena. Las aplicaciones de Unity que se ejecutan en HoloLens deben elegir el mejor punto de enfoque en función de la escena y pasarlo a [SetFocusPoint ()](focus-point-in-unity.md). En la plantilla de cubo giratorio predeterminada se incluye un ejemplo de cómo establecer el punto de enfoque en DirectX.

Tenga en cuenta que cuando la aplicación de Unity se ejecuta en un casco envolvente conectado a un equipo de escritorio, Unity enviará el búfer de profundidad a Windows para habilitar la Reproyección por píxel, lo que normalmente proporcionará una calidad de imagen incluso mejor sin que la aplicación proporcione un trabajo explícito. Si proporciona un punto de enfoque, eso invalidará la Reproyección por píxel, por lo que solo debe hacerlo cuando la aplicación se ejecuta en un HoloLens.




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

La colocación del punto de enfoque depende en gran medida del holograma está examinando. La aplicación tiene el vector de mirada como referencia y el diseñador de aplicaciones sabe qué contenido quieren que el usuario Observe.

Lo más importante que un desarrollador puede hacer para estabilizar los hologramas es representar a 60 FPS. La caída por debajo de 60 FPS reducirá drásticamente la estabilidad de los hologramas, independientemente de la optimización del plano de estabilización.

**Procedimientos recomendados** No hay ninguna manera universal de configurar el plano de estabilización y es específico de la aplicación, por lo que la recomendación principal es experimentar y ver lo que funciona mejor para sus escenarios. Sin embargo, intente alinear el plano de estabilización con tanto contenido como sea posible, ya que todo el contenido de este plano está totalmente estabilizado.

Por ejemplo:
* Si solo tiene contenido plano (aplicación de lectura, aplicación de reproducción de vídeo), alinee el plano de estabilización con el plano que tiene su contenido.
* Si hay 3 esferas pequeñas que están bloqueadas de forma mundial, haga que el plano de estabilización "se corte", a pesar de los centros de todas las esferas que están actualmente en la vista del usuario.
* Si la escena tiene contenido con una profundidad sustancialmente diferente, favorecer más objetos.
* Asegúrese de ajustar el punto de estabilización de cada fotograma para que coincida con el holograma que el usuario está examinando.

**Aspectos que se deben evitar** El plano de estabilización es una herramienta excelente para lograr hologramas estables, pero si se usa de forma inestable, puede provocar una inestabilidad grave de la imagen.
* No "activar y olvidar", ya que puede acabar con el plano de estabilización detrás del usuario o adjuntarlo a un objeto que ya no está en la vista del usuario. Asegúrese de que el plano de estabilización normal está establecido en la cámara hacia delante (por ejemplo,-Camera. forward).
* No cambie rápidamente el plano de estabilización hacia atrás y hacia delante entre extremos
* No deje el plano de estabilización establecido en una distancia o orientación fijas
* No permita que el plano de estabilización se corte por el usuario
* No establezca el punto de enfoque cuando se ejecuta en un equipo de escritorio en lugar de HoloLens y, en su lugar, se basa en la Reproyección basada en la profundidad por píxel.

## <a name="color-separation"></a>Separación de colores 

Debido a la naturaleza de las pantallas de HoloLens, a veces se puede percibir un artefacto denominado "separación de color". Se manifiesta como la imagen que se separa en colores base individuales, rojo, verde y azul. El artefacto puede ser especialmente visible cuando se muestran objetos blancos, ya que tienen grandes cantidades de rojo, verde y azul. Es más pronunciada cuando un usuario realiza un seguimiento visual de un holograma que se mueve por el fotograma holográfica a alta velocidad. Otra forma en que el artefacto puede manifestarse es la deformación o la desestructuración de los objetos. Si un objeto tiene colores de contraste alto o puros (rojo, verde, azul), la separación de colores se percibirá como una deformación de partes diferentes del objeto.

**Ejemplo del aspecto que podría tener la separación de colores de un cursor redondo blanco con bloqueo de cabeza cuando un usuario gira su cabeza hacia el lado:**

![Ejemplo del aspecto que podría tener la separación de colores de un cursor de redondeo blanco con bloqueo de cabeza cuando un usuario gira su cabeza al lado.](images/colorseparationofroundwhitecursor-300px.png)

Aunque es difícil evitar completamente la separación de colores, hay varias técnicas disponibles para mitigarla.

**La separación de colores puede verse en:**
* Objetos que se mueven rápidamente, incluidos los objetos bloqueados por el encabezado, como el [cursor](cursors.md).
* Objetos que están prácticamente lejos del [plano de estabilización](hologram-stability.md#reprojection).

**Para atenuar los efectos de la separación de colores:**
* Haga que el objeto retrase la mirada del usuario. Debería aparecer como si hubiera alguna inercia y se adjunta a la mirada "on Resorts". Esto ralentiza el cursor (lo que reduce la distancia de separación) y lo coloca detrás del punto de mira probable del usuario. Siempre que se detecte rápidamente cuando el usuario deje de desplazarse por la mirada, parece bastante natural.
* Si desea mover un holograma, intente mantener su velocidad de movimiento por debajo de 5 grados/segundo si prevé que el usuario lo seguirá con sus ojos.
* Utilice *Light* en lugar de *Geometry* para el cursor. Un origen de iluminación virtual adjuntado a la mirada se percibirá como un puntero interactivo, pero no provocará la separación del color.
* Ajuste el plano de estabilización para que coincida con los hologramas en los que está Gazing el usuario.
* Haga que el objeto sea rojo, verde o azul.
* Cambie a una versión borrosa del contenido. Por ejemplo, un cursor redondo blanco podría cambiarse a una línea orientada ligeramente desenfocada en la dirección del movimiento.

Como antes, la representación en 60 FPS y el establecimiento del plano de estabilización son las técnicas más importantes para la estabilidad de los hologramas. En caso de una separación de colores apreciable, asegúrese primero de que la velocidad de fotogramas cumple las expectativas.

## <a name="see-also"></a>Consulta también
* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Color, luz y materiales](color,-light-and-materials.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Estabilización del holograma de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
