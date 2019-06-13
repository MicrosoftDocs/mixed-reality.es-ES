---
title: Manipulación directa con las manos
description: Introducción al modelo de entrada mediante manipulación directa
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402393"
---
# <a name="direct-manipulation-with-hands"></a>Manipulación directa con las manos
La manipulación directa es un modelo de entrada de datos que implica tocar hologramas directamente con las manos. El objetivo de la manipulación directa es que los objetos se comporten exactamente igual que lo hacen en el mundo real. Para activar los botones no hay más que presionarlos, para elegir los objetos no hay más que agarrarlos y el contenido 2D se comporta como una pantalla táctil virtual.  Por eso a los usuarios les resulta muy fácil y divertido aprender la manipulación directa.  Se considera un modelo de entrada "cercano", lo que significa que se usa con preferencia para interactuar con contenido que está al alcance de los brazos.

La manipulación directa utiliza prestaciones, lo que significa que es fácil de usar. No hay que enseñar ningún gesto simbólico a los usuarios. Todas las interacciones se crean en torno a un elemento visual que se puede tocar o agarrar.

## <a name="device-support"></a>Compatibilidad con dispositivos


| Modelo de entrada | [HoloLens (1ª generación)](hololens-hardware-details.md) | HoloLens 2 |[Cascos envolventes](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Manipulación directa con las manos | ❌ No se admite | ✔️ Se recomienda | ➕ Una alternativa, se recomienda [apuntar y confirmar con las manos](point-and-commit.md).

La manipulación directa es un modelo de entrada principal de HoloLens 2 y usa el nuevo sistema articulado de seguimiento de la mano. El modelo de entrada también está disponible en los cascos envolventes mediante el uso de controladores de movimiento, pero no se recomienda como medio principal de interacción fuera de la manipulación de objetos.  La manipulación directa no está disponible en HoloLens (1ª generación).


## <a name="collidable-fingertip"></a>Dedo de colisión

En HoloLens 2, se reconocen las manos reales del usuario y se interpretan como modelos óseos de las manos derecha e izquierda. Para aplicar la idea de tocar los hologramas directamente con las manos, lo ideal sería poder acoplar un colisionador a cada dedo del modelo óseo de cada mano. Sin embargo, en la práctica, dada a la falta de información procedente del tacto, diez dedos de colisión provocaron colisiones inesperadas e impredecibles con los hologramas. 

De ahí que se sugiera colocar solo un colisionador en cada dedo índice. Los dedos índice de colisión se pueden seguir usando como puntos táctiles activos para diversos gestos táctiles que implican otros dedos, como por ejemplo, presionar con un dedo, pulsar con un dedo, presionar con dos dedos y presionar con cinco dedos, como se muestra en la imagen siguiente.

![Imagen de dedo de colisión](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Colisionador esférico

En lugar de una forma genérica aleatoria, se recomienda usar un colisionador esférico y representarlo visualmente para proporcionar indicaciones mejores para los objetivos cercanos. Para aumentar la precisión del toque, el diámetro de la esfera debe coincidir con el grosor del dedo índice. Será fácil recuperar la variable de grosor del dedo, solo es preciso llamar a la API de mano.

### <a name="fingertip-cursor"></a>Cursor de dedo

Además de representar una esfera de colisión en el dedo índice, hemos creado una solución avanzada, el cursor de dedo, para llegar mejor a objetivos cercanos de forma interactiva. Es un cursor en forma de anillo acoplado al dedo índice. En función de la proximidad, reacciona dinámicamente a un destino en términos de orientación y tamaño como se detalla a continuación:

* Cuando un dedo índice se mueve hacia un holograma, el cursor está siempre paralelo a la superficie del holograma y su tamaño se reduce gradualmente en consecuencia.
* En cuanto el dedo toca la superficie, el tamaño del cursor se reduce hasta convertirse en un punto y emite un evento de toque.

Con la información interactiva, los usuarios pueden realizar tareas en objetivos cercanos de forma muy precisa, como desencadenar un hipervínculo en contenido web o presionar un botón, como se muestra a continuación. 

![Imagen de cursor de dedo](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Rectángulo de selección con sombreador de proximidad

El propio holograma también requiere la capacidad de proporcionar información visual y sonora para compensar la falta de información táctil. Con ese fin generamos el concepto de rectángulo de selección con sombreador de proximidad. Un rectángulo de selección es un área volumétrica mínima que rodea a un objeto 3D. El rectángulo de selección tiene un mecanismo de representación interactivo denominado sombreador de proximidad. Así es como se comporta el sombreador de proximidad:

* Cuando el dedo índice está dentro del alcance, se proyecta un foco con forma de dedo en la superficie del rectángulo de selección.
* Cuando el dedo se acerca a la superficie, el foco se condensa en consecuencia.
* En cuanto el dedo toca la superficie, todo el rectángulo de selección cambia de color o se genera un efecto visual que refleje dicho estado.
* Además, se puede activar un efecto de sonido que mejore la información visual del toque.

![Imagen de rectángulo de selección con sombreador de proximidad](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Botón presionable

Con el dedo de colisión, los usuarios ya están listos para interactuar con el componente fundamental de la interfaz de usuario holográfica, el botón que se puede pulsar. Un botón presionable es un botón holográfico adaptado a la presión directa del dedo. Una vez más, debido a la falta de información táctil, el botón presionable cuenta con un par de mecanismos para abordar los problemas relacionados con la información táctil.

* El primer mecanismo es un rectángulo de selección con sombreador de proximidad, del que se ha proporcionado la información pertinente en la sección anterior. Sirve para mejorar la sensación de proximidad a los usuarios a la hora de acercarse y entrar en contacto con un botón.
* El segundo es la pulsación. Crea sensación de pulsación después de un dedo entra en contacto con el botón. El mecanismo es que el botón se mueve estrechamente junto con el dedo por el eje de profundidad. El botón se puede desencadenar cuando se alcanza una profundidad designada (al presionar) o se sale de dicha profundidad (al soltar) después de atravesarlo.
* El efecto de sonido se debe agregar para mejorar la información, cuando se desencadena el botón.

![Imagen de botón presionable](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interacción con una tableta táctil 2D

Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web. El concepto de diseño para interactuar con una tableta táctil 2D mediante la manipulación directa es aprovechar el modelo mental de interactuar con una pantalla táctil física.

Para interactuar con el contacto de la tableta táctil:

* Utiliza el dedo índice para presionar un botón o un hipervínculo.
* Utiliza el dedo índice para desplazar el contenido de la tableta táctil hacia arriba y abajo.
* Los usuarios utilizan los dos dedos índice para acercar y alejar el contenido de la tableta táctil, en función del movimiento relativo de los dedos.

![Imagen de tableta táctil 2D](images/2D-Slate-Interaction-720px.jpg)

Para manipular la propia tableta táctil 2D:

* Acerca las manos a las esquinas y bordes para mostrar las prestaciones de manipulación más cercanas.
* Agarra las prestaciones de manipulación y realiza un escalado uniforme mediante las prestaciones de la esquina y el reflujo mediante las prestaciones del borde.
* Arrastra la barra holográfica de la parte superior de la tableta táctil 2D para mover toda la tableta táctil.

![Imagen de manipulación de la tableta táctil](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipulación de objetos 3D

HoloLens 2 permite a los usuarios habilitar sus manos para la manipulación directa de objetos holográficos 3D mediante la aplicación de un rectángulo de selección a cada objeto 3D. El rectángulo de selección proporciona una mejor percepción de la profundidad gracias a su sombreador de proximidad. Con el rectángulo de selección, hay dos enfoques de diseño para la manipulación de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulación con prestaciones

Te permite manipular el objeto 3D a través de un rectángulo de selección y las prestaciones de manipulación que hay a su alrededor. En cuanto la mano de un usuario esté cerca de un objeto 3D, se mostrarán el rectángulo de selección y la prestación más cercana. Los usuarios pueden agarrar el rectángulo de selección para mover todo el objeto, las prestaciones del borde para girarlo y las prestaciones de la esquina para escalarlo de forma uniforme.

![Imagen de manipulación de objetos 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Manipulación sin prestaciones

En este mecanismo, no hay prestaciones conectadas al rectángulo de selección. Los usuarios solo pueden mostrar el rectángulo de selección e interactuar directamente con él. Si el rectángulo de selección se agarra con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano. Cuando el objeto se agarra con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.

La manipulación específica requiere precisión, por lo que es aconsejable usar la **manipulación con prestaciones**, ya que proporciona un alto nivel de granularidad. Para la manipulación flexible, se recomienda usar la **manipulación sin prestaciones**, ya que permite experiencias instantáneas y divertidas.

## <a name="instinctual-gestures"></a>Gestos instintivos

Con HoloLens (1ª generación), enseñamos a los usuarios un par gestos predefinidos, como eclosionar y pulsar en el aire. En el caso de HoloLens 2, no pedimos a los usuarios que memoricen gestos simbólicos. Todos los gestos que los usuarios necesitan para interactuar con los hologramas y el contenido son instintivos. Para lograr gestos instintivos guía a los usuarios para que realicen los gestos mediante el diseño de prestaciones de la interfaz de usuario.

Por ejemplo, si te animamos a arrastrar un objeto o un punto de control acercando dos dedos, tanto el objeto como el punto de control deben ser pequeño. Si queremos que el agarre lo realices con cinco dedos, el objeto o el punto de control debería ser relativamente grande. Al igual que los botones, un botón pequeño limitaría a los usuarios a presionarlo con un solo dedo, mientras que un botón enorme instaría a los usuarios a presionarlo con las palmas de las manos.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Diseño simétrico entre las manos y 6 controladores DoF

Es posible que hayas observado que ahora hay paralelos de interacción que podemos dibujar en AR y controladores de movimiento en VR. Las dos entradas pueden usarse para desencadenar manipulaciones directas en sus respectivos entornos. En HoloLens 2, la realización de las operaciones de agarrar y arrastrar con las manos a corta distancia funciona de forma muy parecida a como lo hace el botón de agarrar en los controladores de movimiento en WMR. Esto proporciona a los usuarios familiaridad en la interacción entre las dos plataformas y resulta muy útil si alguna vez decides portar una aplicación de una plataforma a la otra.

## <a name="optimize-with-eye-tracking"></a>Optimización con el seguimiento de los ojos

Si funciona según lo previsto, la manipulación directa puede parecer mágica, pero también puede resultar frustrante si no se puede mover la mano a ningún lugar sin desencadenar involuntariamente un holograma.
El seguimiento de los ojos puede ayudar a identificar mejor la intención del usuario.

* **Cuándo**: se reduce falsamente, lo que desencadena una respuesta de manipulación. El seguimiento de los ojos permite saber mejor lo que hace un usuario en cada momento.
Por ejemplo, imagina que estás leyendo un texto (con instrucciones) de una holografía cuando te dispones a agarrar tu herramienta del mundo real.

Al hacerlo, accidentalmente mueves la mano por unos botones holográficos interactivos que no te habías percatado de que estaban ahí (hasta es posible que estuvieran fuera del campo de visión del usuario).

  Un resumen: si el usuario lleva un tiempo sin mirar un holograma, pero se ha detectado un evento de tocar o agarrar para él, es probable que el usuario no tuviera realmente intención de interactuar con el holograma.

* **Cuál**:  además de solucionar activaciones positivas falsas, otro ejemplo incluye una mejor identificación de qué hologramas agarrar o usar, ya que es posible que el punto de intersección preciso no esté claro desde tu perspectiva, sobre todo si hay varios hologramas colocados unos cerca de otros.

  Aunque en HoloLens 2 el seguimiento de los ojos tiene cierta limitación en la precisión con la que puede determinar la mirada con los ojos, puede resultar muy útil para las interacciones próximas debido a la disparidad de profundidad al interactuar con la entrada a mano.  Esto significa que a veces es difícil determinar si la mano está detrás o delante de un holograma, por ejemplo, para agarrar con precisión un widget de manipulación.

* **A dónde**: usa información acerca de lo que mira un usuario con gestos que se realizan rápidamente. Agarra un holograma y tíralo hacia su destino previsto.  

    Aunque es posible que a veces esto funcione bien, la realización rápida de gestos con la mano puede dar lugar destinos muy imprecisos. Aquí es donde el seguimiento de los ojos puede ayudar para inclinar el vector que se lanza con la mano a la posición deseada.

## <a name="see-also"></a>Consulte también

* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)

