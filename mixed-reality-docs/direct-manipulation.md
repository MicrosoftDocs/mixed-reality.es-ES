---
title: Manipulación directa con las manos
description: Introducción al modelo de entrada mediante manipulación directa
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: d263c84d306a2ece3783c2e7fb0e3f599dec49eb
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694179"
---
# <a name="direct-manipulation-with-hands"></a>Manipulación directa con las manos

![Botón](images/UX/UX_Hero_Manipulation.jpg)

La manipulación directa es un modelo de entrada de datos que implica tocar hologramas directamente con las manos. La idea que impulsa este concepto es que los objetos se comporten exactamente igual que lo hacen en el mundo real. Para activar los botones no hay más que presionarlos, para elegir los objetos no hay más que agarrarlos y el contenido 2D se comporta como una pantalla táctil virtual. Por eso a los usuarios les resulta muy fácil y divertido aprender la manipulación directa. Se considera un modelo de entrada "cercano" porque se usa con preferencia para interactuar con contenido que está al alcance de los brazos.

La manipulación directa utiliza prestaciones, lo que significa que es fácil de usar. No hay que enseñar ningún gesto simbólico a los usuarios. Todas las interacciones se crean en torno a un elemento visual que se puede tocar o agarrar.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modelo de entrada</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Manipulación directa con las manos</td>
     <td>❌ No se admite</td>
     <td>✔️ Recomendado</td>
     <td>➕ Una alternativa, se recomienda <a href="point-and-commit.md">apuntar y confirmar con las manos</a>.</td>
    
</tr>
</table>


La manipulación directa es un modelo de entrada principal de HoloLens 2, que usa el nuevo sistema articulado de seguimiento de la mano. El modelo de entrada también está disponible en los cascos envolventes mediante el uso de controladores de movimiento, pero no se recomienda como medio principal de interacción fuera de la manipulación de objetos. La manipulación directa no está disponible en HoloLens (1.ª generación).

<br>

---

## <a name="collidable-fingertip"></a>Dedo de colisión

En HoloLens 2, se reconocen las manos del usuario y se interpretan como modelos óseos de las manos derecha e izquierda. Para implementar la idea de tocar los hologramas directamente con las manos, se tendrían que acoplar cinco colisionadores a los cinco dedos del modelo óseo de cada mano. Sin embargo, dada la falta de información procedente del tacto, diez dedos de colisión pueden provocar colisiones inesperadas e impredecibles con los hologramas. 

De ahí que se sugiera colocar solo un colisionador en cada dedo índice. Los dedos índices de colisión se pueden seguir usando como puntos táctiles activos para diversos gestos táctiles que implican otros dedos como, por ejemplo, presionar con un dedo, pulsar con un dedo, presionar con dos dedos y presionar con cinco dedos, como se muestra en la imagen siguiente.

:::row:::
    :::column:::
       ![dedo de colisión](images/Collidable-Fingertip.jpg)<br>
       **Dedo de colisión**<br>
    :::column-end:::
    :::column:::
       ![Presión de un dedo](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **Presión de un dedo**<br>
    :::column-end:::
    :::column:::
       ![Pulsación de un dedo](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **Pulsación de un dedo**<br>
    :::column-end:::
    :::column:::
       ![Presión de cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **Presión de cinco dedos**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>Colisionador esférico

En lugar de usar una forma genérica aleatoria, se recomienda usar un colisionador esférico. A continuación, puedes representarlo visualmente para proporcionar mejores indicaciones a objetivos cercanos. Para aumentar la precisión del toque, el diámetro de la esfera debe coincidir con el grosor del dedo índice. Será más fácil recuperar la variable de grosor del dedo con una llamada a la API de mano.

### <a name="fingertip-cursor"></a>Cursor de dedo

Además de representar una esfera de colisión en el dedo índice, hemos creado un cursor de dedo avanzado para llegar mejor a objetivos cercanos de forma interactiva. Es un cursor en forma de anillo acoplado al dedo índice. En función de la proximidad, reacciona dinámicamente a un destino en términos de orientación y tamaño como se detalla a continuación:

* Cuando un dedo índice se mueve hacia un holograma, el cursor está siempre paralelo a la superficie del holograma y su tamaño se reduce gradualmente en consecuencia.
* En cuanto el dedo toca la superficie, el tamaño del cursor se reduce hasta convertirse en un punto y emite un evento de toque.

Con la información interactiva, los usuarios pueden realizar tareas en objetivos cercanos de forma muy precisa, como desencadenar un hipervínculo o presionar un botón, como se muestra a continuación. 

:::row:::
    :::column:::
       ![Cursor de dedo lejano](images/Fingertip-cursor-far.jpg)<br>
       **Cursor de dedo lejano**<br>
    :::column-end:::
    :::column:::
       ![Cursor de dedo cercano](images/Fingertip-cursor-near.jpg)<br>
        **Cursor de dedo cercano**<br>
    :::column-end:::
    :::column:::
       ![Cursor de dedo de contacto](images/Fingertip-cursor-contact.jpg)<br>
       **Cursor de dedo de contacto**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>Rectángulo de selección con sombreador de proximidad

El propio holograma también requiere la capacidad de proporcionar información visual y sonora para compensar la falta de información táctil. Con ese fin generamos el concepto de rectángulo de selección con sombreador de proximidad. Un rectángulo de selección es un área volumétrica mínima que rodea a un objeto 3D. El rectángulo de selección tiene un mecanismo de representación interactivo denominado sombreador de proximidad. Así es como se comporta el sombreador de proximidad:

:::row:::
    :::column:::
       ![Mantener el puntero (lejos) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **Mantener el puntero (lejos)**<br>
       Cuando el dedo índice está dentro del alcance, se proyecta un foco con forma de dedo en la superficie del rectángulo de selección.
    :::column-end:::
    :::column:::
       ![Mantener el puntero (cerca) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **Mantener el puntero (cerca)**<br>
        Cuando el dedo se acerca a la superficie, el foco se reduce en consecuencia.
    :::column-end:::
    :::column:::
       ![Inicio de contacto](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **Inicio de contacto**<br>
       En cuanto el dedo toca la superficie, todo el rectángulo de selección cambia de color o genera efectos visuales que reflejan dicho estado.
    :::column-end:::
    :::column:::
       ![Fin de contacto](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **Fin de contacto**<br>
       También se puede activar un efecto de sonido que mejore la información visual del toque.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>Botón presionable

Con el dedo de colisión, los usuarios ya están listos para interactuar con el componente fundamental de la interfaz de usuario holográfica, como un botón presionable. Un botón presionable es un botón holográfico adaptado a una presión directa del dedo. Una vez más, debido a la falta de información táctil, el botón presionable cuenta con un par de mecanismos para abordar los problemas relacionados con la información táctil.

* El primer mecanismo es un rectángulo de selección con sombreador de proximidad, del que se ha proporcionado la información pertinente en la sección anterior. Permite a los usuarios mejorar la sensación de proximidad a la hora de acercarse y entrar en contacto con un botón.
* El segundo mecanismo es la depresión. La depresión crea una sensación de presión al tocar un botón con un dedo. El mecanismo garantiza que el botón se mueve estrechamente junto con el dedo por el eje de profundidad. El botón se puede desencadenar cuando se alcanza una profundidad designada (al presionar) o se sale de dicha profundidad (al soltar) después de atravesarlo.
* El efecto de sonido se debe agregar para mejorar la información cuando se desencadena el botón.

:::row:::
    :::column:::
       ![botón presionable lejano](images/pressable-button-far.jpg)<br>
       **El dedo está lejos**<br>
    :::column-end:::
    :::column:::
       ![botón presionable cercano](images/pressable-button-approach.jpg)<br>
        **El dedo se acerca**<br>
    :::column-end:::
    :::column:::
       ![empieza el contacto con el botón presionable](images/pressable-button-contact.jpg)<br>
       **Inicio de contacto**<br>
    :::column-end:::
    :::column:::
       ![presión del botón presionable](images/pressable-button-press.jpg)<br>
       **Presión**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interacción con una tableta táctil 2D

Una [tableta táctil](slate.md) 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web. El concepto de diseño para interactuar con una tableta táctil 2D mediante la manipulación directa es aprovechar el modelo mental de interactuar con una pantalla táctil física.

### <a name="to-interact-with-the-slate-contact"></a>Para interactuar con el contacto de la tableta táctil

:::row:::
    :::column:::
       ![Tocar](images/2d-slate-interaction-touch.jpg)<br>
       **Tocar**<br>
       Utiliza el dedo índice para presionar un botón o un hipervínculo.
    :::column-end:::
    :::column:::
       ![Desplazar](images/2d-slate-interaction-scroll2.jpg)<br>
        **Desplazar**<br>
        Utiliza el dedo índice para desplazar el contenido de la tableta táctil hacia arriba y abajo.
    :::column-end:::
    :::column:::
       ![Zoom](images/2d-slate-interaction-zoom2.jpg)<br>
       **Zoom**<br>
       Los dos dedos índices del usuario se utilizan para acercar y alejar el contenido de la tableta táctil, en función del movimiento relativo de los dedos.
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>Para manipular la propia tableta táctil 2D

:::row:::
    :::column:::
       ![Mover](images/manipulate-2d-slate-move.jpg)<br>
       **Mover**<br>
       Mueve las manos a las esquinas y bordes para mostrar las prestaciones de manipulación más cercanas. Agarra la barra holográfica de la parte superior de la tableta táctil 2D para mover toda la tableta táctil.
    :::column-end:::
    :::column:::
       ![Escalar](images/manipulate-2d-slate-scale.jpg)<br>
        **Escalar**<br>
        Agarra las prestaciones de manipulación y realiza un escalado uniforme mediante las prestaciones de esquina.
    :::column-end:::
    :::column:::
       ![Redistribuir](images/manipulate-2d-slate-reflow.jpg)<br>
       **Redistribuir**<br>
       Agarra las prestaciones de manipulación y realiza reflujo a través de las prestaciones de borde.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>Manipulación de objetos 3D

HoloLens 2 permite a los usuarios habilitar sus manos para dirigir y manipular objetos holográficos 3D mediante la aplicación de un rectángulo de selección a cada objeto 3D. El rectángulo de selección proporciona una mejor percepción de la profundidad gracias a su sombreador de proximidad. Con el rectángulo de selección, hay dos enfoques de diseño para la manipulación de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulación con prestaciones

La manipulación con prestaciones te permite manipular el objeto 3D a través de un rectángulo de selección por las prestaciones de manipulación que hay a su alrededor. 

:::row:::
    :::column:::
       ![Mover](images/3d-object-manipulation-move.jpg)<br>
       **Mover**<br>
       En cuanto la mano de un usuario esté cerca de un objeto 3D, se mostrarán el rectángulo de selección y la prestación más cercana. Los usuarios pueden agarrar el rectángulo de selección para mover todo el objeto.
    :::column-end:::
    :::column:::
       ![Girar](images/3d-object-manipulation-rotate.jpg)<br>
        **Girar**<br>
        Los usuarios pueden agarrar las prestaciones de borde para girar.
    :::column-end:::
    :::column:::
       ![Escalar](images/3d-object-manipulation-scale.jpg)<br>
       **Escalar**<br>
       Los usuarios pueden agarrar las prestaciones de esquina para escalar de forma uniforme.
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>Manipulación sin prestaciones

La manipulación sin prestaciones no acopla ninguna prestación al rectángulo de selección. Los usuarios solo pueden mostrar el rectángulo de selección e interactuar directamente con él. Si el rectángulo de selección se agarra con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano. Cuando el objeto se agarra con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.

La manipulación específica requiere precisión. Se recomienda usar la **manipulación con prestaciones**, ya que proporciona un alto nivel de granularidad. Para la manipulación flexible, se recomienda usar la **manipulación sin prestaciones**, ya que permite experiencias instantáneas y divertidas.

<br>

---


## <a name="instinctual-gestures"></a>Gestos instintivos

Con HoloLens (1.ª generación), enseñamos a los usuarios un par de gestos predefinidos, como eclosionar y pulsar en el aire. En el caso de HoloLens 2, no pedimos a los usuarios que memoricen gestos simbólicos. Todos los gestos que los usuarios necesitan (cuando deben interactuar con hologramas y contenido) son instintivos. Para lograr gestos instintivos ayuda a los usuarios a realizar los gestos mediante el diseño de prestaciones de la interfaz de usuario.

Por ejemplo, si se anima al usuario a arrastrar un objeto o un punto de control acercando dos dedos, el objeto o el punto de control deben ser pequeños. Si queremos que el agarre lo realice con cinco dedos, el objeto o el punto de control deberían ser relativamente grandes. Al igual que los botones, un botón pequeño limitaría a los usuarios a presionarlo con un solo dedo; un botón grande instaría a los usuarios a presionarlo con las palmas de las manos.


:::row:::
    :::column:::
       ![Mover](images/instinctual-gestures-smallobject.jpg)<br>
       **Objeto pequeño**<br>
    :::column-end:::
    :::column:::
       ![Girar](images/instinctual-gestures-mediumobject.jpg)<br>
        **Objeto mediano**<br>
    :::column-end:::
    :::column:::
       ![Escalar](images/instinctual-gestures-largeobject.jpg)<br>
       **Objeto grande**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Diseño simétrico entre las manos y 6 controladores DoF

Es posible que hayas observado que hay paralelos de interacción que podemos dibujar en AR y controladores de movimiento en VR. Las dos entradas pueden usarse para desencadenar manipulaciones directas en sus respectivos entornos. En HoloLens 2, la realización de las operaciones de agarrar y arrastrar con las manos a corta distancia funciona de forma muy parecida a como lo hace el botón de agarrar en los controladores de movimiento de WMR. Esto proporciona a los usuarios familiaridad en la interacción entre las dos plataformas, que puede resultar útil si alguna vez decides portar la aplicación de una plataforma a la otra.

<br>

---

## <a name="optimize-with-eye-tracking"></a>Optimización con el seguimiento de los ojos

La manipulación directa puede parecer mágica si funciona según lo previsto. No obstante, también puede resultar frustrante si no se puede mover la mano a ningún lugar sin desencadenar involuntariamente un holograma. El seguimiento de los ojos puede ayudar a identificar mejor la intención del usuario.

* **Cuándo**: se reduce accidentalmente, lo que desencadena una respuesta de manipulación. El seguimiento de los ojos permite saber mejor lo que hace un usuario en cada momento.
Por ejemplo, imagina que estás leyendo un texto (con instrucciones) de una holografía cuando te dispones a agarrar tu herramienta del mundo real.

Al hacerlo, mueves la mano accidentalmente por unos botones holográficos interactivos que no te habías percatado de que estaban ahí (por ejemplo, pueden estar fuera del campo de visión del usuario).

  Un resumen: si el usuario lleva un tiempo sin mirar un holograma, pero se ha detectado un evento de tocar o agarrar para él, es probable que el usuario no tuviera realmente intención de interactuar con el holograma.

* **Cuál**:  además de solucionar activaciones positivas falsas, otro ejemplo incluye una mejor identificación de qué hologramas agarrar o usar, ya que es posible que el punto de intersección preciso no esté claro desde tu perspectiva, sobre todo si hay varios hologramas colocados unos cerca de otros.

  Aunque en HoloLens 2 el seguimiento de los ojos tiene limitaciones en función de la precisión con la que puede determinar la mirada con los ojos, puede resultar muy útil para las interacciones cercanas debido a la disparidad de profundidad al interactuar con la entrada a mano. Esto significa que a veces es difícil determinar si la mano está detrás o delante de un holograma, por ejemplo, para agarrar con precisión un widget de manipulación.

* **A dónde**: usa información acerca de lo que mira un usuario con gestos que se realizan rápidamente. Agarra un holograma y tíralo hacia su destino previsto.  

    Aunque es posible que a veces esto funcione, la realización rápida de gestos con la mano puede dar lugar a destinos muy imprecisos. Sin embargo, el seguimiento de los ojos podría mejorar la precisión del gesto.

<br>

---

## <a name="manipulation-in-mrtkmixed-reality-toolkit-for-unity"></a>Manipulación en MRTK (Mixed Reality Toolkit) para Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede conseguir un comportamiento de manipulación común con el script **ManipulationHandler**. Con ManipulationHandler, puede agarrar y mover objetos directamente con las manos o con el haz de mano. También admite la manipulación con dos manos para escalar y girar un objeto.

* [MRTK: manipulación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)


---

## <a name="see-also"></a>Consulta también

* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
