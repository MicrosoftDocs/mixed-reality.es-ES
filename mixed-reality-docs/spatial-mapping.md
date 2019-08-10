---
title: Asignación espacial
description: La asignación espacial proporciona una representación detallada de las superficies del mundo real en el entorno en torno a HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: asignación espacial, HoloLens, realidad mixta, reconstrucción superficial, malla, Sr
ms.openlocfilehash: 4914cf5b7864ecb2430a39af73729eb6dfc0e2bd
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937069"
---
# <a name="spatial-mapping"></a>Asignación espacial

La asignación espacial proporciona una representación detallada de las superficies del mundo real en el entorno en torno a HoloLens, lo que permite a los desarrolladores crear una experiencia de realidad mixta. Al combinar el mundo real con el mundo virtual, una aplicación puede hacer que los hologramas parezcan reales. Las aplicaciones también pueden alinearse de forma más natural con las expectativas del usuario, ya que proporcionan comportamientos e interacciones conocidos del mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Asignación espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Información general conceptual

![Superficies de malla que cubren una habitación](images/SurfaceReconstruction.jpg)<br>
*Ejemplo de una malla de asignación espacial que cubre una habitación*

Los dos tipos de objetos principales utilizados para la asignación espacial son el "observador de superficie espacial" y la "superficie espacial".

La aplicación proporciona el observador de superficie espacial con uno o más volúmenes delimitadores para definir las regiones de espacio en las que la aplicación desea recibir datos de asignación espacial. Para cada uno de estos volúmenes, la asignación espacial proporcionará a la aplicación un conjunto de superficies espaciales.

Estos volúmenes pueden ser estacionarios (en una ubicación fija con respecto al mundo real) o se pueden adjuntar a HoloLens (se mueven, pero no giran, con HoloLens mientras se mueven por el entorno). Cada superficie espacial describe las superficies del mundo real en un pequeño volumen de espacio, representado como una malla de triángulo conectada a un [sistema de coordenadas espaciales](coordinate-systems.md)con bloqueo mundial.

A medida que HoloLens recopile nuevos datos sobre el entorno y, a medida que se produzcan cambios en el entorno, aparecerán las superficies espaciales, desaparecerán y cambiarán.

## <a name="common-usage-scenarios"></a>Escenarios de uso comunes

![Ilustraciones de escenarios comunes de uso de la asignación espacial: Selección de ubicación, oclusión, física y navegación](images/sm-concepts-1000px.png)

### <a name="placement"></a>Colocación

La asignación espacial proporciona a las aplicaciones la oportunidad de presentar formas naturales y familiares de interacción con el usuario; ¿Qué puede ser más natural que colocar el teléfono en el escritorio?

Restringir la colocación de los hologramas (o más en general, cualquier selección de ubicaciones espaciales) que se encuentran en las superficies proporciona una asignación natural desde 3D (punto en el espacio) hasta 2D (punto en superficie). Esto reduce la cantidad de información que el usuario debe proporcionar a la aplicación y, por tanto, hace que las interacciones del usuario sean más rápidas, más sencillas y precisas. Esto es especialmente cierto porque ' Distance out ' no es algo que se usa para la comunicación física con otras personas o con equipos. Cuando nos señalan con nuestro dedo, especificamos una dirección, pero no una distancia.

Una advertencia importante es que cuando una aplicación deduce la distancia desde la dirección (por ejemplo, mediante la realización de una Raycast a lo largo de la dirección de miración del usuario para encontrar la superficie espacial más cercana), esto debe producir resultados que el usuario pueda predecir de forma confiable. De lo contrario, el usuario perderá su sentido de control y esto puede resultar frustrante. Un método que ayuda con esto es realizar varias raycasts en lugar de solo una. Los resultados agregados deben ser más suaves y más predecibles, menos susceptibles de influir en los resultados de ' atípico ' transitorios (como pueden estar causados por rayos pequeños o hasta alcanzar pequeños bits de geometría que el usuario no conoce). La agregación o el suavizado también se pueden realizar a lo largo del tiempo; por ejemplo, puede limitar la velocidad máxima a la que un holograma puede variar a la distancia del usuario. Simplemente limitar el valor de la distancia mínima y máxima también puede ser útil, por lo que el holograma que se está moviendo no se desplaza repentinamente hacia la distancia o se vuelve a bloquear en la superficie del usuario.

Las aplicaciones también pueden usar la forma y la dirección de las superficies para guiar la colocación de los hologramas. Una silla holográfica no debe penetrar a través de las paredes y debe sentarse con el suelo incluso si es ligeramente desigual. Este tipo de funcionalidad probablemente dependerá del uso de colisiones físicas en lugar de simplemente raycasts, pero se aplicarán preocupaciones similares. Si el holograma que se está colocando tiene muchos polígonos pequeños que se exponen, como las piernas de una silla, puede que tenga sentido expandir la representación física de esos polígonos a algo más amplio y más suave, de modo que puedan deslizarse sobre las superficies espaciales sin snagging.

En su extremo, los datos proporcionados por el usuario se pueden simplificar completamente y las superficies espaciales pueden usarse para realizar la colocación automática del holograma. Por ejemplo, la aplicación podría colocar un interruptor de luz holográfica en algún lugar de la pared para que el usuario lo presione. Aquí se aplica la misma advertencia sobre la predicción. Si el usuario espera el control sobre la colocación de hologramas, pero la aplicación no siempre coloca los hologramas en los que esperan (si el conmutador ligero aparece en algún lugar en el que el usuario no puede tener acceso), esta será una experiencia frustrante. En realidad, puede ser peor realizar la selección de ubicación automática que requiere la corrección del usuario en parte del tiempo, además de requerir que el usuario realice siempre la ubicación. Dado que se *espera*una colocación automática correcta, la corrección manual se parece a una carga.

Tenga en cuenta también que la capacidad de una aplicación para usar superficies espaciales para la selección de ubicación depende en gran medida de la [experiencia de análisis](spatial-mapping-design.md#the-environment-scanning-experience)de la aplicación. Si no se ha analizado una superficie, no se puede usar para la selección de ubicación. Depende de la aplicación que se desactive al usuario para que pueda examinar las nuevas superficies o seleccionar una nueva ubicación.

Los comentarios visuales al usuario son de importancia primordial durante la selección de ubicación. El usuario debe saber dónde se encuentra el holograma en relación con la superficie más cercana con efectos de la [base](spatial-mapping.md#visualization). Deben comprender por qué se está restringiendo el movimiento de su holograma (por ejemplo, debido a un conflicto con otra superficie cercana). Si no pueden colocar un holograma en la ubicación actual, los comentarios visuales deben dejar claro por qué no. Por ejemplo, si el usuario intenta colocar un sofá Holographic en la pared, las partes del sofá que están detrás de la pared deben pulsater en un color enfadado. O bien, si la aplicación no puede encontrar una superficie espacial en una ubicación en la que el usuario pueda ver una superficie del mundo real, la aplicación debería dejar de estar clara. La ausencia obvia de un efecto de base en esta área puede lograr este fin.

### <a name="occlusion"></a>Oclusión

Uno de los usos principales de las superficies de asignación espacial es simplemente tapaba hologramas. Este comportamiento sencillo tiene un gran impacto en el realismo percibido de los hologramas, lo que ayuda a crear un sentido visceral que realmente inhabit el mismo espacio físico que el usuario.

La oclusión también proporciona información al usuario; Cuando un holograma parece estar ocluidosdo por una superficie del mundo real, proporciona información visual adicional sobre la ubicación espacial de ese holograma en el mundo. Por el contrario, la oclusión también puede *ocultar* de forma útil información del usuario; occluding hologramas Behind Walls puede reducir la confusión visual de una manera intuitiva. Para ocultar o mostrar un holograma, el usuario solo tiene que desplace su encabezado.

La oclusión también se puede utilizar para las expectativas principales de una interfaz de usuario natural basada en interacciones físicas conocidas. Si un holograma es ocluidos por una superficie, se debe a que esa superficie es sólida, por lo que el usuario debería esperar que el holograma se colisionará con esa superficie y no simplemente lo pase.

A veces, no se desea la oclusión de hologramas. Si un usuario tiene que ser capaz de interactuar con un holograma, debe ser capaz de verlo, incluso si está detrás de una superficie del mundo real. En tales casos, normalmente tiene sentido representar tal holograma de manera diferente cuando se ocluidos (por ejemplo, reduciendo su luminosidad). De este modo, el usuario podrá localizar visualmente el holograma, pero seguirá teniendo en cuenta que está detrás de algo.

### <a name="physics"></a>Efectos

El uso de la simulación física es otra manera en que se puede usar la asignación espacial para reforzar la *presencia* de hologramas en el espacio físico del usuario. Cuando mi bola de caucho holográfica se sitúa de forma realista en el escritorio, rebota por el piso y desaparece bajo el sofá, podría ser difícil creer que no está realmente ahí.

La simulación física también proporciona la oportunidad de que una aplicación use interacciones físicas y conocidas basadas en la física. Mover una pieza de muebles holográfica en torno a la planta es probable que sea más fácil para el usuario si el mobiliario responde como si estuviera desplazándose por el piso con la inercia y la fricción adecuadas.

Para generar comportamientos físicos realistas, es probable que tenga que realizar algún [procesamiento](spatial-mapping.md#mesh-processing) de la malla, como rellenar los huecos, quitar hallucinations flotantes y superficies aproximadas de suavizado.

También debe tener en cuenta el modo en que la [experiencia de análisis](spatial-mapping-design.md#the-environment-scanning-experience) de la aplicación influye en su simulación física. En primer lugar, las superficies que faltan no entran en conflicto. ¿Qué ocurre cuando la bola de goma apaga el corredor y sale del mundo conocido? En segundo lugar, debe decidir si seguirá respondiendo a los cambios en el entorno a lo largo del tiempo. En algunos casos, querrá responder lo más rápido posible; por ejemplo, si el usuario usa puertas y mobiliario como barricades movible en defensa frente a Tempest de flechas latinas de entrada. No obstante, en otros casos, puede que desee omitir las nuevas actualizaciones. es posible que la conducción de un coche deportivo de holográfica en torno al Racetrack de su piso no sea tan divertido si su perro decide sentarse en el medio de la pista.

### <a name="navigation"></a>Navegación

Las aplicaciones pueden usar datos de asignación espacial para conceder a los caracteres holográficas (o agentes) la capacidad de navegar por el mundo real de la misma forma que lo haría una persona real. Esto puede ayudar a reforzar la presencia de caracteres holográficas mediante su restricción en el mismo conjunto de comportamientos naturales y familiares que los del usuario y sus amigos.

Las funcionalidades de navegación también pueden resultar útiles para los usuarios. Una vez que se ha creado un mapa de navegación en un área determinada, se podría compartir para proporcionar instrucciones holográficas para nuevos usuarios desconocidos con esa ubicación. Este mapa podría diseñarse para ayudar a mantener el flujo de tráfico de peatones sin problemas, o para evitar accidentes en ubicaciones peligrosas como sitios de construcción.

Los principales desafíos técnicos que conlleva la implementación de la funcionalidad de navegación serán la detección confiable de las superficies que se pueden examinar (los usuarios no se recorren en las tablas) y la adaptación estable a los cambios en el entorno (los usuarios no se dirigen a las puertas cerradas). La malla puede requerir algún [procesamiento](spatial-mapping.md#mesh-processing) antes de que se pueda usar para la planeación de la ruta de acceso y la navegación por un carácter virtual. Suavizar la malla y quitar hallucinations puede ayudar a evitar que se bloqueen los caracteres. También puede simplificar drásticamente la malla con el fin de acelerar los cálculos de navegación y planeación de la ruta de acceso de los caracteres. Estos desafíos han recibido una gran atención en el desarrollo de la tecnología de videogame y hay una gran cantidad de documentación de investigación disponible en estos temas.

Tenga en cuenta que la funcionalidad de NavMesh integrada en Unity no se puede usar con superficies de asignación espacial. Esto se debe a que las superficies de asignación espacial no se conocen hasta que se inicia la aplicación, mientras que los archivos de datos NavMesh deben generarse a partir de los recursos de origen con anterioridad. Tenga en cuenta también que, el sistema de asignación espacial no proporcionará [información sobre las superficies lejos](spatial-mapping-design.md#the-environment-scanning-experience) de la ubicación actual del usuario. Por lo tanto, la aplicación debe "recordar" superficies si se va a crear un mapa de un área muy grande.

### <a name="visualization"></a>Visualiza

La mayor parte del tiempo es adecuado para que las superficies espaciales sean invisibles; para minimizar la confusión visual y dejar que el mundo real se hable de sí mismo. Sin embargo, a veces es útil visualizar directamente las superficies de asignación espacial, a pesar de que sus homólogos reales ya están visibles.

Por ejemplo, cuando el usuario está intentando colocar un holograma en una superficie (colocando un armario de Holographic en la pared, por ejemplo), puede ser útil para el holograma al convertir una sombra en la superficie. Esto ofrece al usuario un sentido mucho más claro de la proximidad física exacta entre el holograma y la superficie. Este también es un ejemplo de la práctica más general de la "vista previa" de visualmente un cambio antes de que el usuario se confirme.

Al visualizar las superficies, la aplicación puede compartir con el usuario su conocimiento del entorno. Por ejemplo, un juego de la placa holográfica podría visualizar las superficies horizontales que ha identificado como ' tablas ', por lo que el usuario sabe dónde deben ir para interactuar.

Visualizar las superficies puede ser una forma útil de mostrar los espacios cercanos del usuario que están ocultos en la vista. Esto podría proporcionar una manera sencilla de conceder al usuario acceso a su cocina (y a todos sus hologramas contenidos) desde su salón.

Es posible que las mallas de superficie que proporciona la asignación espacial no sean especialmente "limpias". Por lo tanto, es importante visualizarlos de forma adecuada. Los cálculos de iluminación tradicionales pueden resaltar errores en las normales de superficie en un modo de distracción visual, mientras que las texturas "limpias" proyectadas en la superficie pueden ayudarle a darle una apariencia tidier. También es posible realizar el procesamiento de la [malla](spatial-mapping.md#mesh-processing) para mejorar las propiedades de la malla, antes de que se representen las superficies.

## <a name="using-the-surface-observer"></a>Uso del observador de superficie

El punto de partida para la asignación espacial es el observador de la superficie. El flujo de programa es el siguiente:
* Creación de un objeto de observador de superficie
   * Proporcione uno o más volúmenes espaciales para definir las regiones de interés en las que la aplicación desea recibir datos de asignación espacial. Un volumen espacial es simplemente una forma que define una región de espacio, como una esfera o un cuadro.
   * Use un volumen espacial con un sistema de coordenadas espaciales de bloque mundial para identificar una región fija del mundo físico.
   * Use un volumen espacial, actualizado cada fotograma con un sistema de coordenadas espaciales bloqueado por el cuerpo, para identificar una región de espacio que se mueve (pero no gira) con el usuario.
   * Estos volúmenes espaciales se pueden cambiar más adelante en cualquier momento, a medida que cambia el estado de la aplicación o del usuario.
* Usar sondeo o notificación para recuperar información sobre las superficies espaciales
   * Puede "sondear" el observador de superficie para el estado de la superficie espacial en cualquier momento. Como alternativa, puede registrarse para el evento ' Surfaces Changed ' de los observador, que enviará una notificación a la aplicación cuando las superficies espaciales hayan cambiado.
   * En el caso de los volúmenes espaciales dinámicos, como el frustum de la vista o un volumen bloqueado por el cuerpo, las aplicaciones deberán sondear los cambios en cada fotograma estableciendo la región de interés y, a continuación, obtener el conjunto actual de superficies espaciales.
   * En el caso de un volumen estático, como un cubo de bloque mundial que abarque un solo salón, las aplicaciones pueden registrarse para el evento ' Surfaces Changed ' que se va a notificar cuando las superficies espaciales dentro de ese volumen puedan haber cambiado.
* Cambios en las superficies del proceso
   * Recorrer en iteración el conjunto de superficies espaciales proporcionado.
   * Clasificar las superficies espaciales como agregadas, cambiadas o eliminadas.
   * Para cada superficie espacial agregada o modificada, si procede, envíe una solicitud asincrónica para recibir la malla actualizada que representa el estado actual de la superficie en el nivel de detalle deseado.
* Procese la solicitud de malla asincrónica (más información en las secciones siguientes).

## <a name="mesh-caching"></a>Almacenamiento en caché de malla

Las superficies espaciales se representan mediante mallas de triángulo densa. Almacenar, representar y procesar estas mallas puede consumir importantes recursos de cálculo y almacenamiento. Como tal, cada aplicación debe adoptar un esquema de almacenamiento en caché de malla apropiado para sus necesidades, con el fin de minimizar los recursos usados para el procesamiento y el almacenamiento de malla. Este esquema debe determinar qué mallas conservar y qué descartar, así como cuándo actualizar la malla para cada superficie espacial.

Muchas de las consideraciones que se han explicado informarán directamente sobre cómo la aplicación debe abordar el almacenamiento en caché de malla. Debe considerar cómo el usuario se desplaza por el entorno, qué superficies son necesarias, Cuándo se observarán diferentes superficies y cuándo se deben capturar los cambios en el entorno.

Al interpretar el evento ' Surfaces Changed ' proporcionado por el observador de la superficie, la lógica de almacenamiento en caché de la malla básica es la siguiente:
* Si la aplicación ve un identificador de superficie espacial que no ha aparecido antes, debe tratarlo como una nueva superficie espacial.
* Si la aplicación ve una superficie espacial con un identificador conocido pero con una nueva hora de actualización, debe tratarla como una superficie espacial actualizada.
* Si la aplicación ya no ve una superficie espacial con un identificador conocido, debe tratarla como una superficie espacial quitada.

A continuación, cada aplicación debe tomar las siguientes decisiones:
* En el caso de las nuevas superficies espaciales, ¿se debe solicitar la malla?
   * Normalmente, la malla se debe solicitar inmediatamente para las nuevas superficies espaciales, lo que puede proporcionar información útil nueva al usuario.
   * Sin embargo, se debe dar prioridad a las nuevas superficies espaciales cercanas y delante del usuario y se debe solicitar primero su malla.
   * Si la nueva malla no es necesaria, si, por ejemplo, la aplicación tiene inmovilizado de forma permanente o temporal su modelo de entorno, no se debe solicitar.
* En el caso de las superficies espaciales actualizadas, ¿se debe solicitar la malla?
   * Las superficies espaciales actualizadas cercanas y delante del usuario deben tener prioridad y se debe solicitar primero su malla.
   * También puede ser adecuado asignar mayor prioridad a las superficies nuevas que a las superficies actualizadas, especialmente durante la experiencia de exploración.
   * Para limitar los costos de procesamiento, las aplicaciones pueden querer limitar la velocidad a la que procesan las actualizaciones de las superficies espaciales.
   * Puede deducir que los cambios en una superficie espacial son menores; por ejemplo, si los límites de la superficie son pequeños, en cuyo caso es posible que la actualización no sea lo suficientemente importante para procesarla.
   * Es posible que las actualizaciones de las superficies espaciales fuera de la región actual de interés del usuario se omitan por completo, aunque en este caso puede ser más eficaz modificar los volúmenes de límite espacial en uso por el observador de la superficie.
* En el caso de las superficies espaciales quitadas, ¿se debe descartar la malla?
   * Por lo general, la malla debe descartarse inmediatamente para las superficies espaciales quitadas, de modo que la oclusión de holograma siga siendo correcta.
   * Sin embargo, si la aplicación tiene motivos para creer que una superficie espacial volverá a aparecer en breve (quizás según el diseño de la experiencia del usuario), puede ser más eficaz conservarla que descartar su malla y volver a crearla más tarde.
   * Si la aplicación está compilando un modelo a gran escala del entorno del usuario, es posible que no desee descartar ninguna de las mallas. Sin embargo, todavía necesitará limitar el uso de recursos, posiblemente mediante la puesta en cola de las mallas en el disco a medida que desaparezcan las superficies espaciales.
   * Tenga en cuenta que algunos eventos relativamente poco frecuentes durante la generación de superficies espaciales pueden hacer que las superficies espaciales se reemplacen por nuevas superficies espaciales en una ubicación similar pero con diferentes identificadores. Por lo tanto, las aplicaciones que decidan no descartar una superficie quitada deben tener cuidado de no acabar con varias mallas de superficie espacial muy superpuestas que cubran la misma ubicación.
* ¿Se debe descartar la malla para cualquier otra superficie espacial?
   * Aunque existe una superficie espacial, si ya no es útil para la experiencia del usuario, se debe descartar. Por ejemplo, si la aplicación ' reemplaza ' la sala en el otro lado de una puerta con un espacio virtual alternativo, las superficies espaciales de ese salón ya no importan.

Este es un ejemplo de estrategia de almacenamiento en caché de malla, mediante histéresis espaciales y temporales:
* Considere la posibilidad de usar una aplicación que desee usar un volumen espacial en forma de frustum de interés que siga la mirada del usuario y mire.
* Una superficie espacial puede desaparecer temporalmente de este volumen, simplemente porque el usuario mira fuera de la superficie o los pasos fuera de ella... solo para volver a mirar o retroceder un momento más adelante. En este caso, descartar y volver a crear la malla para esta superficie representa una gran cantidad de procesamiento redundante.
* Para reducir el número de cambios procesados, la aplicación utiliza dos observadores de superficie espacial, uno incluido en el otro. El volumen más grande es esférico y sigue al usuario ' diferida '; solo se mueve cuando sea necesario para asegurarse de que su centro está dentro de 2,0 metros del usuario.
* Las mallas de superficie espacial nuevas y actualizadas siempre se procesan desde el observador de la superficie interna más pequeña, pero las mallas se almacenan en caché hasta que desaparecen del observador de la superficie externa más grande. Esto permite que la aplicación evite el procesamiento de muchos cambios redundantes debido al movimiento del usuario local.
* Puesto que una superficie espacial también puede desaparecer temporalmente debido a la pérdida de seguimiento, la aplicación también pospone las superficies espaciales descartadas quitadas durante la pérdida de seguimiento.
* En general, una aplicación debe evaluar el equilibrio entre el procesamiento reducido de la actualización y el mayor uso de la memoria para determinar la estrategia de almacenamiento en caché ideal.

## <a name="rendering"></a>Representación

Hay tres formas principales en las que se suelen usar las mallas de asignación espacial para la representación:
* Para visualización de superficie
   * A menudo resulta útil visualizar directamente las superficies espaciales. Por ejemplo, la conversión de ' Shadows ' de objetos en superficies espaciales puede proporcionar información visual útil al usuario mientras coloca hologramas en superficies.
   * Lo que hay que tener en cuenta es que las mallas espaciales son diferentes a la clase de mallas que puede crear un artista 3D. La topología de triángulo no será "limpia" como topología de creación humana y la malla se verá afectada por [diversos errores](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Con el fin de crear una estética visual agradable, puede que desee realizar algún procesamiento de la [malla](spatial-mapping.md#mesh-processing), por ejemplo, para rellenar los huecos o las normales de superficie suave. También puede usar un sombreador para proyectar texturas diseñadas por intérpretes en la malla en lugar de visualizar directamente la topología de la malla y las normales.
* Para occluding hologramas detrás de las superficies del mundo real
   * Las superficies espaciales se pueden representar en un paso de solo profundidad que solo afecta al [búfer de profundidad](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) y no afecta a los destinos de representación de color.
   * Esto Prime el búfer de profundidad para tapaba los hologramas representados posteriormente detrás de las superficies espaciales. La oclusión exacta de hologramas mejora el sentido de que los hologramas existen realmente en el espacio físico del usuario.
   * Para habilitar la representación solo de profundidad, actualice el estado de Blend para establecer el valor de [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) en cero para todos los destinos de representación de color.
* Para modificar la apariencia de los hologramas ocluidos por las superficies del mundo real
   * Normalmente, la geometría representada se oculta cuando se ocluidos. Esto se consigue estableciendo la función Depth en el estado de la [Galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) en "menor o igual que", lo que hace que la geometría solo esté visible cuando esté **más cerca** de la cámara que toda la geometría representada previamente.
   * Sin embargo, puede ser útil mantener determinada geometría visible incluso cuando se ocluidos y modificar su apariencia cuando ocluidos como forma de proporcionar comentarios visuales al usuario. Por ejemplo, esto permite a la aplicación mostrar al usuario la ubicación de un objeto mientras lo deja claro que está detrás de una superficie real.
   * Para lograr esto, represente la geometría una segunda vez con un sombreador diferente que cree la apariencia deseada de "ocluidos". Antes de representar la geometría por segunda vez, realice dos cambios en el [Estado de la galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). En primer lugar, establezca la función Depth en "mayor o igual que" para que la geometría solo sea visible cuando sea **más allá** de la cámara que todas las geometrías representadas previamente. En segundo lugar, establezca DepthWriteMask en cero, para que no se modifique el búfer de profundidad (el búfer de profundidad debe seguir representando la profundidad de la geometría **más cercana** a la cámara).

El [rendimiento](understanding-performance-for-mixed-reality.md) es una preocupación importante a la hora de representar mallas de asignación espacial. A continuación se muestran algunas técnicas de rendimiento específicas para la representación de mallas de asignación espacial:
* Ajustar la densidad del triángulo
   * Cuando solicite mallas de superficie espacial del observador de la superficie, solicite la menor densidad de mallas de triángulo que serán suficientes para sus necesidades.
   * Puede que tenga sentido variar la densidad de los triángulos en una superficie por superficie, en función de la distancia de la superficie del usuario, y su relevancia para la experiencia del usuario.
   * La reducción de los recuentos de triángulo reduce el uso de memoria y los costos de procesamiento de vértices en la GPU, aunque no afectará a los costos de procesamiento de píxeles.
* Realizar la selección de frustum
   * La selección de frustum omite objetos de dibujo que no se pueden ver porque están fuera del frustum de pantalla actual. Esto reduce los costos de procesamiento de la CPU y la GPU.
   * Dado que la selección se realiza por malla y las superficies espaciales pueden ser grandes, dividir cada malla de superficie espacial en fragmentos más pequeños puede dar lugar a una selección más eficaz (en el caso de que se representen menos triángulos fuera de la vista). Sin embargo, hay una desventaja. cuanto más mallas tenga, más llamadas de dibujo debe realizar, lo que puede aumentar los costos de la CPU. En un caso extremo, los cálculos de selección de frustum en sí mismos podrían incluso tener un costo de CPU medible.
* Ajustar el orden de representación
   * Las superficies espaciales tienden a ser grandes, ya que representan el entorno completo del usuario que las rodea. Por tanto, los costos de procesamiento de píxeles en la GPU pueden ser altos, especialmente en los casos en los que hay más de una capa de geometría visible (incluidas las superficies espaciales y otros hologramas). En este caso, la capa más cercana al usuario estará occludingndo cualquier capa más allá, por lo que se desperdicia cualquier tiempo de GPU dedicado a representar esas capas más lejanas.
   * Para reducir este trabajo redundante en la GPU, ayuda a representar las superficies opacas en orden ascendente (más cerca de las primeras, más alejadas en último lugar). Por ' opaco ', se refiere a las superficies para las que el DepthWriteMask se establece en uno en el estado de la [Galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Cuando se representan las superficies más cercanas, se Prime el búfer de profundidad para que el procesador de píxeles de la GPU omita de forma eficaz las superficies más lejanas.

## <a name="mesh-processing"></a>Procesamiento de mallas

Una aplicación puede querer realizar [varias operaciones](spatial-mapping.md#mesh-processing) en mallas de superficie espacial para satisfacer sus necesidades. Los datos de índice y vértices que se proporcionan con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de [vértices y de índices](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que se usan para representar mallas de triángulo en todas las API de representación modernas. Sin embargo, un hecho clave que hay que tener en cuenta es que los triángulos de la asignación espacial tienen un **orden de paso en sentido**ascendente. Cada triángulo se representa mediante tres índices de vértice en el búfer de índice de la malla y estos índices identifican los vértices del triángulo en el orden que se encuentra en el sentido de las **agujas del reloj** , cuando el triángulo se ve desde la parte **frontal** . El lado delantero (o exterior) de las mallas de superficie espacial se corresponde como cabría esperar en el lado frontal (visible) de las superficies reales.

Las aplicaciones solo deben realizar la simplificación de la malla si la densidad del triángulo más gruesa proporcionada por el observador de la superficie sigue siendo insuficiente, este trabajo es costoso en informática y ya lo realiza el tiempo de ejecución para generar los distintos niveles de detalle proporcionados.

Dado que cada observador de superficie puede proporcionar varias superficies espaciales sin conexión, es posible que algunas aplicaciones deseen recortar estas mallas de superficie espacial entre sí y, después, moverlas juntas. En general, el paso de recorte es necesario, ya que las mallas de superficie espacial cercanas suelen superponerse ligeramente.

## <a name="raycasting-and-collision"></a>Raycasting y colisión

Para que una API física (como [Havok](http://www.havok.com/)) proporcione una aplicación con la funcionalidad raycasting y Collision para las superficies espaciales, la aplicación debe proporcionar mallas de superficie espacial a la API física. Las mallas usadas para la física suelen tener las siguientes propiedades:
* Contienen solo números pequeños de triángulos. Las operaciones de física son más intensivas computacionalmente que las operaciones de representación.
* Son "estrechos". Las superficies destinadas a ser sólidas no deben tener orificios pequeños en ellas. incluso los agujeros demasiado pequeños para ser visibles pueden causar problemas.
* Se convierten en los casco convexo. Los casco convexo tienen pocos polígonos y están libres de los huecos, y son mucho más eficaces para procesarse que las mallas de triángulo sin formato.

Al realizar raycasts con las superficies espaciales, tenga en cuenta que estas superficies suelen ser complejas y las formas desordenadas tienen pocos detalles, al igual que el escritorio. Esto significa que un único Raycast suele ser insuficiente para proporcionar información suficiente sobre la forma de la superficie y la forma del espacio vacío cerca de ella. Por lo tanto, suele ser una buena idea realizar muchos raycasts dentro de un área pequeña y usar los resultados agregados para obtener un conocimiento más confiable de la superficie. Por ejemplo, si se usa el promedio de 10 raycasts para guiar la colocación de hologramas en una superficie, se producirá un resultado mucho más suave y menos ' de vibración ' que use solo un Raycast.

Sin embargo, tenga en cuenta que cada Raycast puede tener un alto costo computacional. Por lo tanto, según el escenario de uso, debe intercambiar el costo computacional de raycasts adicionales (realizado cada fotograma) con el costo computacional del procesamiento de la [malla](spatial-mapping.md#mesh-processing) para suavizar y quitar los huecos en las superficies espaciales (se realiza cuando está espacial). las mallas se actualizan).

## <a name="troubleshooting"></a>Solución de problemas
* Para que las mallas de superficie se orienten correctamente, cada GameObject debe estar activo antes de enviarse a SurfaceObeserver para que se construya su malla. De lo contrario, las mallas se mostrarán en el espacio, pero girarán en ángulos extraños.
* El GameObject que ejecuta el script que se comunica con SurfaceObserver debe establecerse en el origen. De lo contrario, todos los GameObjects que cree y envíe a SurfaceObserver para que sus mallas se construyan tendrán un desplazamiento igual al desplazamiento del objeto primario Game. Esto puede hacer que las mallas muestren varios medidores, lo que hace que sea muy difícil depurar lo que está ocurriendo.

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Conocimiento de escenas](scene-understanding.md)
* [Case study - Looking through holes in your reality](case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)
